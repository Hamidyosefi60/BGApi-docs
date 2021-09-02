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

```
GET/api/v1/payment_methods
```
Returns a list of valid payment methods. Also contains name and code for payment methods, and possible limitations in currencies and bank name choices.

**HEADERS**

Apiauth-Key| {{apiKey}} 
------------ | ------------ 
Apiauth-Signature| {{signature}} 
------------ | ------------ 
Apiauth-Nonce| {{nonce}} 

**Example request**
```
curl --location --request GET 'https://api.bitcoin.global/api/v1/payment_methods' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}'
```

### Payment methods for country

## ADS

## Wallet

## Trade
      
