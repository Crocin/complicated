
# Meta Tokens

With this feature, you can securely store one or more payment details in the form of alternate tokens per shopper across multiple shops. This allows you to use saved payment details across multiple shops under the same enterprise and have faster payment check out experience across multiple shops.



## Benefits of meta tokens

+ Shoppers can save payment details in one shop and use the same for other shops under the same enterprise
+ Shoppers can expect reduced payment retries and faster payment checkout times
+ Subscription based business models can expect reduced payment tries accross multiple platforms

To make your payment with saved payment details, you need to pass a additional parameter meta token Id in the payments request.

[comment]: The document mentions that the meta tokens are beneficial in subscription based business models, I would ask the developer if there are any other business models that are benefitted and if the same Request and Response are required for the same
## PCI Compliance
[comment]: The payment industry talks alot about PCI compliance so i think it is important to mention about it in the beginning
## Getting Started
+ [comment]: I would like to mention here about the YOUR_API_KEY parameter that is how the Developer needs to obtain the Authentication or Authorization to use the API .I would ask the Developer to get me the details of the Authentication and Authorization flow that is being followed in the company or how the customer set up their accounts and so on
+ [comment]: I would like to ask the developer if the requests can be sent by any customer or how does the owner of the business implement this functionality. Is it available to anyone or is this functionality available for specific roles in enterprises
## Meta Token functionality

### Create a meta token
You can create meta token and use them to save the payment details for:
+ Subscriptions: Shoppers can save payment details for subscription based payments and use the saved details on multiple platforms under the same enterprise

+ <!-- I would like some more details here about which type of payments the meta tokens can be created for, the document mentions Subscription based payments -->

+ <!-- I would ask for the actual test scripts for these request and test them on POSTMAN or any other testing tool --> 

##HTTP Method

```https://checkout-test.adyen.com/v68/metaTokens
  POST /checkout-test.adyen.com/v68/metaTokens
```
#### Request code:

curl https://checkout-test.adyen.com/v68/metaTokens \
-H 'x-api-key: ' \
-H 'content-type: application/json' \
-d '{
"shopperReference": "shopper-123",
"merchantAccount": "YOUR_MERCHANT_ACCOUNT"}'

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `api_key` | `string` | **Required**. Your API key
|shopperReference |`string`|[Comment]: Need this info from developer|
|merchantAccount|`string`|[Comment]: Need this info from developer|

#### Response Code:

```json
{
"merchantAccount": "YOUR_MERCHNAT_ACCOUNT",
"shopperReference": "yourShopperReference",
"metaTokenId": "9647-2876"
}
```
+ ***Comment***: What is the value of merchant account and yourshopper reference string or numeric

***

```
Note: Response Times: The token creation might take upto to couple of minutes to half an hour***


```
***

+ [Comment]: I would ask the developer this time depends on what and does the user require to do anything to reduce this time

### Response Error Code:
+ [Comment]: Here, I would ask the developer how many times the user can try again if they get this error code to successfully generate a metatoken 

```json
{
  "live": "false",
  "notificationItems": [
    {
      "NotificationRequestItem": {
        "eventCode": "META_TOKEN_CREATION",
        "reason": "Technical error",
        "success": "false"
      }
    }
  ]
}
```

+[Comment]:I would ask the developer if we should mention that only one value of Reason Code is avialable right now and more will be added in later versions

### Webhook Notification Response Code:
You will receive a webhook notification when the meta token is successfully created


{
"live": "false",
"notificationItems": [ {
"NotificationRequestItem": {
"merchantAccount": "YOUR_MERCHNAT_ACCOUNT"
"eventCode": "META_TOKEN_CREATION",
"metaTokenId": "9647-2876",
"success": "true"
}} ]}


### Make payments with meta token
You can make a payment with a MetaToken after including the metaTokenId 

```https://checkout-test.adyen.com/v68/payments
  POST /checkout-test.adyen.com/v68/payments
```
+ [Comment] : Here I would like to ask the developer the request and response details of the payment 


