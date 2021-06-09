---
date: "1"
---
# Seamless IC App Authentication

![](imgs/seamless-auth.svg)

Dank can be used to improve the onboarding and authentication experience on Internet Computer applications greatly, and plug IC applications into a wide ecosystem of cycle-based Finances, canister, charging station, and asset management features instantly.

**Dank isn't an authentication provider per-se**, but by eliminating the need of a separate Cycles Wallet, it can enable any app that integrates it to authenticate users with just a Principal ID (just like they would normally), and provide them access to their Cycles in-app via Dank's API. Reducing the amount of steps in auth to one.

## One-step User Onboardings

**How is this enabled by Dank?** Dank replaces the need for a Cycles Wallet to hold cycles (Principal IDs can't hold them), which is a canisters users need to deploy for the sole purpose of holding cycles.

Without Dank, when interacting with IC applications that can surface cycles, users would need to manage two unique identifiers. One for their identity (Principal ID) and one for their wallet (Cycles Wallet / Canister ID). 

If you were to log into an IC app like this, **you would have to input your Wallet ID** each time before entering your Principal ID so that the app can authorize your identity to use your cycles balance. This adds several points of friction when onboarding users:

- Multiple steps in the user's onboarding
- Sending cycles across user identities (Principal IDs) is not possible
- In the case of Internet Identity, balances also end up being app-specific


With the Cycles Ledger, Dank allows users to hold cycles with just a Principal ID, removing the need for a Cycles Wallet. Any IC app that integrates Dank doesn't need to ask user's for their Wallet ID, because **the the Dank canister ID is the same across all users**. Therefore, any IC app that integrates Dank can authenticate a user with their Principal ID, and knows what Canister ID they need to authorize to surface the user's balance.

One step, one unique identifier, and the same identity/balances across all interfaces.

**Reference Implementation:**

[Plugwallet.ooo](https://plugwallet.ooo/) is a browser wallet / identity / authentication provider that uses Dank, and any platform will be able to integrate to enable a seamless one-step authentication flow in IC browser experiences. By integrating Plug, you can easily authenticate Principal IDs and surface their balances in-app (and trigger transactions) in one seamless step.

## What are the main benefits of authenticating Dank users?

The key perk of authenticating Dank users, or using a Dank Authentication provider [such as the Plug browser Wallet](https://plugwallet.ooo), is that **it enables a one-step seamless onboarding experience for users**, because **Dank users can hold cycles** with just a Principal ID. 

But there are other cool perks! Those users can then **send cycles to each others with just their account's Principal ID and no need to know a separate Wallet ID!**

Other than access to cycles, using Dank has other benefits, like:


- Dank gives users a registry of the canisters they owns/control, and can be surfaced into any app to interact with them easily.
- Developers can integrate cycle actions, asset transactions, or canister/charging station management features for users, using Dank's API to interact with these Open Internet Services.
