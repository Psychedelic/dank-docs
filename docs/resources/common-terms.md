---
date: "1"
---

# Common Terms

Mini-dictionary specific to the Dank, its products, and Internet Computer ecosystem!

-----

### IC
- Abbreviation of 'Internet Computer'.

### Account
- An account in the Internet Computer is comprised by a `Principal ID (public)`, and a `Seed Phrase or Private Key`.
- Your account is both your wallet, and your identity for IC applications.
- It holds token balances, referenced from their respective ledgers.
- When added to XTC, it is considered a XTC User.

### Cycles Token (XTC) Users
- A user's Principal ID or Account as stated above, registered as a balance in the XTC Token's canister.
- It is the same Principal ID, but integrated to XTC.
- It is registered in te Cycles Token (XTC) canister and assigned a balance.
- Because of this, the Principal ID can hold Cycles without a separate Cycles Wallet (canister).
- It is identified and referenced inside and outside of XTC with the original Principal ID.

### Cycles Token (XTC).
- A cycles token that wraps cycles so users can hold them with just a `Principal ID`
- Central piece of Dank's cycles finance open internet services.
- Registered `Principal IDs` have assigned Cycles Token (XTC) balances.
- Cycles in XTC are wrapped into Cycles Tokens (XTC). 1 XTC = 1 Trillion Cycles.
- The XTC canister handles operations and user requested transactions.
- The XTC canister is compatible with DFX and has proxy canister management calls.

### Principal ID (Public Key)
- A user's main identifier on the Internet Computer.
- Your  **wallet address**, used to surface balances and authenticate.
- It's an **address** you can send cycles or other assets to.
- It's an **identifier** you can use to sign into Internet Computer apps.
- Also could be mentioned as **public key** or **address**.
- Part of a key-pair, therefore accompanied by a **private key**.
- On the Internet Computer, they look like:
- `uncuj-asqp4-whsw6-tcfcz-es7ur-jutew-6oi3s-zti6i-bxxfp-zosth-gae`

### Private Key
- The private key of the key pair that makes your Principal ID account.
- You use it to **sign and authorize** operations in your behalf.
- Your private key is used to generate your recovery Seed Phrase.
- You must **not share it in any way with anyone**.

### Wallet
- The interface you use to surface your Principal ID account and balances.


### Seed Phrase
- A mnemonic phrase version of your account's Private Key.
- Composed by 12-words in a specific order that represent your Private Key.
- They are used to **recover or import** your Principal ID.
- Example: `table birds have paper granola furniture football country mercury genesis soup holder`

### ICP
- The main utility and governance token of the Internet Computer
- Can be locked in the Network Nervous System (NNS) to create "Neurons" (another IC token) to vote on NNS governance.
- **Can be swapped for Cycles** (another IC token), currently the only way to create them.
- Read [this post](https://medium.com/dfinity/the-internet-computers-token-economics-an-overview-29e238bd1d83#:~:text=ICP%20tokens%20allow%20users%20to,proposals%20and%20earn%20voting%20rewards.) to learn more about them.

### Cycles
- Cycles are another Internet Computer token that represents computational power.
- You burn it to use that computational power and memory to power canisters and the software in them.
- They can only be created from **ICP**.
- You can send cycles to other Cycles Token (XTC) Users, or to any canisters.
- You can deposit cycles from external sources to your balance in XTC.

### Neurons
- NNS token held by users to vote on the Network Nervous System governance.
- Voting power is equal to the amount of ICP locked.
- Provides a monthly voting reward based on participation.
- Can be dissolved to withdraw the ICP locked in it.


### Canisters
- Canisters are computational units that can hold both program and state.
- It's where all code, data, and software lives and is executed on the Internet Computer.
- They are powered by burning Cycles, which represent computational power they can use on the network.
- You can build frontends, backends, apps, services, ledgers, databases, or anything in them.
- Think **Smart Contracts** on Ethereum, but evolved to hold entire software services.
- They are **tamper-proof** and governed by the Internet Computer Protocol.
- Learn more about them [in this article](https://medium.com/dfinity/the-internet-computers-token-economics-an-overview-29e238bd1d83#:~:text=ICP%20tokens%20allow%20users%20to,proposals%20and%20earn%20voting%20rewards.).

### Charging Stations
- Charging Stations are a type of canister on the Internet Computer.
- Their purpose is to **refill canisters with cycles** to fund their functioning.
- They can be configured to do so in a **smart and programmatic way**.


### Cycles Distribution
- A configuration setting in charging stations
- Allows Users to configure cycles distribution for canisters inside their charging stations.
- Sets priority of cycles distribution based on preference or cycles consumption.

### Auto-refill Rules
- A configuration setting for charging stations.
- Allows Users to configure triggers and limits on cycles refills for their charging stations.

### Open Internet Services
- A service on the Internet Computer running autonomous code
- It is managed by open tokenized governance systems that work similarly to NNS
- They can have their own tokens, specific to each governance system or features
- Dank is a collection of open internet service with a roadmap towards fully community-owned governance