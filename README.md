# Official Documentation of Bitcoin Global API

* [General](/General.md)
    * [Payment methods](/General.md#payment-methods)
    * [Payment methods for country](/General.md#payment-methods-for-country)
    * [Countrycodes](/General.md#countrycodes)
    * [currencies](/General.md#currencies)
* [ADS](/Ads.md)
    * [Ads](#ads)
    * [Info for order](/Ads.md#info-for-order)
    * [Info for definite order list](/Ads.md#info-for-definite-order-list)
    * [Create an advertisment](/Private/Ads.md#create-an-advertisement)
    * [Update an advertisement](/Private/Ads.md#update-an-advertisement)
    * [Delete an advertisement](/Private/Ads.md#delete-an-advertisement)
    * [Update equation](/Private/Ads.md#update-equation)
    * [Specified equation](/Private/Ads.md#specified-equation)
 * [Wallet](/Private/Wallet.md)
 * [Codes](/Private/Wallet.md#codes)
    * [Create a WB code](/Private/Wallet.md#create-a-wb-code)
    * [Apply WB code](/Private/Wallet.md#apply-wb-code)
    * [Currency Balance](/Private/Wallet.md#currency-balance)
    * [Generate address](/Private/Wallet.md#generate-address)
    * [Create Withdraw](/Private/Wallet.md#create-withdraw)
    * [Transactions](/Private/Wallet.md#Transactions)
    * [Adresses](/Private/Wallet.md#Adresses)
 * [Trade](/Private/Trade.md)
    * [Deals](/Private/Trade.md#deals)
 
 
## Info HTTP

1. Bitcoin Global API supports `private` methods.
2. Available API versions: `V1`.
3. Using **Private endpoints**:
    1. To make private API calls:
        1. Go to your account on bitcoin.global
        2. Go to Settings, click on the API tab.
        3. Generate API keys.
    2. Auth request should be using `POST` method and should include:
        1. Body data - **JSON** that includes:
            1. **'request'** - a request path without the domain name. Example: `'/api/v1/payment_methods'`.
            2. **'nonce'** - a number that is always **larger** than the previous request’s nonce number. Example: `'1594297865'`. A good method of creating a **nonce** is to use the unix timestamp in milliseconds. This way you'll always get an incrementing number, but make sure not to send two API calls at the same time, otherwise their nonce will be identical.
            3. **params of request** - Example: `'ticker': 'BTC'`
        2. Headers:
            1. `'Content-type': 'application/json'`
            2. `'Apiauth-Key': {{apiKey}}` - where api_key is your public Bitcoin Global API key
            3. `'Apiauth-Nonce': {{nonce}}` - where nonce is  number that is always **larger** than the previous request’s nonce number from your json body
            4. `'Apiauth-Signature': {{signature}}` - where signature is `hex(HMAC_SHA256 (payload)('utf-8'), key=api_secret, encoded('utf-8'))`
        3. To help you get started with our API, we've created the [API Quick start helper](https://github.com/bohdanBG/BGapi_quickstart) library. It supports the following languages:
            1. ``Go``
            2. ``NodeJS``
            3. ``Python``
            4. ``PHP``
            5. ``Java``
            6. ``Kotlin``
            7. ``DotNet``
            8. ``Ruby``
            9. ``C++``
