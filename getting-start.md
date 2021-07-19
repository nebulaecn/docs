# Getting Started

## Preparation

Before you use API, you need to login the website to create API Key with proper permissions.

You can manage your API Key in UI or by [Authenticating API](rest-api/authenticating.md). See the [Authentication Guide](guides/authentication-guide.md)

Every user can create at  API Keys, each can be applied with either permission below:

* Read permission: It is used to query the data, such as order query, trade query.
* Trade permission: It is used to create order, cancel order and transfer, etc.
* Withdraw permission: It is used to create withdraw order, cancel withdraw order, etc.



## Issuing API Credentials

You can get your API credentials after passing verification process. You need to reach Level 3. That requires your email & phone to be verified, enable 2FA enabled and complete KYB.

![](.gitbook/assets/image%20%2828%29.png)



## Interface Type

There are two types of interface, you can choose the proper one according to your scenario and preferences.



### REST API

REST \(Representational State Transfer\) is one of the most popular communication mechanism under HTTP, each URL represents a type of resource.

It is suggested to use Rest API for one-off operation, like trading and withdraw.



### WebSocket API

WebSocket is a new protocol in HTML5. It is full-duplex between client and server. The connection can be established by a single handshake, and then server can push the notification to client actively.

It is suggest to use WebSocket API to get data update, like market data and order update.



**Authentication**

Both API has two levels of authentication:

Public API: It is for basic information and market data. It doesn't need authentication.

Private API: It is for account related operation like trading and account management. Each private API must be authenticated with API Key.

