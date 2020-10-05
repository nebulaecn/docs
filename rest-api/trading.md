---
description: All endpoints in this section require authentication
---

# Trading

### Order types

`Market` — an order that the Client makes through Order Book to buy or sell Symbol immediately at the best price currently available. The Price field should be missing if the order type is Market. 

`Limit` — an order placed by Client through Order Book to buy or sell an amount of current trading pair at a specified price or better. Both quantity and price fields should be filled if the order type is Limit.  Because the limit order is not a market order, it may not be executed if the price set by the Client cannot be met during the period of time, in which the order is left open.  After being placed, Limit orders can be:

1. Fully executed immediately
2. Not executed immediately, and left open to be fully of partially executed, or cancelled
3. Partially executed immediately and have open outstanding amount waiting to be fully or partially executed, or cancelled.
4. Fill-or-Kill - cancelled completely if not executed immediately.

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



