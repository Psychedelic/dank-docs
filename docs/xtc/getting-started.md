---
date: "1"
---

# Cycles Token (XTC) - Getting Started

![](imgs/xtc-trx.png)

Time to start using the Cycles Token (XTC)! Here you will find all currently available methods to interact with the XTC Token Canister, and perform:

- Ledger Operations (Deposit, Send, Withdraw, Check balances...)
- Proxy Canister Calls (Create Canister, Make Proxy Call to Canisters)

## 🧰 Interacting with Cycles Token (XTC) - On Mainnet (DFX)

Cycles Token (XTC) offers its services on the mainnet of the Internet Computer (IC). The XTC Token Canister ID on mainnet is `aanaa-xaaaa-aaaah-aaeiq-cai`. **You have to use this address for your calls**.

### 🚨 Important: Formatting for XTC Values/Amounts in Calls

1 XTC represents one trillion cycles (1,000,000,000,000). In frontends, and integrated UIs, we use the friendlier format with decimals (no zeroes, 1 XTC = 1 trillion cycles -- 0.5 XTC == 0.5 TC).

But, for our **APIs and interfaces**, we utilize the **standard full numerical value of raw cycles** that XTC represents (1XTC = 1000000000000) to maintain accuracy and consistency with the development cycles/DFX experience. This is the example amount format you will see on the methods/calls below. So, to transfer 1 XTC, in the call you would specify 1000000000000, not 1.

---

## 📓 Ledger Operations
These are all the operations related to interacting, using, and trading with your Cycles Token balance in the XTC Token Canister.

## ✒️ Update Calls
The update calls described in this section charge a fee amount of tokens to prevent DDoS attack, this is necessary because of the reverse gas model of the IC. 

All update functions are allowed to trap, instead of returning an error in order to take advantage of the canisters automatic, atomic state rollback.

The cost of the fee is not for financial benefit, but to cover the cost of computation on the IC.

---

### Deposit cycles to mint an XTC balance - Mint

You can get your first Cycles Token (XTC) balance by either depositing cycles to the XTC Token Canister to mint them (see below), or getting a one-time redeem of 100$ worth of cycles from DFINITY's [Cycles Faucet tool](https://faucet.dfinity.org/), selecting the option to redeem them as Dank's Cycles Token (XTC)! 

(**If you used the faucet already**, and chose the Cycles Wallet option but want to migrate to Cycles Tokens (XTC) [see this example](#sending-your-faucet-cycles-wallet-balance-to-cycles-token-xtc).)

#### Depositing from a personal Cycles Wallet

You can deposit cycles into the XTC canister from a personal cycles wallet directly. The cycles are locked in the XTC canister to "mint" your 1-1 Cycles Token (XTC), tied to your Principal ID. 

To send cycles from a personal cycle wallet it must be deployed to a public subnet on mainnet, it must have cycles and be set as the wallet against dfx. In the following `mint` command the AMOUNT to deposit is in cycles (You should change the amount). 

```bash
$ dfx canister --network=ic --wallet=$(dfx identity --network=ic get-wallet) call --with-cycles AMOUNT aanaa-xaaaa-aaaah-aaeiq-cai mint "(principal \"$(dfx identity get-principal)\",0:nat)"
```

NOTE: You can deposit cycles to another XTC balance from your identity with the same `mint` method that we used to deposit cycles to our own XTC balance. For that situation, you should change the argument to a principal ID:

```bash
$ dfx canister --network=ic --wallet=$(dfx identity --network=ic get-wallet) call --with-cycles AMOUNT aanaa-xaaaa-aaaah-aaeiq-cai mint "(principal \"Some-Principal-ID\",0:nat")"
```

Note: This command should not require the `--wallet` flag, but we need the `--wallet` to make `--with-cycles` work. This is a known DFX bug.

#### Sending your Faucet Cycles Wallet Balance to Cycles Token (XTC)

Did you use DFINITY's Cycles Faucet tool, but selected the Cycles Wallet to receive your redeem? Want to move that balance to Cycles Token (XTC?). **If you have ```bc``` installed** you can do this quick command.

(Make sure you set your cycles wallet as your default dfx wallet first)

```bash
dfx canister --network=ic --wallet=$(dfx identity --network=ic get-wallet) call --with-cycles $(echo "$(dfx wallet --network=ic balance | cut -d' ' -f1)-10000000000" | bc) aanaa-xaaaa-aaaah-aaeiq-cai mint "(principal \"$(dfx identity get-principal)\")"
```

---
### Deposit ICP to mint an XTC balance - mint_by_icp

You are able to get a Cycles Token (XTC) balance by sending ICP to the XTC canister. 

Using the mint_by_icp method is done in two steps. First, we need to make a transfer call at the ICP ledger to the XTC account ID. Using the following command you’ll be returned the block height when your transaction was approved.

```bash
dfx ledger --network ic transfer --amount "$AMOUNT" "758bdb7e54b73605d1d743da9f3aad70637d4cddcba03db13137eaf35f12d375" --memo 0
```

Now that we have the blockheight of our ICP transfer, we can call the mint_by_icp method on the XTC canister. In addition, the mint_by_icp method takes ‘subaccount’, a parameter that allows you to specify if you’ve made the previous ICP transfer from a subaccount. Index 0 (or null) is your main account, while all non-zero indices refer to subaccounts.

```bash
dfx canister --network ic call aanaa-xaaaa-aaaah-aaeiq-cai mint_by_icp "(null,$BLOCK_HEIGHT:nat64)"
```
---


### Withdrawing cycles to a Canister - Burn

Unwraps Cycles Token (XTC) into raw Cycles to send them to a Canister ID. (You should change the amount)

```bash
$ dfx canister --network=ic --no-wallet call aanaa-xaaaa-aaaah-aaeiq-cai burn "(record { canister_id= principal \"some-canister's-principal-id\"; amount= (2000:nat64)})"
(variant { Ok = 1 })
```

---

### Transfer XTC to another XTC Balance - transferErc20
Send Cycles Token (XTC) to a Principal ID, balances change internally on the XTC ledger. (You should change the amount).

Transfers `value` amount of tokens to user `to`, returns a `TxReceipt` which contains the transaction index or an error message.


```bash
dfx canister --network=ic --no-wallet call aanaa-xaaaa-aaaah-aaeiq-cai transferErc20 "(principal \"some-account's-principal-id\", 1000:nat)"
```

---

###  Transfer XTC on Another User's Behalf - transferFrom

Transfers `value` amount of tokens from user `from` to user `to`, this method allows canister smart contracts to transfer tokens on your behalf, it returns a `TxReceipt` which contains the transaction index or an error message.

```bash
dfx canister --network=ic --no-wallet call aanaa-xaaaa-aaaah-aaeiq-cai transferFrom "(principal \"from-account-principal\",principal \"to-account-principal\", 1000:nat)"
```

---

###  Set an Allowance to Another Identity - approve

You can set an allowance using this method, giving a third-party access to a specific number of tokens they can withdraw from your balance if they want.

An allowance permits the `spender` to withdraw tokens from your account, up to the `value` amount. If it is called again it overwrites the current allowance with `value`. There is no upper limit for value.

```bash
dfx canister --network=ic --no-wallet call aanaa-xaaaa-aaaah-aaeiq-cai approve "(principal \"third-party-account-principal\", 1000:nat)"
```

---

###  Check Details of a Transaction - getTransaction

Returns transaction detail of the transaction identified by ´index´. If the ´index´ is out of range, the execution traps. Transactions are indexed from zero.

```bash
dfx canister --network=ic --no-wallet call aanaa-xaaaa-aaaah-aaeiq-cai getTransaction "($txId:nat)"
```

####  Check Details of Several Transactions - getTransactions

Returns an array of transaction records in the range `[start, start + limit)`. To fend off DoS attacks, this function is allowed to trap, if limit is greater than the limit allowed by the token. This function is also allowed to trap if `start + limit > historySize()`.


```bash
dfx canister --network=ic --no-wallet call aanaa-xaaaa-aaaah-aaeiq-cai getTransactions "(start:nat, limit:nat)"
```

---

## 📡 User Query Calls

This query calls don't require a fee since they only query information.

---

###  Check Your Balance - balanceOf

Returns the balance of user `who`.

```bash
dfx canister --network=ic --no-wallet call --query aanaa-xaaaa-aaaah-aaeiq-cai balanceOf "(principal \"who-account-principal\")"
```

### Check the set allowance for an ID - allowance

Returns the amount which `spender` is still allowed to withdraw from `owner`.

```bash
dfx canister --network=ic --no-wallet call --query aanaa-xaaaa-aaaah-aaeiq-cai allowance "(principal \"owner-account-principal\", principal \"spender-account-principal\")"
```

---

## 🛰️ Metadata Query Calls

This query calls don't require a fee since they only query information.

---

### logo

Returns the logo of the Cycles Token (XTC).

```bash
dfx canister --network=ic --no-wallet call --query aanaa-xaaaa-aaaah-aaeiq-cai logo
```

### nameErc20

Returns the name of the token.

```bash
dfx canister --network=ic --no-wallet call --query aanaa-xaaaa-aaaah-aaeiq-cai nameErc20
```

### symbol

Returns the symbol of the token.

```bash
dfx canister --network=ic --no-wallet call --query aanaa-xaaaa-aaaah-aaeiq-cai symbol
```

### decimals

Returns the decimals of the token.

```bash
dfx canister --network=ic --no-wallet call --query aanaa-xaaaa-aaaah-aaeiq-cai decimals
```

### totalSupply

Returns the total supply of the token.

```bash
dfx canister --network=ic --no-wallet call --query aanaa-xaaaa-aaaah-aaeiq-cai totalSupply
```


### getMetadata

Returns the metadata of the token.

```bash
dfx canister --network=ic --no-wallet call --query aanaa-xaaaa-aaaah-aaeiq-cai getMetadata
```

### historySize

Returns the history size.

```bash
dfx canister --network=ic --no-wallet call --query aanaa-xaaaa-aaaah-aaeiq-cai historySize
```

---

## 🚨 Deprecated Methods

The XTC token previously utilized a different token standard interface [(see it here)](https://github.com/Psychedelic/standards/tree/main/standards/token-interface). **However, we have begun a migration to a new standard/interface** that follows a closer approach to ERC20, providing a well-known and familiar interface (with an allowances feature), including the extended functionalities XTC has (interacting with canisters, proxy calls, etc.).

During this transition, we deprecated **older methods following the previous standard**. They are still supported when interacting with XTC, but we are leaving a 2 months grace period to update integrations before deprecating them from the canister entirely.

These methods are:

### Check your balance on Cycles Token (Deprecated):

```bash
$ dfx canister --network=ic --no-wallet call aanaa-xaaaa-aaaah-aaeiq-cai balance "(null)"
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

### Transferring cycles to another XTC balance (Deprecated)
Send Cycles Token (XTC) to a Principal ID, balances change internally on the XTC ledger. (You should change the amount)

```bash
$ dfx canister --network=ic --no-wallet call aanaa-xaaaa-aaaah-aaeiq-cai transfer "(record { to= principal \"some-account's-principal-id\"; amount= (1000:nat64) })"
(variant { Ok = 2 })
```
