---
date: "1"
---
# Dank's Cycle-based Finances

![](imgs/transaction.svg)

The core functioning of Dank is acting as a decentralized bank for the Internet Computer, allowing Principal IDs to hold cycles without needing a separate Cycles Wallet.

!!! info

    Dank is currently in development and this documentation and the initial architecture/scope of Dank might be subject to changes or modifications as that evolves. We'll update this documentation recurrently on our path to V1.

In a nutshell, with Dank we created a Cycles Ledger so that a user can hold them and interact with them using nothing but a Principal ID. Dank’s Cycles Ledger holds cycles in an auto-scalable, autonomous, multi-canister infrastructure, and maps the balances to each user’s Principal ID, using big-map to track each associated balance. This way, we abstract the need of using a Cycles Wallet (canister that holds cycles for users), and managing a separate ID to hold cycles.

Dank's Ledger and new Principal-ID centric standard enables an ecosystem in which Dank can provide users with streamlined cycles operations. Through Dank, any user can:

- Send or receive cycles across Principal IDs (Dank users).
- Send or receive cycles to any external recipient (canisters, wallets).
- Easily surface cycles inside of Internet Computer apps with just a Principal ID

These operations are called via Dank's Ledger, whether it is directly through Dank's Main Canister interface, or via a Dank-integrated IC application that leverages and integrated Dank.

## How does Dank's Ledger work?

The ledger is composed of two main pieces.

Firstly, the **main Dank Canister**. This piece is in charge of storing large amounts of cycles for all registered users, keeping track of each individual balance by registering their Principal IDs, and using big-map to keep track of the amount that corresponds to each ID. It's the main interface/API from where users can interact and perform cycle-related actions with their balances.

Secondly, **multi-canister infrastructure**, a sub-set of canisters inside the ledger keeps track of transactions; together with another scalable architecture of 'vault' canisters that grow as necessary to store more cycles in case the main canister reaches the capped cycles limit a canister can hold.

## Dank's Universal Canister ID

The Main Dank Canister **also acts as a universal Canister ID** for all users. What do we mean by this? When developing or navigating the Internet Computer, you may encounter the need to use cycles. When you do so, the balance comes from a Cycles Wallet (because Principal IDs can't hold cycles) which you specify with a Canister ID. 

For example, when deploying a canister using the DFINITY Canister SDK, you must set a default wallet from where the cycles to be consumed will be spent.

In the case of Dank, that Canister ID is **universal**, since Dank is the 'Cycles Wallet' for all Dank users (like a decentralized bank!).

This is the **main objective of the Cycles ledger**. Without the Cycles Ledger, a user's Cycles Wallet ID and Principal ID are separate addresses. Meaning their Cycles are not only separate from their main identity, but from their other assets (ICP, Neurons, etc.).

With Dank, a user's Principal ID references their cycles on Dank's ledger; and when authenticating into any app **they don't need to worry about authenticating a Cycles Wallet each time**, because the application can authorize the main Dank Canister ID every time, and Dank will in turn return that specific user's cycles balance. This also means users can **send Cycles to other Principal IDs, without needing the other user's Cycles Wallet ID!**