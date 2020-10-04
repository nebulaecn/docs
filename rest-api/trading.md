---
description: All endpoints in this section require authentication
---

# Trading

## Get trades

#### Description

This endpoint retrieves your executed trades with its price, volume, and direction. Trades are sorted in reverse creation order.

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/market/trades
```

#### Request Parameters

| Name | Located In | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| market | query |  |  | string |
| limit | query | Limit the number of returned trades. Default to 100. |  | integer |
| page | query | Specify the page of paginated results. |  | integer |
| time\_from | query | An integer represents the seconds elapsed since Unix epoch.If set, only trades executed after the time will be returned. |  | integer |
| time\_to | query | An integer represents the seconds elapsed since Unix epoch.If set, only trades executed before the time will be returned. |  | integer |
| order\_by | query | If set, returned trades will be sorted in specific order, default to 'desc'. |  | string |

#### Response Content

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get your executed trades. Trades are sorted in reverse creation order. | [Trade](trading.md#trades) |

## Cancel orders

#### Description

Cancel all my orders.

#### HttpRequest

```text
POST https://api.nebulaecn.com/v1/market/orders/cancel
```

#### Request Parameters

| Name | Located In | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| market | formData |  | No | string |
| side | formData | If present, only sell orders \(asks\) or buy orders \(bids\) will be cancelled. | No | string |

#### Response Content

| Code | Description | Schema |
| :--- | :--- | :--- |
| 201 | Get your executed trades. Trades are sorted in reverse creation order. | [Trade](trading.md#trades) |

## Cancel an order

#### Description

Cancel an order.

#### HttpRequest

```text
POST https://api.nebulaecn.com/v1/market/orders/{id}/cancel
```

#### Request Parameters

| Name | Located In | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| id | path |  | Yes | string |

#### Response Content

| Code | Description |
| :--- | :--- |
| 201 | Cancel an order. |

## Create an order

#### Description

Create a Sell/Buy order.

#### HttpRequest

```text
POST https://api.nebulaecn.com/v1/market/orders
```

#### Request Parameters

| Name | Located In | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| market | formData |  | Yes | string |
| side | formData |  | Yes | string |
| volume | formData |  | Yes | double |
| ord\_type | formData |  | No | string |
| price | formData |  | Yes | double |

#### Response Content

| Code | Description | Schema |
| :--- | :--- | :--- |
| 201 | Create a Sell/Buy order. | Order |

## Get orders

#### Description

Get your orders, result is paginated.

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/market/orders
```

#### Request Parameters

| Name | Located In | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| market | query |  | No | string |
| base\_unit | query |  | No | string |
| quote\_unit | query |  | No | string |
| state | query | Filter order by state. | No | string |
| limit | query | Limit the number of returned orders, default to 100. | No | integer |
| page | query | Specify the page of paginated results. | No | integer |
| order\_by | query | If set, returned orders will be sorted in specific order, default to "desc". | No | string |
| ord\_type | query | Filter order by ord\_type. | No | string |
| type | query | Filter order by type. | No | string |
| time\_from | query | An integer represents the seconds elapsed since Unix epoch.If set, only orders created after the time will be returned. | No | integer |
| time\_to | query | An integer represents the seconds elapsed since Unix epoch.If set, only orders created before the time will be returned. | No | integer |

#### Response Content

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get your orders, result is paginated. | Order |



## Get specified order

#### Description

Get information of specified order.

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/market/orders/{id}
```

#### Request Parameters

| Name | Located In | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| id | path |  | Yes | string |

#### Response Content

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get information of specified order. | **Order** |

## Models

### WithdrawLimit

Returns withdraw limits table as paginated collection.

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | integer | Unique withdraw limit table identifier in database. | No |
| group | string | Member group for define withdraw limits. | No |
| kyc\_level | string | KYC level for define withdraw limits. | No |
| limit\_24\_hour | double | 24 hours withdraw limit. | No |
| limit\_1\_month | double | 1 month withdraw limit. | No |
| created\_at | string | Withdraw limit table created time in iso8601 format. | No |
| updated\_at | string | Withdraw limit table updated time in iso8601 format. | No |

### TradingFee

Returns trading\_fees table as paginated collection

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | integer | Unique trading fee table identifier in database. | No |
| group | string | Member group for define maker/taker fee. | No |
| market\_id | string | Market id for define maker/taker fee. | No |
| maker | double | Market maker fee. | No |
| taker | double | Market taker fee. | No |
| created\_at | string | Trading fee table created time in iso8601 format. | No |
| updated\_at | string | Trading fee table updated time in iso8601 format. | No |

### **Ticker**

Get ticker of all markets \(For response doc see /:market/tickers/ response\).

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| at | integer | Timestamp of ticker | No |
| ticker | **TickerEntry** | Ticker entry for specified time | No |

### **TickerEntry**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| low | double | The lowest trade price during last 24 hours \(0.0 if no trades executed during last 24 hours\) | No |
| high | double | The highest trade price during last 24 hours \(0.0 if no trades executed during last 24 hours\) | No |
| open | double | Price of the first trade executed 24 hours ago or less | No |
| last | double | The last executed trade price | No |
| volume | double | Total volume of trades executed during last 24 hours | No |
| amount | double | Total amount of trades executed during last 24 hours | No |
| vol | double | Alias to volume | No |
| avg\_price | double | Average price more precisely VWAP is calculated by adding up the total traded for every transaction\(price multiplied by the number of shares traded\) and then dividing by the total shares traded | No |
| price\_change\_percent | string | Price change in the next format +3.19%.Price change is calculated using next formula \(last - open\) / open \* 100% | No |
| at | integer | Timestamp of ticker | No |

### **Trade**

Get your executed trades. Trades are sorted in reverse creation order.

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | Trade ID. | No |
| price | double | Trade price. | No |
| amount | double | Trade amount. | No |
| total | double | Trade total \(Amount \* Price\). | No |
| fee\_currency | double | Currency user's fees were charged in. | No |
| fee | double | Percentage of fee user was charged for performed trade. | No |
| fee\_amount | double | Amount of fee user was charged for performed trade. | No |
| market | string | Trade market id. | No |
| created\_at | string | Trade create time in iso8601 format. | No |
| taker\_type | string | Trade taker order type \(sell or buy\). | No |
| side | string | Trade side. | No |
| order\_id | integer | Order id. | No |

### **OrderBook**

Get the order book of specified market.

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| asks | \[ **Order** \] | Asks in orderbook | No |
| bids | \[ **Order** \] | Bids in orderbook | No |

### **Order**

Get your orders, result is paginated.

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | integer | Unique order id. | No |
| uuid | string | Unique order UUID. | No |
| side | string | Either 'sell' or 'buy'. | No |
| ord\_type | string | Type of order, either 'limit' or 'market'. | No |
| price | double | Price for each unit. e.g.If you want to sell/buy 1 btc at 3000 usd, the price is '3000.0' | No |
| avg\_price | double | Average execution price, average of price in trades. | No |
| state | string | One of 'wait', 'done', or 'cancel'.An order in 'wait' is an active order, waiting fulfillment; a 'done' order is an order fulfilled;'cancel' means the order has been canceled. | No |
| market | string | The market in which the order is placed, e.g. 'btcusd'.All available markets can be found at /api/v2/markets. | No |
| created\_at | string | Order create time in iso8601 format. | No |
| updated\_at | string | Order updated time in iso8601 format. | No |
| origin\_volume | double | The amount user want to sell/buy.An order could be partially executed, e.g. an order sell 5 btc can be matched with a buy 3 btc order, left 2 btc to be sold; in this case the order's volume would be '5.0',its remaining\_volume would be '2.0', its executed volume is '3.0'. | No |
| remaining\_volume | double | The remaining volume, see 'volume'. | No |
| executed\_volume | double | The executed volume, see 'volume'. | No |
| maker\_fee | double | Fee for maker. | No |
| taker\_fee | double | Fee for taker. | No |
| trades\_count | integer | Count of trades. | No |
| trades | \[ [Trade](trading.md#trade) \] | Trades with this order. | No |

### **Market**

Get all available markets.

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | Unique market id. It's always in the form of xxxyyy, where xxx is the base currency code, yyy is the quotecurrency code, e.g. 'btcusd'. All available markets canbe found at /api/v2/markets. | No |
| name | string | Market name. | No |
| base\_unit | string | Market Base unit. | No |
| quote\_unit | string | Market Quote unit. | No |
| min\_price | double | Minimum order price. | No |
| max\_price | double | Maximum order price. | No |
| min\_amount | double | Minimum order amount. | No |
| amount\_precision | double | Precision for order amount. | No |
| price\_precision | double | Precision for order price. | No |
| state | string | Market state defines if user can see/trade on current market. | No |

### **Currency**

Get a currency.

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | Currency code. _Example:_ `"btc"` | No |
| name | string | Currency name _Example:_ `"Bitcoin"` | No |
| description | string | Currency description _Example:_ `"btc"` | No |
| homepage | string | Currency homepage _Example:_ `"btc"` | No |
| price | string | Currency current price | No |
| explorer\_transaction | string | Currency transaction exprorer url template _Example:_ `"https://testnet.blockchain.info/tx/"` | No |
| explorer\_address | string | Currency address exprorer url template _Example:_ `"https://testnet.blockchain.info/address/"` | No |
| type | string | Currency type _Example:_ `"coin"` | No |
| deposit\_enabled | string | Currency deposit possibility status \(true/false\). | No |
| withdrawal\_enabled | string | Currency withdrawal possibility status \(true/false\). | No |
| deposit\_fee | string | Currency deposit fee _Example:_ `"0.0"` | No |
| min\_deposit\_amount | string | Minimal deposit amount _Example:_ `"0.0000356"` | No |
| withdraw\_fee | string | Currency withdraw fee _Example:_ `"0.0"` | No |
| min\_withdraw\_amount | string | Minimal withdraw amount _Example:_ `"0.0"` | No |
| withdraw\_limit\_24h | string | Currency 24h withdraw limit _Example:_ `"0.1"` | No |
| withdraw\_limit\_72h | string | Currency 72h withdraw limit _Example:_ `"0.2"` | No |
| base\_factor | string | Currency base factor _Example:_ `100000000` | No |
| precision | string | Currency precision _Example:_ `8` | No |
| position | string | Position used for defining currencies order _Example:_ `8` | No |
| icon\_url | string | Currency icon _Example:_ `"https://upload.wikimedia.org/wikipedia/commons/0/05/Ethereum_logo_2014.svg"` | No |
| min\_confirmations | string | Number of confirmations required for confirming deposit or withdrawal | No |

### **Withdraw**

List your withdraws as paginated collection.

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | integer | The withdrawal id. | No |
| currency | string | The currency code. | No |
| type | string | The withdrawal type | No |
| amount | string | The withdrawal amount | No |
| fee | double | The exchange fee. | No |
| blockchain\_txid | string | The withdrawal transaction id. | No |
| rid | string | The beneficiary ID or wallet address on the Blockchain. | No |
| state | string | The withdrawal state. | No |
| confirmations | integer | Number of confirmations. | No |
| note | string | Withdraw note. | No |
| transfer\_type | string | Withdraw transfer type | No |
| created\_at | string | The datetimes for the withdrawal. | No |
| updated\_at | string | The datetimes for the withdrawal. | No |
| done\_at | string | The datetime when withdraw was completed | No |

### **Beneficiary**

Get list of user beneficiaries

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | integer | Beneficiary Identifier in Database | No |
| currency | string | Beneficiary currency code. | No |
| uid | string | Beneficiary owner | No |
| name | string | Human rememberable name which refer beneficiary. | No |
| description | string | Human rememberable description of beneficiary. | No |
| data | json | Bank Account details for fiat Beneficiary in JSON format.For crypto it's blockchain address. | No |
| state | string | Defines either beneficiary active - user can use it to withdraw moneyor pending - requires beneficiary activation with pin. | No |
| sent\_at | string | Time when last pin was sent | No |

### **Deposit**

Get your deposits history.

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | integer | Unique deposit id. | No |
| currency | string | Deposit currency id. | No |
| amount | double | Deposit amount. | No |
| fee | double | Deposit fee. | No |
| txid | string | Deposit transaction id. | No |
| confirmations | integer | Number of deposit confirmations. | No |
| state | string | Deposit state. | No |
| transfer\_type | string | Deposit transfer type | No |
| created\_at | string | The datetime when deposit was created. | No |
| completed\_at | string | The datetime when deposit was completed.. | No |
| tid | string | The shared transaction ID | No |

### **Account**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| currency | string | Currency code. | No |
| balance | double | Account balance. | No |
| locked | double | Account locked funds. | No |

### **Transactions**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| address | string | Recipient address of transaction. | No |
| currency | string | Transaction currency id. | No |
| amount | double | Transaction amount. | No |
| fee | double | Transaction fee. | No |
| txid | string | Transaction id. | No |
| state | string | Transaction state. | No |
| note | string | Withdraw note. | No |
| confirmations | integer | Number of confirmations. | No |
| created\_at | string | Transaction created time in iso8601 format. | No |
| updated\_at | string | Transaction updated time in iso8601 format. | No |
| type | string | Type of transaction | No |

### **Member**

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| uid | string | Member UID. | No |
| email | string | Member email. | No |
| accounts | \[ [Account](account.md) \] | Member accounts. | No |







