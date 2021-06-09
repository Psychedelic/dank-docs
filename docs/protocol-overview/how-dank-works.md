---
date: "1"
---
# How Dank Works

![](imgs/architecture.svg)

Dank is an Open Internet Service and protocol for `cycle-based finances and development` on the Internet Computer. It lives in a tamperproof multi-canister architecture, composed by a main canister, and a sub-set of canisters storing metadata, and transactions records.

In total, the Dank Open Internet Service is composed by these services:

- **The Main Dank Canister**: Dank's primary point of entry for users, and main API interface that orchestrates all other sub-services.
- **The Cycles Ledger API**: First services, in charge of interacting with Dank's Cycles Ledger, giving users a way to perform transactions with their account's balance. Allows users to hold cycles with just a Principal ID.
- **The Charging Station API**: Second service, in charge of interacting with Dank's Charging Station framework, a service that abstracts and handles charging station creation for users, allowing them to easily deploy and connect them with their account's cycles/canisters.
- **The Canister Management API**: The final service, that similarly to the previous one, abstracts and handles canister deployment/management for users. It uses **proxied calls** to the Internet Computer to allow users to deploy canisters easily, link them to charging stations, update their WASM files, or send them cycles from their Principal ID. It also provides a **canister registry** that keeps a record of the canisters a user owns/manages, to be surfaced in any app or interface.

The main purpose of Dank is being a decentralized cycles bank that enables users  to hold and use Cycles with just a Principal ID (they natively can't do so). It does this with the **Cycles ledger**, in which users hold a balance references to their ID. You can think of it as a token ledger for cycles!

## Converting Principal IDs into the Core of the Internet Computer

By enabling Principal IDs to hold cycles, **Dank eliminates the need of managing separate unique identifiers for different assets and apps**, merging wallet and identity into a single unique identifier.

Principal IDs are to the Internet Computer what ETH addresses are to Ethereum. They are the user's identity (the only ID an IC app knows from a user), and the only ID that can **own/control canisters** on the network, which makes them the unique identifier centerpiece of the Internet Computer. 

We believe Principal IDs have to take that role as the Universal Unique Identifier of the Internet Computer to allow interconnected, composable, user-owned and controlled experiences to thrive easily without sacrificing the user-experience gains of Web3.

That is why with Dank we are taking a path where, instead of using app-specific Principal IDs for identity, or token-specific identifiers, we create an ecosystem that allows users to use their Principal ID as their unique universal identifier (identity/wallet/auth) across the entire Internet Computer network.

This approach works best to enable interface-agnostic and interconnected experiences, like we see on **Dapps & DeFi**; where a user can easily jump from app to app, bringing their assets with them. No friction or boundaries.

For the same reason, aside from its Cycles ledger, Dank offers a Canister Registry service. So that users can **keep a record of the canister their Principal ID owns/controls** and automatically surface them in any interface that integrates Dank to easily manage them in whichever interface they see fit without having to start over.

## An Abstraction Layer for Cycle Related Use Cases

By unifying cycles under `Principal IDs` in the Dank ecosystem, Dank can also provide a **unification and abstraction layer for many cycle related use cases as well. Including, mainly, canister and charging station development**.

All operations involving cycles, for example, from canister and charging station development and deployment, to cycles refill management, and asset transactions across accounts and wallets, are automated, abstracted, and accessible as `simple API calls to the Dank Main Interface`.

**Therefore Dank creates a seamless connections between users, their cycles, and the use cases they can give to them**.

This is achieved by having the Main Dank Canister orchestrate different services, in charge of abstracting specific use cases (Charging Station development, Canister Management, Cycle-related actions), which are then surfaced via Dank's Main API (main canister interface) as simple to use calls.

Through Dank, anyone can deploy a new canister (automatically paying the cycles fee from their balance); deploy and configure a charging station without actually developing it (Dank provides a configurable template), and easily connect said canister with the charging station to **automatically refill it with cycles to power the software in it continuously**.

## A Unified Development Environment

**From a developer perspective, Dank provides an unified development environment, and an abstraction layer for integrating or interacting with all of these functionalities.**

By leveraging Dank's developer interfaces/APIs, a developer can integrate Dank's cycles, canister, and charging station features **into their applications** so that their users can access them in an abstracted, and UI-oriented way.

Developers can also leverage the Dank ecosystem **for their own development** process; as Dank better helps orchestrate all moving pieces and  interactions required to build on the Internet Computer (canisters, cycles, charging stations) through a unified, and simplified API interface.
