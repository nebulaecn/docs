# Market Data



### Get member levels

**Description**

Returns hash of minimum levels and the privileges they provide.

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/public/member-levels
```

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Returns hash of minimum levels and the privileges they provide. |

### Get **specified** ticker

**Description**

Get ticker of specific market.

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/public/markets/{market}/tickers
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| market | path |  | Yes | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get ticker of specific market. | Ticker |

### **Get tickers**

**Description**

Get ticker of all markets \(For response doc see /:market/tickers/ response\).

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/public/markets/tickers
```

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get ticker of all markets \(For response doc see /:market/tickers/ response\). | Ticker |

### Get OHLC

**Description**

Get OHLC\(k line\) of specific market.

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/public/markets/{market}/k-line
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| market | path |  | Yes | string |
| period | query | Time period of K line, default to 1. You can choose between 1, 5, 15, 30, 60, 120, 240, 360, 720, 1440, 4320, 10080 | No | integer |
| time\_from | query | An integer represents the seconds elapsed since Unix epoch. If set, only k-line data after that time will be returned. | No | integer |
| time\_to | query | An integer represents the seconds elapsed since Unix epoch. If set, only k-line data till that time will be returned. | No | integer |
| limit | query | Limit the number of returned data points default to 30. Ignored if time\_from and time\_to are given. | No | integer |

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get OHLC\(k line\) of specific market. |

### Get depth of specified market

**Description**

Get depth of specified market. Both asks and bids are sorted from highest price to lowest.

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/public/markets/{market}/depth
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| market | path |  | Yes | string |
| limit | query | Limit the number of returned price levels. Default to 300. | No | integer |

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get depth or specified market. Both asks and bids are sorted from highest price to lowest. |

### Get recent trades

**Description**

Get recent trades on market, each trade is included only once. Trades are sorted in reverse creation order.

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/public/markets/{market}/trades
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| market | path |  | Yes | string |
| limit | query | Limit the number of returned trades. Default to 100. | No | integer |
| timestamp | query | An integer represents the seconds elapsed since Unix epoch.If set, only trades executed before the time will be returned. | No | integer |
| order\_by | query | If set, returned trades will be sorted in specific order, default to 'desc'. | No | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get recent trades on market, each trade is included only once. Trades are sorted in reverse creation order. | \[ Trade \] |

### Get the order book

**Description**

Get the order book of specified market.

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/public/markets/{market}/order-book
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| market | path |  | Yes | string |
| asks\_limit | query | Limit the number of returned sell orders. Default to 20. | No | integer |
| bids\_limit | query | Limit the number of returned buy orders. Default to 20. | No | integer |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get the order book of specified market. | \[ OrderBook \] |

### Get all markets

**Description**

Get all available markets.

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/public/markets
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| limit | query | Limit the number of returned paginations. Defaults to 100. | No | integer |
| page | query | Specify the page of paginated results. | No | integer |
| ordering | query | If set, returned values will be sorted in specific order, defaults to 'asc'. | No | string |
| order\_by | query | Name of the field, which result will be ordered by. | No | string |
| base\_unit | query | Strict filter for base unit | No | string |
| quote\_unit | query | Strict filter for quote unit | No | string |
| search | query |  | No | json |
| search\[base\_code\] | query | Search base currency code using LIKE | No | string |
| search\[quote\_code\] | query | Search qoute currency code using LIKE | No | string |
| search\[base\_name\] | query | Search base currency name using LIKE | No | string |
| search\[quote\_name\] | query | Search quote currency name using LIKE | No | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get all available markets. | \[ Market \] |

### Get currencies

**Description**

Get list of currencies

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/public/currencies
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| limit | query | Limit the number of returned paginations. Defaults to 100. | No | integer |
| page | query | Specify the page of paginated results. | No | integer |
| type | query | Currency type | No | string |
| search | query |  | No | json |
| search\[code\] | query | Search by currency code using SQL LIKE | No | string |
| search\[name\] | query | Search by currency name using SQL LIKE | No | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get list of currencies | \[ Currency \] |

### Get a currency

**Description**

Get a currency

#### HttpRequest

```text
GET https://api.nebulaecn.com/v1/public/currencies/{id}
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| id | path | Currency code. | Yes | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get a currency | Currency |







