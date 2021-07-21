---
date: "1"
---

# Cycles Token (XTC) - Getting Started

![](imgs/xtc-trx.png)

Time to start using the Cycles Token (XTC)! Here you will find all currently available methods to interact with the XTC Token Canister, and perform:

- Ledger Operations (Deposit, Send, Withdraw, Check balances...)
- Proxy Canister Calls (Create Canister, Make Proxy Call to Canisters)

You can **get your first Cycles Token (XTC) balance** by either depositing cycles to the XTC Token Canister to mint them (see below), or getting a one-time redeem of 100$ worth of cycles from DFINITY's [Cycles Faucet tool](https://faucet.dfinity.org/) (select the "Dank" option to get Cycles Tokens - XTC)

## Interacting with Cycles Token (XTC) - On Mainnet (DFX)

Cycles Token (XTC) offers its services on the mainnet of the Internet Computer (IC). The XTC Token Canister ID on mainnet is `aanaa-xaaaa-aaaah-aaeiq-cai`. **You have to use this address for your calls**.

## Ledger Operations
These are all the operations related to interacting, using, and trading with your Cycles Token balance in the XTC Token Canister.

### Check your balance on Cycles Token (XTC):

```bash
$ dfx canister --network=ic call aanaa-xaaaa-aaaah-aaeiq-cai balance "(null)"
(0)
$ dfx canister --network=ic --no-wallet call xtc balance "(null)"
(0)
```

The reason that we passed `null` as a parameter to the balance method is that we want to check our own balance. If we wanted to check
another account's balance, **we would've added a principal ID there**. In that scenario, the command would have changes to this
(the principal ID used in the command is not real, just an example):

```bash
$ principalID="q6d6b-7t7pe-wdoiw-wjwn7-smnub-aaflq-cjd6i-luoec-gqtg3-62hiy-7qe"
$ dfx canister --network=ic call aanaa-xaaaa-aaaah-aaeiq-cai balance "(principal \"$principalID\")"
(0)
```

### Depositing cycles to mint a Cycles Token (XTC) balance
To get Cycles Token (XTC), you deposit cycles into the XTC Token Canister, which are locked to "mint" your 1-1 Cycles Token (XTC) balance, tied to a Principal ID. Remember that 1 XTC = 1 Trillion Cycles. (You should change the amount)

```bash
$ dfx canister --network=ic call aanaa-xaaaa-aaaah-aaeiq-cai mint "(null)" --with-cycles AMOUNT
(variant { Ok = 3 })
```

NOTE: You can deposit cycles to another XTC balance from your identity with the same `mint` method that we used to deposit cycles to our own XTC balance. For that situation, you should change `"(null)"` to a principal ID:

```bash
$ dfx canister --network=ic call aanaa-xaaaa-aaaah-aaeiq-cai mint "(principal \"Some-Principal-ID\")" --with-cycles AMOUNT
(variant { Ok = 4 })
```


### Withdrawing Cycles to Canister
Unwraps Cycles Token (XTC) into raw Cycles to send them to a to Canister ID. (You should change the amount)

```bash
$ dfx canister --network=ic call aanaa-xaaaa-aaaah-aaeiq-cai burn "(record { canister_id= principal \"some-canister's-principal-id\"; amount= 2000})"
(variant { Ok = 1 })
```

### Transferring cycles to another XTC balance/Principal ID
Send Cycles Token (XTC) to a Principal ID, balances change internally on the XTC ledger. (You should change the amount)

```bash
$ dfx canister --network=ic call aanaa-xaaaa-aaaah-aaeiq-cai transfer "(record { to= principal \"some-account's-principal-id\"; amount= 1000 })"
(variant { Ok = 2 })
```


## Create and Manage Canisters

These are all the operations related to using Cycles Token (XTC) to create canisters, refill canisters, and make proxy canister calls to any canister's methods, using your Cycles Token (XTC) balance to fund the operations.

### Creating canisters using Cycles Token (XTC):

You can create canisters using your Cycles Token (XTC) balance. Using `wallet_create_canister` method, you can create a canister and set the controller of the canister to a principal ID you want. 

If you leave the controller to be `null`, you will be automatically selected as the controller of the newly created canister. Using the `cycles` parameter, it is possible to deposit cycles to your new canister from your XTC balance.

```bash
dfx canister --network=ic call aanaa-xaaaa-aaaah-aaeiq-cai wallet_create_canister "(record (cycles: (AMOUNT:nat64); controller: (\"null\"); ))"

```

### Proxy canister calls with XTC:

XTC allows you to proxy all of your `dfx` calls through it so your Cycles Token (XTC) balance is used to fund the operations (the XTC canister unwraps them to raw cycles). To use this feature, you should use the `wallet_call` method. This method accepts four arguments:

  - canister: principal -> Your target canister
  - method_name: text -> The method you want to call from that canister
  - args: blob -> The arguments you should pass to for the call
  - cycles: nat64 -> The amount of cycles you want to pass

Let's proxy a call to the Piggy Bank canister's `whoami` method (an example canister we deployed to show an example of a proxy call!). We expect this method to return our XTC balance's ID:

```bash
dfx canister --network=ic call aanaa-xaaaa-aaaah-aaeiq-cai wallet_call "(record { canister= principal \"dmj37-5iaaa-aaaad-qakya-cai\"; method_name= \"whoami\"; args= blob \"DIDL\01nh\01\00\00\"; cycles= (0:nat64); })"
```
