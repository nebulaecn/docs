# Authentication Guide

This section is under development

## Get API key using the interface

* Enable Two-factor authentication [https://api.nebulaecn.com/security/2fa](https://api.nebulaecn.com/security/2fa)

![](../.gitbook/assets/image%20%281%29.png)

* Click "Create New" button at My API Keys Section
* Enter 2fa code
* Please remember the below information after creation:
  * `Access Key` It is used in API request
  * `Secret Key` It is used to generate the signature \(only visible once after creation\)
* Click Confirm Button

## **How to use API key**

Before calling private endpoint you will need to generate three headers:

`X-Auth-Apikey` - API key \(from previous step\)

`X-Auth-Nonce` - A nonce is an arbitrary number that can be used just once. You _MUST_ use a millisecond timestamp in UTC time. Read more about it [here](https://en.wikipedia.org/wiki/Cryptographic_nonce).

Example:

```text
date +%s%3N
1584087661035
```

 `X-Auth-Signature` - HMAC-SHA256 signature calculated using a concatenation of X-Auth-Nonce and X-Auth-Apikey. Hexdigest secret is your API Secret. 

#### Sample Request below:

```text
curl -X GET https://api.nebulaecn.com/v1/account/balances \
-H "X-Auth-Apikey: "Your Api Key" \
-H "X-Auth-Nonce: "Nonce" \
-H "X-Auth-Signature: "HMAC-SHA256 signature"
```





