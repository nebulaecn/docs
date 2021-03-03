# WebSocket API

## API

There are two types of channels: \* Public: accessible by anyone \* Private: accessible only by given member

GET request parameters:

| Field | Description | Multiple allowed |
| :--- | :--- | :--- |
| `stream` | List of streams to be subscribed on | Yes |

List of supported public streams: \* [`<market>.ob-inc`](https://www.openware.com/sdk/docs/peatio/api/websocket-api.html#order-book) market order-book update \* [`<market>.trades` ](https://www.openware.com/sdk/docs/peatio/api/websocket-api.html#trades)\* [`<market>.kline-PERIOD` ](https://www.openware.com/sdk/docs/peatio/api/websocket-api.html#kline-point)\(available periods are "1m", "5m", "15m", "30m", "1h", "2h", "4h", "6h", "12h", "1d", "3d", "1w"\) \* [`global.tickers`](https://www.openware.com/sdk/docs/peatio/api/websocket-api.html#tickers)

List of supported private streams \(requires authentication\): \* [`order`](https://www.openware.com/sdk/docs/peatio/api/websocket-api.html#order) \* [`trade`](https://www.openware.com/sdk/docs/peatio/api/websocket-api.html#trade)

You can find a format of these events below in the doc.

### Authentication <a id="subscribe-to-streams"></a>

Authentication happens on websocket message with following JSON structure.

```text
{
  "jwt": "Bearer <Token>"
}
```

If authentication was done, server will respond successfully

```text
{
  "success": {
    "message": "Authenticated."
  }
}
```

Otherwise server will return an error

```text
{
  "error": {
    "message": "Authentication failed."
  }
}
```

If authentication JWT token has invalid type, server return an error

```text
{
  "error": {
    "message": "Token type is not provided or invalid."
  }
}
```

If other error occurred during the message handling server throws an error

```text
{
  "error": {
    "message": "Error while handling message."
  }
}
```

**Note:** Websocket API supports authentication only Bearer type of JWT token.

**Example** of authentication message:

```text
{
  "jwt": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9.TJVA95OrM7E2cBab30RMHrHDcEfxjoYZgeFONFh7HgQ"
}
```

### Streams subscription <a id="subscribe-to-streams"></a>

#### **Using parameters**

You can specify streams to subscribe to by passing the `stream` GET parameter in the connection URL. The parameter can be specified multiple times for subscribing to multiple streams.

example:

```text
wss://trade.nebulaecn.com/api/v2/stream/public/?stream=global.tickers&stream=ethusd.trades
```

This will subscribe you to _tickers_ and _trades_ events from _ethusd_ market once the connection is established.

#### **Subscribe and unsubscribe events**

You can manage the connection subscriptions by send the following events after the connection is established:

Subscribe event will subscribe you to the list of streams provided:

```text
{"event":"subscribe","streams":["ethusd.trades","ethusd.ob-inc"]}
```

The server confirms the subscription with the following message and provides the new list of your current subscriptions:

```text
{"success":{"message":"subscribed","streams":["global.tickers","ethusd.trades","ethusd.ob-inc"]}}
```

Unsubscribe event will unsubscribe you to the list of streams provided:

```text
{"event":"unsubscribe","streams":["ethusd.trades","ethusd.ob-inc"]}
```

The server confirms the unsubscription with the following message and provides the new list of your current subscriptions:

```text
{"success":{"message":"unsubscribed","streams":["global.tickers","ethusd.kline-15m"]}}
```

## Public streams

### **Order-Book**

This stream sends a snapshot of the order-book at the subscription time, then it sends increments. Volumes information in increments replace the previous values. If the volume is zero the price point should be removed from the order-book.

Register to stream `<market>.ob-inc` to receive snapshot and increments messages.

Example of order-book snapshot:

```text
{
    "eurusd.ob-snap":{
        "asks":[
            ["15.0","21.7068"],
            ["20.0","100.2068"],
            ["20.5","30.2068"],
            ["30.0","21.2068"]
        ],
        "bids":[
            ["10.95","21.7068"],
            ["10.90","65.2068"],
            ["10.85","55.2068"],
            ["10.70","30.2068"]
        ]
    }
}
```

Example of order-book increment message:

```text
 {
     "eurusd.ob-inc":{
         "asks":[
             ["15.0","22.1257"]
         ]
     }
 }
```

### **Trades**

Here is structure of `<market>.trades` event expose as array with trades:

| Field | Description |
| :--- | :--- |
| `tid` | Unique trade tid. |
| `taker_type` | Taker type of trade, either `buy` or `sell`. |
| `price` | Price for the trade. |
| `amount` | The amount of trade. |
| `created_at` | Trade create time. |

**Kline point**

Kline point as array of numbers:

1. Timestamp.
2. Open price.
3. Max price.
4. Min price.
5. Last price.
6. Period volume

Example:

```text
[1537370580, 0.0839, 0.0921, 0.0781, 0.0845, 0.5895]
```

### **Tickers**

Here is structure of `global.tickers` event expose as array with all markets pairs:

| Field | Description |
| :--- | :--- |
| `at` | Date of current ticker. |
| `name` | Market pair name. |
| `base_unit` | Base currency. |
| `quote_unit` | Quote currency. |
| `low` | Lowest price in 24 hours. |
| `high` | Highest price in 24 hours. |
| `last` | Last trade price. |
| `open` | Last trade from last timestamp. |
| `close` | Last trade price. |
| `volume` | Volume in 24 hours. |
| `sell` | Best price per unit. |
| `buy` | Best price per unit. |
| `avg_price` | Average price for last 24 hours. |
| `price_change_percent` | Average price change in percent. |

## Private streams

### **Order**

Here is structure of `Order` event:

| Field | Description |
| :--- | :--- |
| `id` | Unique order id. |
| `market` | The market in which the order is placed. \(In backend `market_id`\) |
| `order_type` | Order type, either `limit` or `market`. |
| `price` | Order price. |
| `avg_price` | Order average price. |
| `state` | One of `wait`, `done`, `reject` or `cancel`. |
| `origin_volume` | The amount user want to sell/buy. |
| `remaining_volume` | Remaining amount user want to sell/buy. |
| `executed_volume` | Executed amount for current order. |
| `created_at` | Order create time. |
| `updated_at` | Order create time. |
| `trades_count` | Trades with this order. |
| `kind` | Type of order, either `bid` or `ask`. \(Deprecated\) |
| `at` | Order create time. \(Deprecated\) \(In backend`created_at`\) |

### **Trade**

Here is structure of `Trade` event:

| Field | Description |
| :--- | :--- |
| `id` | Unique trade identifier. |
| `price` | Price for each unit. |
| `amount` | The amount of trade. |
| `total` | The total of trade \(volume \* price\). |
| `market` | The market in which the trade is placed. \(In backend market\_id\) |
| `side` | Type of order in trade that related to current user `sell` or `buy`. |
| `taker_type` | Order side of the taker for the trade, either `buy` or `sell`. |
| `created_at` | Trade create time. |
| `order_id` | User order identifier in trade. |



Websocket API is mounted at `/api/v2/trading`. If you pass a JWT header, your connection will be authenticated, otherwise it will be considered anonymous.

### Subscribe to streams <a id="subscribe-to-streams"></a>

Example

```text
[1, 2, "subscribe", ["private", ["order", "trade", "balances"]]]
```

### Get your open orders <a id="get-your-open-orders"></a>

```text
[1, 2, "list_orders", ["btcusd"]]
```

```text
[
  2,
  2,
  "list_orders",
  [
    [
      "btcusd",
      97,
      "6dcc2c8e-c295-11ea-b7ad-1831bf9834b0",
      "sell",
      "w",
      "l",
      "9120",
      "0",
      "0.25",
      "0.25",
      "0",
      0,
      1594386563
    ]
  ]
]
```

#### Order response schema <a id="order-response-schema"></a>

| Field | Example |
| :--- | :--- |
| Market | "btcusd" |
| ID | 97 |
| UUID | "6dcc2c8e-c295-11ea-b7ad-1831bf9834b0" |
| Side | "sell" |
| State | "w" |
| Type | "l" |
| Price | "9120" |
| Avg. Price | "0" |
| Volume | "0.25" |
| Orig. Volume | "0.25" |
| Executed Volume | "0" |
| Trades Count | 0 |
| Timestamp | 1594386563 |

### Get order by uuids <a id="get-order-by-uuids"></a>

```text
[
  1,
  3,
  "get_orders",
  [
    "6dcc2c8e-c295-11ea-b7ad-1831bf9834b0",
    "4fec493d-c2a2-11ea-b670-1831bf9834b0"
  ]
]
```

```text
[
  2,
  3,
  "get_orders",
  [
    [
      "btcusd",
      97,
      "6dcc2c8e-c295-11ea-b7ad-1831bf9834b0",
      "sell",
      "w",
      "l",
      "9120",
      "0",
      "0.25",
      "0.25",
      "0",
      0,
      1594386563
    ],
    [
      "btcusd",
      98,
      "4fec493d-c2a2-11ea-b670-1831bf9834b0",
      "sell",
      "c",
      "m",
      "0",
      "0",
      "0.25",
      "0.25",
      "0",
      0,
      1594392096
    ]
  ]
]
```

### Get order trades <a id="get-order-trades"></a>

```text
[1, 42, "get_order_trades", ["ab224fef-c2a2-11ea-b670-1831bf9834b0"]]
```

```text
[
  2,
  42,
  "get_order_trades",
  [
    [
      "btcusd",
      33,
      "9120",
      "0.25",
      "2280",
      100,
      "ab224fef-c2a2-11ea-b670-1831bf9834b0",
      "buy",
      "buy",
      "0.0005",
      "btc",
      1594392250
    ]
  ]
]
```

#### Trade response schema <a id="trade-response-schema"></a>

| Field | Example |
| :--- | :--- |
| Market | "btcusd" |
| ID | 33 |
| Price | "9120" |
| Amount | "0.25" |
| Total | "2280" |
| OrderID | 100 |
| OrderUUID | "ab224fef-c2a2-11ea-b670-1831bf9834b0" |
| OrderSide | "buy" |
| TakerSide | "buy" |
| Fee | "0.0005" |
| Fee Unit | "btc" |
| Timestamp | 1594392250 |

## 

