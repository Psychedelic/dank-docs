---
date: "1"
---

# XTC - The Cycles Token

![](imgs/xtc-trx.png)

The Cycles Token (XTC) is Dank's first product. A cycles ledger canister that provides users with a “wrapped/tokenized” version of cycles (XTC) **that can be held with just a Principal ID** (no need for a Cycles Wallet).

**XTC also has the same built-in developer features and functionality as the Cycles Wallet** (built into the XTC token itself) so that it can used to **create and manage canisters through proxy calls, or develop in DFX** funding the cycles fees from your XTC Cycles Token balance.

Each XTC token represents and is backed **1-to-1 with 1 Trillion Cycles (1 XTC = 1 Trillion Cycles)**  that they can hold, utilize, pay for computation, and trade with just like with any other token, tied to their Principal ID (and only requiring a Principal ID).

!!! Important

    Dank's XTC Cycles token is an Alpha product and is in active development. During this testing/development period, the Dank core team will have control over the canister's upgradeability and the "stop/halt" feature to facilitate bug and security updates, prevent malicious acts, and grow the Main Dank Canister in features. 
    
    When the project reaches the desired maturity level, it will transition towards a fully community-owned governance system.

## The XTC Cycles Ledger Supports the Following Actions/Methods:

- Depositing cycles (sending cycles to XTC, getting a 1-1 balance).
- Checking your balance on XTC (checking your balance in XTC).
- Transferring cycles (transfer cycles internally to other XTC users).
- Withdrawing cycles (send cycles externally, to a Canister ID).
- Accessing a basic linear history of transactions.
- Creating canisters (proxy call to create a canister using your XTC balance).
- Making proxy canister calls (make calls to canisters, topping it or not with cycles).

## The XTC Cycles Token Ledger
![](imgs/transaction.svg)



## Canister Development & Proxy Calls Through XTC 
![](imgs/canister.svg)
