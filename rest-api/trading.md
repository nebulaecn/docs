---
description: All endpoints in this section require authentication
---

# Trading

### Order types

`Market` — an order that the Client makes through Order Book to buy or sell Symbol immediately at the best price currently available. The Price field should be missing if the order type is Market. 



`Limit` — an order placed by Client through Order Book to buy or sell an amount of current trading pair at a specified price or better. Both quantity and price fields should be filled if the order type is Limit. Because the limit order is not a market order, it may not be executed if the price set by the Client cannot be met during the period of time, in which the order is left open.  After being placed, Limit orders can be:

1. Fully executed immediately
2. Not executed immediately, and left open to be fully of partially executed, or cancelled
3. Partially executed immediately and have open outstanding amount waiting to be fully or partially executed, or cancelled.
4. Fill-or-Kill - cancelled completely if not executed immediately.



`Stop`— a stop order is used to trigger a market sell when the market drops to your trigger price or used to trigger a market buy if the market rises to your trigger price. This is often used as a stop-loss order if the market is moving in an unfavourable direction. Stop orders will fully execute as a market order once the trigger price is reached.

Example: If the current market price is 50 000, the trader in a long position might want to sell if the price drops to 49 900 to avoid further losses. A stop sell at 49 900 will be used in this case.

Example: If the current market price is 50 000, the trader in a short position might want to buy if the price reaches 50 100 to avoid further losses. A stop buy at 50 100 will be used in this case.



`Stop-Limit`— a stop-limit order triggers a limit order. With a stop-limit, the trader sets a stop price at which the order is triggered and a limit price at which the order may be filled. Once the stop of a stop-limit order is triggered, the limit order is automatically placed. 

Example: If a trader would like to buy once the market price reaches 50 000, but not pay more than 50 100, then a stop price of 50 000 and limit price of 51 000 will be specified at the same time using a stop-limit order. If the market price reaches 50 000, the order is triggered and will match the best available asks up to 50 100. If the market price moves to 50 101 or above, then the order may go partially unfilled due to the limit price. 

## Get trades

#### Description

This endpoint retrieves your executed trades with its price, volume, and direction. Trades are sorted in reverse creation order.

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/backend/market/trades
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

## Cancel an order

#### Description

Submit cancel request, cancels order from orderbook.

#### HttpRequest

```text
POST https://trade.nebulaecn.com/api/v2/trading/market/orders/cancel/{id|uuid}
```

**Responses**

| code | description |
| :--- | :--- |
| 201 | Your cancel request was submitted and awaits for processing |
| 422 | Invalid request, make sure every mandatory fields are present |
| 500 | Internal Server Error |

## Cancel orders

#### Description

Submit cancel request, cancels all your orders from orderbook.

#### HttpRequest

```text
POST https://trade.nebulaecn.com/api/v2/trading/market/orders/cancel
```

**Request Parameters \(JSON\)**

| param | type | desc |
| :--- | :--- | :--- |
| market | string | market id |
| side | string | buy or sell |

**Responses**

| code | description |
| :--- | :--- |
| 200 | Your cancel request was submitted and awaits for processing |
| 422 | Invalid request, make sure every mandatory fields are present |
| 500 | Internal Server Error |

#### Example

```text
curl -X POST https://trade.nebulaecn.com/api/v2/trading/market/orders/cancel/1 \
-H 'Content-Type: application/json'
```

```text
curl -X POST https://trade.nebulaecn.com/api/v2/trading/market/orders/cancel/b47d2527-5a0c-11ea-822c-1831bf9834b0 \
-H 'Content-Type: application/json'
```

## Create an order

#### Description

Submit a new order to API. Notice that while the response from the server is ok, the order can still be rejected by the matching engine. You should wait the confirmation from the websocket to be sure that your order has been added to the orderbook.

#### HttpRequest

```text
POST https://trade.nebulaecn.com/api/v2/trading/market/orders
```

**Request Parameters \(JSON\)**

| param | type | desc |
| :--- | :--- | :--- |
| market | string | market id |
| side | string | buy or sell |
| amount | decimal | valid decimal value |
| type | string | market, limit, post\_only |
| price | decimal | valid decimal value |

#### Response Content

| Code | Description |
| :--- | :--- |
| 201 | Your order was submitted and awaits for processing |
| 400 | Bad request, make sure the JSON syntax of your request is correct |
| 422 | Invalid request, make sure every mandatory fields are present |
| 500 | Internal Server Error |

#### Example

```text
curl -X POST https://trade.nebulaecn.com/api/v2/trading/market/orders \
  --data '{"market":"btcusd", "amount":"1.0","type":"limit", "side":"sell", "price":"1"}' \
  -H 'Content-Type: application/json'
{"uuid":"b436163d-5c73-11ea-be71-1831bf9834b0","side":"sell","type":"limit","market_id":"btcusd","volume":"1","price":"1","state":"pending","created_at":1583146260
```

## Create a list of orders

#### Description

Bulk api to create a list of orders in one request. The default limit is set to 100 orders for one request, this might be configured by support.

#### HttpRequest

```text
POST https://trade.nebulaecn.com/api/v2/trading/market/bulk/orders
```

**Request Parameters \(JSON\)**

| param | type | desc |
| :--- | :--- | :--- |
| \[\] | \[\]object | array of order params \(refer to create order params\) |

**Responses**

| code | description |
| :--- | :--- |
| 201 | Your order was submitted and awaits for processing |
| 422 | Invalid request, make sure every mandatory fields are present |
| 413 | Request entity too large. Your request contains too much orders. |
| 500 | Internal Server Error |

#### Example

```text
curl -X POST https://trade.nebulaecn.com/api/v2/trading/market/bulk/orders \
  --data '[{"market":"btcusd", "amount":"1.0","type":"limit", "side":"sell", "price":"1"}, {"market":"btcusd", "amount":"1.0","type":"limit", "side":"sell", "price":"1"}]' \
-H 'Content-Type: application/json'
[{"uuid":"b76aef45-5c73-11ea-be71-1831bf9834b0","side":"sell","type":"limit","market_id":"btcusd","volume":"1","price":"1","state":"pending","created_at":1583146265},{"uuid":"b76afa8b-5c73-11ea-be71-1831bf9834b0","side":"sell","type":"limit","market_id":"btcusd","volume":"1","price":"1","state":"pending","created_at":1583146265}]
```

## Cancel orders by UUID

#### Description

Bulk api to cancel orders.

#### HttpRequest

```text
DELETE https://trade.nebulaecn.com/api/v2/trading/market/bulk/orders
```

**Request Parameters \(JSON\)**

| param | type | desc |
| :--- | :--- | :--- |
| \[\] | \[\]string | Order UUIDs to cancel |

**Responses**

| code | description |
| :--- | :--- |
| 200 | Your cancel requests were submitted and await for processing |
| 422 | Invalid request, make sure every mandatory fields are present |
| 413 | Request entity too large. Your request contains too much orders. |
| 500 | Internal Server Error |

#### Example

```text
curl -X DELETE https://trade.nebulaecn.com/api/v2/trading/market/bulk/orders \
 --data '["580d891d-5c8b-11ea-a012-1831bf9834b0", "580d891d-5c8b-11ea-a012-1831bf9834b0"]' \
-H 'Content-Type: application/json'
"orders.cancel.accepted"
```

## Cancel orders by ID

#### Description

Bulk api to cancel orders.

#### HttpRequest

```text
DELETE https://trade.nebulaecn.com/api/v2/trading/market/bulk/orders_by_id
```

**Request Parameters \(JSON\)**

| param | type | desc |
| :--- | :--- | :--- |
| \[\] | \[\]integer | Array of ids to cancel |

**Responses**

| code | description |
| :--- | :--- |
| 200 | Your cancel requests were submitted and await for processing |
| 422 | Invalid request, make sure every mandatory fields are present |
| 413 | Request entity too large. Your request contains too much orders. |
| 500 | Internal Server Error |

#### Example

```text
curl -X DELETE https://trade.nebulaecn.com/api/v2/trading/market/bulk/orders_by_id \
--data '[1, 2, 3, 4]' \
-H 'Content-Type: application/json'
"orders.cancel.accepted"
```

## Get orders

#### Description

Get your orders, result is paginated.

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/backend/market/orders
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
GET https://trade.nebulaecn.com/api/v2/backend/market/orders/{id}
```

#### Request Parameters

| Name | Located In | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| id | path |  | Yes | string |

#### Response Content

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get information of specified order. | **Order** |



