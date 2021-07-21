---
date: "1"
---

# Cycles Token (XTC)

![](imgs/xtc-trx.png)

The Cycles Token (XTC) is Dank's first product. A cycles canister that provides users with a “wrapped/tokenized” version of cycles (XTC) **that can be held with just a Principal ID** (no need for a Cycles Wallet).

**The Cycles Token (XTC) also has the same built-in developer features and functionality as the Cycles Wallet** (built into the XTC token itself) so that it can used to **create and manage canisters through proxy calls, or develop in DFX** funding the cycles fees from your Cycles Token balance.

Each XTC token is backed **1-to-1 with 1 Trillion Cycles (1 XTC = 1 Trillion Cycles)**  that users can hold, utilize, pay for computation, and trade with just like with any other token, tied to their Principal ID (and only requiring a Principal ID).

- Cycles Token (XTC) Canister ID: ```aanaa-xaaaa-aaaah-aaeiq-cai```
- [View Canister on IC Rocks](https://ic.rocks/principal/aanaa-xaaaa-aaaah-aaeiq-cai)
- [Review the Code on our GitHub](https://github.com/Psychedelic/dank/tree/main/xtc)
- [Visit our Website for more Details](https://dank.ooo/xtc/)
- [Visit our Website for more Details](https://dank.ooo/xtc/)


!!! Important

    Dank's Cycles Token (XTC) is an Alpha product and is in active development. During this testing/development period, the Dank core team will have control over the canister's upgradeability and the "stop/halt" feature to facilitate bug and security updates, prevent malicious acts, and grow the Main Dank Canister in features. 
    
    When the project reaches a level of maturity, it will transition towards a fully community-owned governance system.

## Available Features & Methods  :

As of V0's Alpha release, these are the features that are built-into the Cycles Token (XTC) canister, and available as methods to be called.

- **Depositing cycles** (sending cycles to XTC, getting a 1-1 balance).
- **Checking your balance** (asking the XTC canister for your cycles balance).
- **Transferring cycles** (transfer cycles internally to Principal IDs).
- **Withdrawing cycles** (send cycles externally, to a Canister ID).
- **Transaction history** (basic linear history of transactions).
- **Creating canisters** (proxy call to create a canister using your XTC balance).
- **Proxied canister calls** (create canisters, make calls to canisters, topping calls -or not- with cycles in XTC).

## The Cycles Token (XTC) Canister
![](imgs/transaction.svg)

The Cycles Token (XTC) was built following a Principal-ID centric token standard [(Repository)](https://github.com/Psychedelic/standards). Users deposit and lock cycles and get a 1-1 balance of Cycles Token (1 XTC = 1 Trillion Cycles). It is an **alternative to using Cycles Wallet in terms of using and accessing cycles on the Internet Computer**.

You can learn the main differences between using the Cycles Token (XTC) and a Cycles Wallet [in this article](https://medium.com/@dank_ois/b9a1d3ddcebe?source=friends_link&sk=0d4c790eda6883d1c013b10cdb8f89f4).

Just like the Cycles Wallets, the Cycles Token is a **cycles provider for development on the IC**. It was built using the same interface as Cycles Wallet and has built-in proxy-call methods to create and manage canisters.

One important difference is that with XTC, instead of having a per-user Cycles Wallet ID, all XTC users share the same **“Universal ID” (the XTC Canister ID)** that they can set as their Wallet IDs. 

Which also means users -and developers- that want to use apps that surface cycles don't need to worry about authenticating multiple unique identifiers, and focus on just Principal IDs (since any app that integrates XTC would know what Wallet ID they need to authorize for the user!):

That abstraction is what enables a lot of amazing experience benefits:

- Better DeFi/Dapp compatibility (easier to integrate, access, and send cycles.)
- Smoother access to cycles for user-experiences (no need to authenticate separate Cycles Wallets)
- Composability across apps that surface cycles (one ID to surface the same balance)
- Friendlier format for GUIs (1 XTC = 1,000,000,000,000 cycles = 1$ approx)
- But standard format on APIs/CLI for development (1,000,000,000,000 XC)

Meaning XTC **has the same development perks and features of Cycles Wallet, but with a better compatibility for DeFi/Dapp experiences**.


## Canister Development & Proxy Calls
![](imgs/canister.svg)

The Cycles Token (XTC) is **DFX compatible and its canister has built-in functions that allow users to call the XTC Canister to create, fund, or make proxy calls** to canisters on the Internet Computer using their cycles balance in XTC.

Make the canister calls directly for XTC to execute, or use your XTC wallet in DFX just like a Cycles Wallet. The difference between using XTC and the Cycles Wallet here is, when you set your default-wallet on the DFX CLI, you just put XTC’s Canister ID (shared among XTC users) instead of a unique personal Cycles Wallet ID.

The XTC Canister will take your Cycles Token balance, and withdraw (or unwrap) the cycles that back it to fund any necessary operations.

This way, XTC can not only allow developers to user their Cycles Token to fund their development (just like with Cycles Wallets); but also offer those features as "plug-n-play" features that any interface can leverage.