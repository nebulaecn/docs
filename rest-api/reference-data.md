# Reference Data

####  <a id="public-withdraw_limits"></a>

### Get withdraw limits

**Description**

Returns withdrawal limits table as paginated collection

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/backend/public/withdraw_limits
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| group | query | Member group for define withdraw limits. | No | string |
| kyc\_level | query | KYC level for define withdraw limits. | No | string |
| limit | query | Limit the number of returned paginations. Defaults to 100. | No | integer |
| page | query | Specify the page of paginated results. | No | integer |
| ordering | query | If set, returned values will be sorted in specific order, defaults to 'asc'. | No | string |
| order\_by | query | Name of the field, which result will be ordered by. | No | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Returns withdraw limits table as paginated collection | \[ WithdrawLimit \] |

### Get trading fees

**Description**

Returns trading\_fees table as paginated collection

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/backend/public/trading_fees
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| group | query | Member group for define maker/taker fee. | No | string |
| market\_id | query | Market id for define maker/taker fee. | No | string |
| limit | query | Limit the number of returned paginations. Defaults to 100. | No | integer |
| page | query | Specify the page of paginated results. | No | integer |
| ordering | query | If set, returned values will be sorted in specific order, defaults to 'asc'. | No | string |
| order\_by | query | Name of the field, which result will be ordered by. | No | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Returns trading\_fees table as paginated collection | \[ TradingFee \] |

### Get app readiness status

**Description**

Get application readiness status

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/backend/public/health/ready
```

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get application readiness status |



### Get server time

**Description**

Get server current time, in seconds since Unix epoch.

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/backend/public/timestamp
```

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get server current time, in seconds since Unix epoch. |

