# General endpoints

* [General](#general)
    * [Payment methods](#payment-methods)
    * [Payment methods for country](#payment-methods-for-country)
    * [Countrycodes](#countrycodes)
    * [currencies](#currencies)
    
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
**Responce**
```
{
    "data": {
        "methods": {
            "tigopesa_tanzania": {
                "code": "TIGOPESA_TANZANIA",
                "name": "Tigo-Pesa Tanzania",
                "currencies": [
                    "UAH",
                    "RUB",
                    "DZDD",
                    "ZWL",
                   ....
                ]
            }
        },
        "method_count": 77
    }
}
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
**Responce**
```
{
    "data": {
        "cc_list": [
            "BY",
            "MR",
            "LT",
            "BD",
            "BE",
            ...
        ],
        "cc_count": 249
    }
}
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
**Responce**
```
{
    "currencies": {
        "collection": {
            "UAH": {
                "name": "Ukrainian Hryvnia",
                "altcoin": false
            },
            "RUB": {
                "name": "Russian Ruble",
                "altcoin": false
            },
            ...
        },
        "total": 173
    }
}
```
___
