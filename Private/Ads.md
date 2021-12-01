# Ads endpoints

* [ADS](#ads)
    * [Ads](#ads)
    * [Info for order](#info-for-order)
    * [Info for definite order list](#info-for-definite-order-list)
    * [Create an advertisment](#create-an-advertisement)
    * [Update an advertisement](#update-an-advertisement)
    * [Delete an advertisement](#delete-an-advertisement)
    * [Update equation](#update-equation)
    * [Specified equation](#specified-equation)
    
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
**Responce**
```
{
    "data": {
        "ad_list": {
            "data": [
                {
                    "ad_id": "2980f546-29b6-4bed-a682-6f9a32838179",
                    "countrycode": "UA",
                    "currency": "UAH",
                    "max_amount": null,
                    "min_amount": null,
                    "max_amount_available": "10",
                    "online_provider": "NATIONAL_BANK",
                    "profile": {
                        "username": "Bodya003",
                        "feedback_score": "0",
                        "trade_count": 3,
                        "last_online": "2021-09-06T21:28:50+00:00",
                        "name": "Bodya003 (3; 0%)"
                    },
                    "bank_name": null,
                    "trade_type": "ONLINE_SELL",
                    "payment_window_minutes": null,
                    "display_reference": true,
                    "created_at": "2021-07-27T12:21:13+00:00",
                    "require_feedback_score": 0,
                    "msg": "xbcvxdfvb",
                    "account_info": "cvbxcvb",
                    "volume_coefficient_btc": "1.000000000000000000",
                    "temp_price": "51890.42",
                    "temp_price_usd": "51890.42",
                    "hidden_by_opening_hours": false,
                    "require_identification": false,
                    "is_local_office": false,
                    "first_time_limit_btc": null,
                    "city": "",
                    "location_string": "Ukraine",
                    "opening_hours": null,
                    "lon": 0,
                    "sms_verification_required": false,
                    "require_trade_volume": "0",
                    "limit_to_fiat_amounts": null,
                    "require_trusted_by_advertiser": false,
                    "track_max_amount": false,
                    "lat": 0,
                    "price_equation": "btc_in_usdt",
                    "visible": false,
                    "atm_model": null,
                    "reference_code": "ZTc1NzE1",
                    "reference_type": "SHORT"
                },
                {
                    "ad_id": "e0578e5e-a488-419f-98f8-962d406cb78f",
                    "countrycode": "UA",
                    "currency": "UAH",
                    "max_amount": "1000",
                    "min_amount": "100",
                    "max_amount_available": "10",
                    "online_provider": "MONOBANK",
                    "profile": {
                        "username": "Bodya003",
                        "feedback_score": "0",
                        "trade_count": 3,
                        "last_online": "2021-09-06T21:28:50+00:00",
                        "name": "Bodya003 (3; 0%)"
                    },
                    "bank_name": null,
                    "trade_type": "ONLINE_SELL",
                    "payment_window_minutes": null,
                    "display_reference": true,
                    "created_at": "2021-09-05T21:44:20+00:00",
                    "require_feedback_score": 0,
                    "msg": "-",
                    "account_info": "000",
                    "volume_coefficient_btc": "1.000000000000000000",
                    "temp_price": "57079.462",
                    "temp_price_usd": "57079.462",
                    "hidden_by_opening_hours": false,
                    "require_identification": false,
                    "is_local_office": false,
                    "first_time_limit_btc": null,
                    "city": "",
                    "location_string": "Ukraine",
                    "opening_hours": null,
                    "lon": 0,
                    "sms_verification_required": false,
                    "require_trade_volume": "0",
                    "limit_to_fiat_amounts": null,
                    "require_trusted_by_advertiser": false,
                    "track_max_amount": false,
                    "lat": 0,
                    "price_equation": "btc_in_usdt*1.1",
                    "visible": false,
                    "atm_model": null,
                    "reference_code": "OTUwYzhk",
                    "reference_type": "SHORT"
                }
            ]
        },
        "ad_count": 2
    }
}
```
<details>
<summary><b>Errors:</b></summary>
   
  ```
{
    "code": 0,
    "message": "Validation failed",
    "errors": {
        "ticker": [
            "The selected ticker is invalid."
        ]
    }
}
```
</details>


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

**Example request**
```
curl --location -g --request GET 'https://api.bitcoin.global/api/v1/ad-get/{ad_id}' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}'
```
**Responce**
```
{
    "ad_id": "3c4dbc84-ad01-41a0-98d2-cdb1b7e2eefe"
}
```
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
**Example request**
```
curl --location -g --request GET 'https://api.bitcoin.global/api/v1/ad-get?ads={ad_id}' \
--header 'Apiauth-Key: {{apiKey}}' \
--header 'Apiauth-Signature: {{signature}}' \
--header 'Apiauth-Nonce: {{nonce}}'
```
**Responce**
```
{
    "data": {
        "ad_list": {
            "data": [
                {
                    "ad_id": "{ad_id}",
                    "countrycode": "UA",
                    "currency": "UAH",
                    "max_amount": null,
                    "min_amount": null,
                    "max_amount_available": "10",
                    "online_provider": "NATIONAL_BANK",
                    "profile": {
                        "username": "username",
                        "feedback_score": "0",
                        "trade_count": 3,
                        "last_online": "2021-09-06T21:32:57+00:00",
                        "name": "Bodya003 (3; 0%)"
                    },
                    "bank_name": null,
                    "trade_type": "ONLINE_SELL",
                    "payment_window_minutes": null,
                    "display_reference": true,
                    "created_at": "2021-07-27T12:21:13+00:00",
                    "require_feedback_score": 0,
                    "msg": "xbcvxdfvb",
                    "account_info": "cvbxcvb",
                    "volume_coefficient_btc": "1.000000000000000000",
                    "temp_price": "51854.04",
                    "temp_price_usd": "51854.04",
                    "hidden_by_opening_hours": false,
                    "require_identification": false,
                    "is_local_office": false,
                    "first_time_limit_btc": null,
                    "city": "",
                    "location_string": "Ukraine",
                    "opening_hours": null,
                    "lon": 0,
                    "sms_verification_required": false,
                    "require_trade_volume": "0",
                    "limit_to_fiat_amounts": null,
                    "require_trusted_by_advertiser": false,
                    "track_max_amount": false,
                    "lat": 0,
                    "price_equation": "btc_in_usdt",
                    "visible": false,
                    "atm_model": null,
                    "reference_code": "ZTc1NzE1",
                    "reference_type": "SHORT"
                }
            ]
        },
        "ad_count": 1
    }
}
```
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
**Responce**
```
{
    "ad_id": "9d0534ad-e86b-46fe-91d9-71301991a2de"
}
```
<details>
<summary><b>Errors:</b></summary>
   
   ```json5
{
    "errors": {
        "opening_hours": "You submitted more or less than 7 values, expected 7"
    }
}
```
   
     ```json5
{
    "errors": {
        "opening_hours": "JSON data invalid!"
    }
}
```
   
   ```json5
{
    "errors": {
        "opening_hours": "The maximum value can be 92. This is equivalent to 23:00"
    }
}
```
   
   ```
   {
    "errors": {
        "opening_hours": "Data cannot have negative values."
    }
}
```
   
   ```
   {
    "errors": {
        "opening_hours": "Hour parameters must be divisible by 4, e.g. 4 or 8, or 12"
    }
}
```
   
   ```
   {
    "errors": {
        "opening_hours": "The hour of the start cannot be more than the hour of the end"
    }
}
```
   
    ```
  {
    "errors": [
        "No enough money on balance for order fee"
    ]
}
```
   
</details>


   
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
**Responce**
```
{
    "ad_id": "3c4dbc84-ad01-41a0-98d2-cdb1b7e2eefe"
}
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
**Responce**
```
{
    "order": {
        "ad_id": "3c4dbc84-ad01-41a0-98d2-cdb1b7e2eefe",
        "status": "DELETED"
    }
}
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
**Responce**
```
{
    "ad_id": "e0578e5e-a488-419f-98f8-962d406cb78f"
}
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
**Responce**
```
{
    "ad_id": "e0578e5e-a488-419f-98f8-962d406cb78f"
}
```
