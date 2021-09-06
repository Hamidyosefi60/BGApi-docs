# Wallet endpoints of Bitcoin Global API
* [Wallet](#wallet)
 * [Codes](#codes)
    * [Create a WB code](#create-a-wb-code)
    * [Apply WB code](#apply-wb-code)
    * [Currency Balance](#currency-balance)
    * [Generate address](#generate-address)
    * [Create Withdraw](#create-withdraw)
    * [Transactions](#Transactions)
    * [Adresses](#Adresses)
 
 ## Wallet
   ## Codes
   ### Create a WB code
   #### POST/api/bg-wallet/wallet/codes
```
https://api.bitcoin.global/api/bg-wallet/wallet/codes
```
Allows API user to create a WB code.

**HEADERS**

X-API-KEY | {{apiKey}} 
------------ | ------------ 
X-ACCESS-TIMESTAMP| {{nonce}}
X-ACCESS-SIGN|  {{signature}}

**BODY** raw
```
{
    "code": {
        "amount": "50",
        "ticker": "USDT",
        "passphrase": "strongpass",
        "description": "randomtext"
    }
}
```

**Example request**
```
curl --location --request POST 'https://api.bitcoin.global/api/bg-wallet/wallet/codes' \
--header 'X-API-KEY: {{apiKey}}' \
--header 'X-ACCESS-TIMESTAMP: {{nonce}}' \
--header 'X-ACCESS-SIGN: {{signature}}' \
--data-raw '{
    "code": {
        "amount": "50",
        "ticker": "USDT",
        "passphrase": "strongpass",
        "description": "randomtext"
    }
}'
```
**Responce**
```
{
    "code": 7,
    "message": "Network Error"
}
```
### Apply WB code
   #### POST/api/bg-wallet/wallet/apply-code
```
https://api.bitcoin.global/api/bg-wallet/wallet/apply-code
```
Allows API user to activate a WB code.

**HEADERS**

X-API-KEY | {{apiKey}} 
------------ | ------------ 
X-ACCESS-TIMESTAMP| {{nonce}}
X-ACCESS-SIGN|  {{signature}}

**BODY** raw
```
{
    "code" : "WBe11f4fce-2a53-4edc-b195-66b693bd77e3USDT",
    "passphrase": "strongpass"
}
```

**Example request**
```
curl --location --request POST 'https://api.bitcoin.global/api/bg-wallet/wallet/apply-code' \
--header 'X-API-KEY: {{apiKey}}' \
--header 'X-ACCESS-TIMESTAMP: {{nonce}}' \
--header 'X-ACCESS-SIGN: {{signature}}' \
--data-raw '{
    "code" : "WBe11f4fce-2a53-4edc-b195-66b693bd77e3USDT",
    "passphrase": "strongpass"
}'
```
**Responce**
```

```
### Currency Balance
   #### GET/api/simple-wallet/wallet/balance
```
https://api.bitcoin.global/api/simple-wallet/wallet/balance?currency=BTC
```

**HEADERS**

X-API-KEY | {{apiKey}} 
------------ | ------------ 
X-ACCESS-TIMESTAMP| {{nonce}}
X-ACCESS-SIGN|  {{signature}}

**BODY** urlencoded

currency| BTC
------------ | ------------


**Example request**
```
curl --location --request GET 'https://api.bitcoin.global/api/simple-wallet/wallet/balance?currency=BTC' \
--header 'X-API-KEY: {{apiKey}}' \
--header 'X-ACCESS-TIMESTAMP: {{nonce}}' \
--header 'X-ACCESS-SIGN: {{signature}}'
```
**Responce**
```
{
    "balance": "10.001000006",
    "currency": "BTC",
    "error": "ok"
}
```
### Generate address
   #### POST/api/simple-wallet/wallet/address/generate
```
https://api.bitcoin.global/api/simple-wallet/address/generate
```

**HEADERS**

X-API-KEY | {{apiKey}} 
------------ | ------------ 
X-ACCESS-TIMESTAMP| {{nonce}}
X-ACCESS-SIGN|  {{signature}}

**BODY** raw
```
{
    "currency": "USDT",
    "network": "TRC20",
    "label": "label_name",
    "ipn_url": "https://yourwebsite.com/..."
}
```
**Example request**
```
curl --location --request POST 'https://api.bitcoin.global/api/simple-wallet/address/generate' \
--header 'X-API-KEY: {{apiKey}}' \
--header 'X-ACCESS-TIMESTAMP: {{nonce}}' \
--header 'X-ACCESS-SIGN: {{signature}}' \
--data-raw '{
    "currency": "USDT",
    "network": "TRC20",
    "label": "label_name",
    "ipn_url": "https://yourwebsite.com/..."
}'
```
**Responce**
```
{
    "error": "ok",
    "result": []
}
```
### Create Withdraw
   #### POST/api/simple-wallet/wallet/create_whithdrawal
```
https://api.bitcoin.global/api/simple-wallet/wallet/create_withdrawal
```

**HEADERS**

X-API-KEY | {{apiKey}} 
------------ | ------------ 
X-ACCESS-TIMESTAMP| {{signature}}
X-ACCESS-SIGN| {{nonce}}

**BODY** raw
```
{
    "currency": "USDT",
    "network": "ERC20", //or "TRC20"
    "address": "USDT_address",
    "amount": "0.002",
    "description": "random text", //optional
    "dest_tag": "1390985919", //required for some currencies
    "priority": "low" //low or medium or high
}
```
**Example request**
```
curl --location --request POST 'https://api.bitcoin.global/api/simple-wallet/wallet/create_withdrawal' \
--header 'X-API-KEY: {{apiKey}}' \
--header 'X-ACCESS-TIMESTAMP: {{signature}}' \
--header 'X-ACCESS-SIGN: {{nonce}}' \
--data-raw '{
    "currency": "USDT",
    "network": "ERC20", //or "TRC20"
    "address": "USDT_address",
    "amount": "0.002",
    "description": "random text", //optional
    "dest_tag": "1390985919", //required for some currencies
    "priority": "low" //low or medium or high
}'
```
**Responce**
```
{
    "id": 45307654446708017,
    "amount": "0.01",
    "address": "address",
    "dest_tag": "",
    "currency": "BTC",
    "status": "pending",
    "blockchain_hash": null,
    "fee": "0.000010000000000000",
    "error": "ok"
}
```
### Transactions
   #### POST/api/simple-wallet/wallet/transactions
```
https://api.bitcoin.global/api/simple-wallet/wallet/transactions
```

**HEADERS**

X-API-KEY | {{apiKey}} 
------------ | ------------ 
X-ACCESS-TIMESTAMP| {{nonce}}
X-ACCESS-SIGN|  {{signature}}

**BODY** raw
```
{
    "id": "transaction_id"
}
```
**Example request**
```
curl --location --request POST 'https://api.bitcoin.global/api/simple-wallet/wallet/transaction' \
--header 'X-API-KEY: {{apiKey}}' \
--header 'X-ACCESS-TIMESTAMP: {{nonce}}' \
--header 'X-ACCESS-SIGN: {{signature}}' \
--data-raw '{
    "id": "transaction_id"
}'
```
**Responce**
```
{
    "error": "ok",
    "count": 0,
    "result": []
}
```
### Adresses
   #### GET/api/simple-wallet/wallet/addresses
```
https://api.bitcoin.global/api/simple-wallet/wallet/addresses
```

**HEADERS**

X-API-KEY | {{apiKey}} 
------------ | ------------ 
X-ACCESS-TIMESTAMP| {{nonce}}
X-ACCESS-SIGN|  {{signature}}

**Example request**
```
curl --location --request GET 'https://api.bitcoin.global/api/simple-wallet/wallet/addresses' \
--header 'X-API-KEY: {{apiKey}}' \
--header 'X-ACCESS-TIMESTAMP: {{nonce}}' \
--header 'X-ACCESS-SIGN: {{signature}}'
```
**Responce**
```
{
    "error": "ok",
    "result": [
        {
            "address": "GMBY9bZLNCFNuwJWS4pP3rcHAoWBWvqJcm",
            "label": null,
            "dest_tag": "",
            "ipn_url": null,
            "currency": "BTC",
            "network": "BTC"
        }
    ]
}
```
