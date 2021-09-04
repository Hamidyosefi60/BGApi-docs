# Official Documentation of Bitcoin Global API

* [General](#general)
    * [Payment methods](#payment-methods)
    * [Payment methods for country](#payment-methods-for-country)
    * [Countrycodes](#countrycodes)
    * [currencies](#currencies)
* [ADS](#ads)
    * [Ads](#ads)
    * [Info for order](#info-for-order)
    * [Info for definite order list](#info-for-definite-order-list)
    * [Create an advertisment](#create-an-advertisement)
    * [Update an advertisement](#update-an-advertisement)
    * [Delete an advertisement](#delete-an-advertisement)
    * [Update equation](#update-equation)
    * [Specified equation](#specified-equation)
 * [Wallet](#wallet)
 * [Codes](#codes)
    * [Create a WB code](#create-a-wb-code)
    * [Apply WB code](#apply-wb-code)
    * [Currency Balance](#currency-balance)
    * [Generate address](#generate-address)
    * [Create Withdraw](#create-withdraw)
    * [Transactions](#Transactions)
    * [Adresses](#Adresses)
 * [Trade](#trade)
    * [Deals](#deals)
## General

### Payment methods
   #### GET/api/v1/payment_methods

```
https://api.bitcoin.global/api/v1/payment_methods
```
Returns a list of valid payment methods. Also contains name and code for payment methods, and possible limitations in currencies and bank name choices.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}} 

**Example request**
```
curl --location --request GET 'https://api.bitcoin.global/api/v1/payment_methods' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}'
```

### Payment methods for country
   #### GET/api/v1/payment_methods/{country}

```
https://api.bitcoin.global/api/v1/payment_methods/{country_code}
```
Returns List of valid payment methods in the specific country.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**Example request**
```
curl --location -g --request GET 'https://api.bitcoin.global/api/v1/payment_methods/{country_code}' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}'
```

### Countrycodes
   #### GET/api/v1/countrycodes
```
https://api.bitcoin.global/api/v1/countrycodes
```
Returns list of valid countrycodes for Bitcoin Global.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**Example request**
```
curl --location --request GET 'https://api.bitcoin.global/api/v1/countrycodes' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}'
```
### Currencies
   #### GET/api/v1/currencies
```
https://api.bitcoin.global/api/v1/currencies
```
Returns List of valid and recognized fiat currencies for Bitcoin Global.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**Example request**
```
curl --location --request GET 'https://api.bitcoin.global/api/v1/currencies' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}'
```
## ADS

### Ads
   #### GET/api/v1/ads
```
https://api.bitcoin.global/api/v1/ads?countrycode={country_code}&currency={currency}&trade_type=ONLINE_SELL
```
Returns all advertisements of the authenticated user.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**PARAMS**

countrycode| {country_code} 
------------ | ------------ 
currency | {currency}
trade_type | ONLINE_SELL

**Example request**
```
curl --location -g --request GET 'https://api.bitcoin.global/api/v1/ads?countrycode={country_code}&currency={currency}&trade_type=ONLINE_SELL' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Nonce: {{nonce}}' \
--header 'Apiauth-Signature: {{signature}}'
```
### Info for order
   #### GET/api/v1/ad-get/{id}
```
https://api.bitcoin.global/api/v1/ad-get/{ad_id}
```
Returns information on a single advertisement.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

### Info for definite order list
   #### GET/api/v1/ad-get/?ads={ad_id}
```
https://api.bitcoin.global/api/v1/ad-get?ads={ad_id}
```
Returns all ads from a list of comma separated ad ID's.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**PARAMS**

Ads| {ad_id} 
------------ | ------------ 

### Create an advertisment
   #### POST/api/v1/ad-create
```
https://api.bitcoin.global/api/v1/ad-create
```
Create a new advertisement.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**BODY** urlencoded

coefficient| 1 
------------ | ------------ 
trade_type| ONLINE_SELL 
price_equation| btc_in_usd*BTC_in_RUB
volume_coefficient_btc|1
account_info| payment_details 
payment_window_minutes| 90 
track_max_amount| false 
bank_name| bank_name
min_amount| 10 
max_amount| 0 
msg| msg 
payment_method_name| payment_method_name
countrycode| RU
currency| RUB
online_provider| NATIONAL_BANK
first_time_limit_btc| 0
require_trade_volume| 1
require_feedback_score| 0
reference_type| SHORT
display_reference| true
visible| true
floating| false
lat| 0
lon| 0
city| city
location_string| location_string
sms_verification_required| false
require_trusted_by_advertiser| false
require_identification| false
opening_hours| []

**Example request**
```
curl --location --request POST 'https://api.bitcoin.global/api/v1/ad-create' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}' \
--data-urlencode 'coefficient=1' \
--data-urlencode 'trade_type=ONLINE_SELL' \
--data-urlencode 'price_equation=btc_in_usd*BTC_in_RUB' \
--data-urlencode 'volume_coefficient_btc=1' \
--data-urlencode 'account_info=payment_details' \
--data-urlencode 'payment_window_minutes=90' \
--data-urlencode 'track_max_amount=false' \
--data-urlencode 'bank_name=bank_name' \
--data-urlencode 'min_amount=10' \
--data-urlencode 'max_amount=0' \
--data-urlencode 'msg=msg' \
--data-urlencode 'payment_method_name=payment_method_name' \
--data-urlencode 'countrycode=RU' \
--data-urlencode 'currency=RUB' \
--data-urlencode 'online_provider=NATIONAL_BANK' \
--data-urlencode 'first_time_limit_btc=0' \
--data-urlencode 'require_trade_volume=1' \
--data-urlencode 'require_feedback_score=0' \
--data-urlencode 'reference_type=SHORT' \
--data-urlencode 'display_reference=true' \
--data-urlencode 'visible=true'
```

### Update an advertisment
   #### POST/api/v1/ad/{ad_id}
```
https://api.bitcoin.global/api/v1/ad/{ad_id}
```
Sending a request to /api/ad/{ad_id}/ with the HTTP method POST for an advertisement ID that was created by the token owner results in the advertisement being updated.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**BODY** urlencoded

coefficient| 1 
------------ | ------------ 
trade_type| ONLINE_SELL 
price_equation| btc_in_usd*BTC_in_UAH
volume_coefficient_btc|1
account_info| payment_details 
payment_window_minutes| 90 
track_max_amount| false 
bank_name| bank_name
min_amount| 0 
max_amount| 10 
msg| msg 
payment_method_name| payment_method_name
countrycode| UA
currency| UAH
online_provider| NATIONAL_BANK
first_time_limit_btc| 0
require_trade_volume| 1
require_feedback_score| 0
reference_type| SHORT
display_reference| true
visible| true
floating| false
lat| 0
lon| 0
city| city
location_string| location_string
sms_verification_required| false
require_trusted_by_advertiser| false
require_identification| false
opening_hours| []

**Example request**
```
curl --location -g --request POST 'https://api.bitcoin.global/api/v1/ad/{ad_id}' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}' \
--data-urlencode 'coefficient=1' \
--data-urlencode 'trade_type=ONLINE_SELL' \
--data-urlencode 'price_equation=btc_in_usd*BTC_in_UAH' \
--data-urlencode 'volume_coefficient_btc=1' \
--data-urlencode 'account_info=payment_details' \
--data-urlencode 'payment_window_minutes=90' \
--data-urlencode 'track_max_amount=false' \
--data-urlencode 'bank_name=bank_name' \
--data-urlencode 'min_amount=0' \
--data-urlencode 'max_amount=10' \
--data-urlencode 'msg=msg' \
--data-urlencode 'payment_method_name=payment_method_name' \
--data-urlencode 'countrycode=UA' \
--data-urlencode 'currency=UAH' \
--data-urlencode 'online_provider=NATIONAL_BANK' \
--data-urlencode 'first_time_limit_btc=0' \
--data-urlencode 'require_trade_volume=1' \
--data-urlencode 'require_feedback_score=0' \
--data-urlencode 'reference_type=SHORT' \
--data-urlencode 'display_reference=true' \
--data-urlencode 'visible=true'
```

### Delete an advertisment
   #### POST/api/v1/ad-delete/{ad_id}
```
https://api.bitcoin.global/api/v1/ad-delete/{ad_id}
```
Sending a request to this endpoint with an advertisement ID created by the token owner deletes the advertisement.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**Example request**
```
curl --location -g --request POST 'https://api.bitcoin.global/api/v1/ad-delete/{ad_id}' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}'
```
### Update equation
   #### POST/api/v1/ad-equation/{ad_id}/
```
https://api.bitcoin.global/api/v1/ad-equation/{ad_id}
```
Update equation of an advertisement.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**BODY** urlencoded

price_equation| btc_in_usd*USD_in_EUR*1.12
------------ | ------------ 

**Example request**
```
curl --location -g --request POST 'https://api.bitcoin.global/api/v1/ad-equation/{ad_id}' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}' \
--data-urlencode 'price_equation=btc_in_usd*USD_in_EUR*1.12'
```
### Specified equation
   #### GET/api/v1/equation/{formula}}
```
https://api.bitcoin.global/api/v1/equation/{formula}
```
Calculates the current price for bitcoin with the specified equation.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**Example request**
```
curl --location -g --request GET 'https://api.bitcoin.global/api/v1/equation/{formula}' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}' \
--data-raw ''
```

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
## Trade
   ### Deals
   #### GET/api/v1/dashboard
  
```
https://api.bitcoin.global/api/v1/dashboard
```
This endpoint retrieves open deals for your account.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}}
Apiauth-Nonce| {{nonce}}

**Example request**
```
curl --location --request GET 'https://api.bitcoin.global/api/v1/dashboard' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}'
```
