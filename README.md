Preview:
Internet Unique ID Identifier
![image](https://github.com/TanujJha/Crypto-Token-Wallet/assets/97455430/0cfdc4ed-780d-4af3-8806-d839f43c4413)
![image](https://github.com/TanujJha/Crypto-Token-Wallet/assets/97455430/317612e1-b40f-418f-8468-b5937c1e5a5a)

Wallet

![image](https://github.com/TanujJha/Crypto-Token-Wallet/assets/97455430/21c95e83-bbb1-41d2-8e58-3e87f5be7095)

# Check your Balance

1. Find out your principal id:

```
dfx identity get-principal
```

2. Save it somewhere.

e.g. My principal id is: wzew5-zo54i-4gwhl-kz334-rodx2-xohkb-mby5g-mehta-mtfmc-divq5-xae

3. Format and store it in a command line variable:

```
OWNER_PUBLIC_KEY="principal \"$( \dfx identity get-principal )\""
```

4. Check that step 3 worked by printing it out:

```
echo $OWNER_PUBLIC_KEY
```

5. Check the owner's balance:

```
dfx canister call token_backend balanceOf "( $OWNER_PUBLIC_KEY )"
```

# Charge the Canister

1. Check canister ID:

```
dfx canister id token_backend
```

2. Save canister ID into a command line variable:

```
CANISTER_PUBLIC_KEY="principal \"$( \dfx canister id token_backend )\""
```

3. Check canister ID has been successfully saved:

```
echo $CANISTER_PUBLIC_KEY
```

4. Transfer half a billion tokens to the canister Principal ID:

```
dfx canister call token_backend transfer "($CANISTER_PUBLIC_KEY, 500_000_000)"
```

2vxsx-fae

# Deploy the Project to the Live IC Network

1. Create and deploy canisters:

```
dfx deploy --network ic
```

2. Check the live canister ID:

```
dfx canister --network ic id token_backend
```

3. Save the live canister ID to a command line variable:

```
LIVE_CANISTER_KEY="principal \"$( \dfx canister --network ic id token_backend )\""
```

4. Check that it worked:

```
echo $LIVE_CANISTER_KEY
```

5. Transfer some tokens to the live canister:

```
dfx canister --network ic call token_backend transfer "($LIVE_CANISTER_KEY, 50_000_000)"
```

6. Get live canister front-end id:

```
dfx canister --network ic id token_frontend
```

7. Copy the id from step 6 and add .raw.ic0.app to the end to form a URL.
   e.g. zdv65-7qaaa-aaaai-qibdq-cai.raw.ic0.app
