---
date: "1"
---
# What are Dank Users?

![](imgs/architecture.svg)

Dank Users are Principal IDs that access to Dank's Open Internet Service. A user can ask Dank for a new Principal ID, or add their own.

Dank gives Principal IDs the capability of becoming a versatile and powerful 'main account' for users on the Internet Computer. How? By having Dank combine the features in finances, development, and identity into one seamless, abstracted environment.

In contrast to a regular Principal ID, Dank users **don't require** a separate Cycles Wallet to hold cycles. Instead, these users can hold cycles in a non-custodial and trustless way using the Cycles Ledger and their Principal ID to reference their balance on the ledger. No need to deploy a separate canister that acts as a Cycles Wallet.

Normally, when not using Dank and using a Cycles Wallet to hold cycles, each user would have to manage a Canister ID separate to their Principal ID that would represent their wallet and cycles balance. If you were to log into an IC application and pay cycles to do something, like you would in a Dapp with gas, you would need to first input a Canister ID (almost like entering a password on a web2 app) so that the app can know which canister they need to authorize your Principal ID to access each time you sign in.

With Dank, we removed this step. All Dank users share the same universal Canister ID, which is Dank's Main Canister ID. In a sense, it is similar to how a token contract/ledger works. This way, **apps or services that integrate Dank don't need to ask or authorize a separate wallet for the user each time** because that ID is shared across all Dank users; and users **only need to worry about managing one unique identifier, their Principal ID**.

By allowing Principal IDs to hold cycles, Dank also unlocks the possibility of Principal IDs that can:

- Sign-in/onboard into IC apps with their cycles or balances in one step, and the one
- Automate cycles operations across different IC assets (canisters, charging stations).
- Perform cycle-related actions (like deploying a canister) from abstracted interfaces.
- Surface and manage their canisters anywhere, as each account keeps a record of the canisters they own.

In a similar fashion, Dank can surface all these features for developers to offer to users; providing a ready-to-go ecosystem of tools FOR financial services, or cycle-related use cases like canister development, that anyone can surface in-app via simple API calls.

## What do Dank Users have access to?

Principal IDs in Dank get access to the entire suite of services. They are automatically registered in Dank's **Cycles Ledger**, so that they can own a balance on the ledger which the Dank protocol allows them to hold, and operate with them directly with only their Principal IDs.

Overall, the main benefit of becoming a Dank user is unifying the management of the core aspects of your IC experience (cycles, tokens, assets, canisters, etc.) from a single space that is built to have them interact with each other seamlessly.

For example, a Dank user can easily hold cycles, use them to deploy a canister, create and configure and auto-refill charging station, and fuel their canisters, all from the same Dank API, or any integrated application's UI. Or in another example, if an application like Open Chat or DSCVR were to integrate Dank, users could use the same Principal ID as their identity across both apps, bringing their token balances into both apps without having to manage app-specific balances or identities.

## Are a user's cycles in Dank exclusive to the Dank ecosystem?

No. Dank extends a Principal IDs functionality and connects it to abstracted tools, but the core of the account continues to be a regular Principal ID.

That Principal ID resides on the Internet Computer, and is owned by the user.

Dank users are just a Principal ID, and can be utilized on developer tools like DFINITY's Canister SDK DFX CLI tool, with the difference that a user will set Dank's Universal Canister ID address as their default wallet for that principal on the CLI.