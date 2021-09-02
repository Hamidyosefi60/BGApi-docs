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
## Wallet

## Trade
      
