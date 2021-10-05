---
date: "1"
---

# Cycles Token (XTC) - Canister Development

![](imgs/xtc-trx.png)

With XTC, you can perform several canister development and management operations utilizing your Cycles Token (XTC) balance to fund the operations that require cycles.

**Remember, to interact with XTC**:
- Canister ID on mainnet:`aanaa-xaaaa-aaaah-aaeiq-cai`
- Specify cycles in full amounts: Not 1 XTC, but `1000000000000`.

---
## 🔋 Create and Manage Canisters

You can create canisters using your Cycles Token (XTC) balance. This is, however, a low level api, if you want to deploy your canister using your XTC balance see [Using dfx deploy with Cycles Token](#using-dfx-deploy-with-cycles-token-xtc).

Using `wallet_create_canister` method, you can create a canister and set the controller of
the canister to a principal ID you want. If you leave the controller to be `null`, you will be automatically selected as the controller of the newly created canister. Using the `cycles` parameter, it is possible to deposit cycles to your new canister from your XTC balance.

```bash
$ dfx canister --network=ic --no-wallet call aanaa-xaaaa-aaaah-aaeiq-cai wallet_create_canister "(record {cycles= (AMOUNT:nat64); controller= (null); })"
(
  variant {
    17_724 = record { 1_313_628_723 = principal "CREATED_CANISTER_ID" }
  },
)
```

To check the status of the created canister run the dfx canister `status` command with the returned `CREATED_CANISTER_ID`:

```bash
dfx canister --network=ic --no-wallet status CREATED_CANISTER_ID
```

---

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


## ✅ Set Cycles Token (XTC) as your default wallet in dfx:

The dfx cli tool provides helper functions during development that consumes cycles from your wallet. You can set the XTC canister to be used for these functions.

```bash
dfx identity --network=ic set-wallet aanaa-xaaaa-aaaah-aaeiq-cai --force
```

### Using dfx deploy with Cycles Token (XTC):

The `dfx deploy` command shows an error when deploying within a dfx project when the cycle wallet is set as the `XTC` canister. The `deploy` command successfully creates the canister, but fails when installing the wasm code (this is due to dfx assuming the controller of the new canister is the cycle wallet, not the dfx identity).

To deploy a projects canisters, instead of `dfx deploy --network=ic` separate the canister and install commands:

```bash
dfx canister --network=ic create --all
dfx deploy --network=ic --no-wallet
```

As an example of setting up and deploying a new project once dfx has been installed:

```bash
# Set XTC as the dfx cycle token
dfx identity --network=ic set-wallet aanaa-xaaaa-aaaah-aaeiq-cai --force

# Create a new dfx project
dfx new example

# move into the project directory
cd example

# install the node.js dependencies
npm install

# Create the empty canisters on mainnet
dfx canister --network=ic create --all

# Install the code into the empty canisters on mainnet
dfx deploy --network=ic --no-wallet
```