# Official Documentation of Bitcoin Global API

* [General](/General.md)
    * [Payment methods](/General.md#payment-methods)
    * [Payment methods for country](#payment-methods-for-country)
    * [Countrycodes](#countrycodes)
    * [currencies](#currencies)
* [ADS](/Ads.md)
    * [Ads](#ads)
    * [Info for order](#info-for-order)
    * [Info for definite order list](#info-for-definite-order-list)
    * [Create an advertisment](#create-an-advertisement)
    * [Update an advertisement](#update-an-advertisement)
    * [Delete an advertisement](#delete-an-advertisement)
    * [Update equation](#update-equation)
    * [Specified equation](#specified-equation)
 * [Wallet](/Wallet.md)
 * [Codes](#codes)
    * [Create a WB code](#create-a-wb-code)
    * [Apply WB code](#apply-wb-code)
    * [Currency Balance](#currency-balance)
    * [Generate address](#generate-address)
    * [Create Withdraw](#create-withdraw)
    * [Transactions](#Transactions)
    * [Adresses](#Adresses)
 * [Trade](/Trade.md)
    * [Deals](#deals)
 
 
## Info HTTP

1. Bitcoin Global API supports `private` and `public` methods.
2. Available API versions: `V1`.
3. Using **Private endpoints**:
    1. To make private API calls:
        1. Go to your account on bitcoin.global
        2. Go to Settings, click on the API tab.
        3. Generate API keys and toggle the activation switcher to "Activated".
    2. Auth request should be using `POST` method and should include:
        1. Body data - **JSON** that includes:
            1. **'request'** - a request path without the domain name. Example: `'/api/v1/simple-wallet/wallet/balances'`.
            2. **'nonce'** - a number that is always **larger** than the previous request’s nonce number. Example: `'1594297865'`. A good method of creating a **nonce** is to use the unix timestamp in milliseconds. This way you'll always get an incrementing number, but make sure not to send two API calls at the same time, otherwise their nonce will be identical.
            3. **params of request** - Example: `'ticker': 'BTC'`
        2. Headers:
            1. `'Content-type': 'application/json'`
            2. `'X-TXC-APIKEY': api_key` - where api_key is your public WhiteBit API key
            3. `'X-TXC-PAYLOAD': payload'` - where payload is base64-encoded body data
            4. `'X-TXC-SIGNATURE': signature` - where signature is `hex(HMAC_SHA512(payload), key=api_secret))`
