# Trade endoints of Bitcoin Global API

 * [Trade](#trade)
    * [Deals](#deals)
 
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
**Responce**
```
{
    "data": {
        "contact_list": []
    },
    "contact_count": 0
}
```
