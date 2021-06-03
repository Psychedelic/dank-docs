---
date: "1"
---
# Dank's Cycle & ICP Finances

![](imgs/transaction.svg)

The core functioning of Dank is acting as a decentralized  bank for the Internet Computer, allowing Principal IDs to hold cycles, ICP, or any token without needing a separate Cycles Wallet, or an Account ID in the case of ICP.

In a nutshell, with Dank we created two ledgers, for cycles and ICP, so that a user can hold them and interact with them using nothing but a Principal ID. Dank’s Cycles Ledger holds cycles in an auto-scalable, autonomous, multi-canister infrastructure, and maps the balances to each user’s Principal ID, using big-map to track each associated balance. This way, we abstract the need of using a Cycles Wallet (canister that holds cycles for users), and managing a separate ID to hold cycles.

In the case of ICP, a ledger already exists on the Internet Computer (NNS-based). However, its standard implies that to hold ICP (or any token based on this type of ledger) you need to manage an ID separate to your Principal ID, an Account ID. This ID is ledger specific, meaning you would manage a "wallet address" for each different token you hold. This doesn't translate to a great experience, especially on DeFi where you might manage dozens of tokens at a time. 

Therefore, to solve this and allow users to hold ICP or any other token with just their Principal ID, we **agreed with the community on a new standard, using Principal IDs as unique identifiers on the network**; and thus created the Dank ICP ledger using that standard, that anyone can use with just a Principal ID to hold a balance.

Dank's Ledgers and new token standard creates a finances ecosystem within the protocol in which Dank can provide users with streamlined cycles and ICP operations. Through Dank, any user can:

- Send or receive cycles or ICP to across Principal IDs (Dank users).
- Send or receive cycles to any external recipient (canisters or Account IDs).
- Use cycles/ICP inside of Internet Computer applications.
- Swap ICP for cycles (minting).

These operations are called via the Ledger's API, whether it is directly through that interface, or via a Dank-integrated IC application that leverages said interface to offer the features via a one-click UI/app.

Dank is an autonomous Open Internet Service without external control, meaning all of these operations are handled trustlessly by the protocol, and in sole reaction to the user's requests and actions.

## How do Dank's Ledgers work?

The ledgers are composed by two main pieces.

Firstly, the **main Dank Canister**. This piece is in charge of storing large amounts of cycles for all registered users, keeping track of each individual balance by registering their Principal IDs, and using big-map to keep track of the amount that corresponds to each ID. It's the main interface/API from where users can interact and perform cycle or ICP related actions with their balances.

Secondly, **multi-canister infrastructure**, a sub-set of canisters inside the ledger keeps track of transactions.

## Dank's Universal Canister ID

The Main Dank Canister **also acts as a universal Canister ID** for all users. What do we mean by this? When developing or navigating the Internet Computer, you may encounter the need to use cycles. When you do so, the balance comes from a Cycles Wallet (because Principal IDs can't hold cycles) which you specify with a Canister ID. 

For example, when deploying a canister using the Canister SDK, you must set a default wallet from where the cycles to be consumed will be spent.

In the case of Dank Accounts, that Canister ID is **universal**, since Dank is the 'Cycles Wallet' of all Dank accounts (like a decentralized bank!).

This is the **main objective of the Cycles ledger**. Without the Cycles Ledger, a user's Cycles Wallet ID and Principal ID are separate addresses. Meaning their Cycles are not only separate from their main identity, but from their other assets (ICP, Neurons, etc.).

With Dank, a user's Principal ID references their cycles on Dank's ledger; and when authenticating into any app **they don't need to worry about authenticating a Cycles Wallet ID each time**, because the application can authorize the main Dank Canister ID every time, and Dank will in turn return that specific user's cycles balance. This also means users can **send Cycles to other Principal IDs, without needing the other user's Cycles Wallet ID!**, simplifying the experience greatly.