# DANG — a token and wallet on the Internet Computer

A custom crypto token with a wallet frontend: check a balance against your principal ID, and transfer tokens to another principal.

Course project, November 2023.

---

## ⚠️ State of this repository

**The committed backend canister is the generated starter, not the finished token.** `src/token_backend/main.mo` contains the default `greet` actor from `dfx new`; the token logic — `balanceOf`, `transfer`, the owner's initial supply — was written during the course but is not in this repository.

The frontend and the project configuration are here, and the walkthrough below is kept because it documents how the finished version was driven. Treat this as an in-progress exercise rather than a working token.

## What the exercise covers

- Minting a fixed supply of a custom token to an owner principal
- Checking a balance for any principal ID
- Transferring tokens between principals
- A wallet frontend that identifies the user by their Internet Computer principal

## Stack

- **Motoko** for the token canister
- Vanilla JavaScript frontend
- **DFINITY SDK (`dfx`)**
- Webpack

## Running it

You need the [DFINITY SDK](https://internetcomputer.org/docs/current/developer-docs/setup/install) installed.

```bash
dfx start --background
npm install
dfx deploy
```

Find your principal ID:

```bash
dfx identity get-principal
```

Then query the canister with it:

```bash
OWNER_PUBLIC_KEY="principal \"$( dfx identity get-principal )\""
dfx canister call token_backend balanceOf "( $OWNER_PUBLIC_KEY )"
```

## What it demonstrates

Principal-based identity on the Internet Computer, passing typed arguments to a canister from the CLI, and the shape of a token ledger — balances keyed by principal, with transfers validated against the sender's balance.
