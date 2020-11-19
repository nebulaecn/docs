# Account

### Get pnl into one currency.

**Description**

Get assets pnl calculated into one currency

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/stats/pnl
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| pnl\_currency | query | Currency code in which the PnL is calculated | No | string |

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get assets pnl calculated into one currency |

### **Get transaction history**

**Description**

Get your transactions history.

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/transactions
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| currency | query | Currency code | No | string |
| order\_by | query | Sorting order | No | string |
| time\_from | query | An integer represents the seconds elapsed since Unix epoch. | No | integer |
| time\_to | query | An integer represents the seconds elapsed since Unix epoch. | No | integer |
| deposit\_state | query | Filter deposits by states. | No | string |
| withdraw\_state | query | Filter withdraws by states. | No | string |
| txid | query | Transaction id. | No | string |
| limit | query | Limit the number of returned transactions. Default to 100. | No | integer |
| page | query | Specify the page of paginated results. | No | integer |

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Get your transactions history. |

### Create withdrawal

**Description**

Creates new withdrawal to active beneficiary.

#### HttpRequest

```text
POST https://trade.nebulaecn.com/api/v2/auth/account/withdraws
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| otp | formData | OTP to perform action | Yes | integer |
| beneficiary\_id | formData | ID of Active Beneficiary belonging to user. | Yes | integer |
| currency | formData | The currency code. | Yes | string |
| amount | formData | The amount to withdraw. | Yes | double |
| note | formData | Optional metadata to be applied to the transaction. Used to tag transactions with memorable comments. | No | string |

**Responses**

| Code | Description |
| :--- | :--- |
| 201 | Creates new withdrawal to active beneficiary. |

### **Get** withdrawals

**Description**

List your withdraws as paginated collection.

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/withdraws
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| currency | query | Currency code. | No | string |
| limit | query | Number of withdraws per page \(defaults to 100, maximum is 100\). | No | integer |
| state | query | Filter withdrawals by states. | No | string |
| rid | query | Wallet address on the Blockchain. | No | string |
| page | query | Page number \(defaults to 1\). | No | integer |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | List your withdraws as paginated collection. | \[ Withdraw \] |

### **Get withdrawals sums**

**Description**

Returns withdrawal sums for last 4 hours and 1 month

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/withdraws/sums
```

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Returns withdrawal sums for last 4 hours and 1 month |

### Delete beneficiary

**Description**

Delete beneficiary

#### HttpRequest

```text
DELETE https://trade.nebulaecn.com/api/v2/auth/account/beneficiaries/{id}
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| id | path | Beneficiary Identifier in Database | Yes | integer |

**Responses**

| Code | Description |
| :--- | :--- |
| 204 | Delete beneficiary |

### **Get beneficiary**

**Description**

Get beneficiary by ID

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/beneficiaries/{id}
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| id | path | Beneficiary Identifier in Database | Yes | integer |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get beneficiary by ID | Beneficiary |

### Activate beneficiary

**Description**

Activates beneficiary with pin

#### HttpRequest

```text
PATCH https://trade.nebulaecn.com/api/v2/auth/account/beneficiaries/{id}/activate
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| id | path | Beneficiary Identifier in Database | Yes | integer |
| pin | formData | Pin code for beneficiary activation | Yes | integer |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Activates beneficiary with pin | Beneficiary |

### Resend pin

**Description**

Resend beneficiary pin

#### HttpRequest

```text
PATCH https://trade.nebulaecn.com/api/v2/auth/account/beneficiaries/{id}/resend_pin
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| id | path | Beneficiary Identifier in Database | Yes | integer |

**Responses**

| Code | Description |
| :--- | :--- |
| 200 | Resend beneficiary pin |

### Create beneficiary

**Description**

Create new beneficiary

#### HttpRequest

```text
POST https://trade.nebulaecn.com/api/v2/auth/account/beneficiaries
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| currency | formData | Beneficiary currency code. | Yes | string |
| name | formData | Human rememberable name which refer beneficiary. | Yes | string |
| description | formData | Human rememberable name which refer beneficiary. | No | string |
| data | formData | Beneficiary data in JSON format | Yes | json |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 201 | Create new beneficiary | Beneficiary |

### Get list of user beneficiaries

**Description**

Get list of user beneficiaries

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/beneficiaries
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| currency | query | Beneficiary currency code. | No | string |
| state | query | Defines either beneficiary active - user can use it to withdraw money or pending - requires beneficiary activation with pin. | No | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get list of user beneficiaries | \[ Beneficiary \] |

### Get deposit address

**Description**

Returns deposit address for account you want to deposit to by currency. The address may be blank because address generation process is still in progress. If this case you should try again later.

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/deposit_address/{currency}
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| currency | path | The account you want to deposit to. | Yes | string |
| address\_format | query | Address format legacy/cash | No | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Returns deposit address for account you want to deposit to by currency. The address may be blank because address generation process is still in progress. If this case you should try again later. | Deposit |

### Get details of deposit

**Description**

Get details of specific deposit.

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/deposits/{txid}
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| txid | path | Deposit transaction id | Yes | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get details of specific deposit. | Deposit |

### Get deposits history

**Description**

Get your deposits history.

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/deposits
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| currency | query | Currency code | No | string |
| state | query | Filter deposits by states. | No | string |
| txid | query | Deposit transaction id. | No | string |
| limit | query | Number of deposits per page \(defaults to 100, maximum is 100\). | No | integer |
| page | query | Page number \(defaults to 1\). | No | integer |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get your deposits history. | \[ Deposit \] |

### Get account by currency

**Description**

Get user account by currency

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/balances/{currency}
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| currency | path | The currency code. | Yes | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get user account by currency | Account |

### Get list of accounts

**Description**

Get list of user accounts

#### HttpRequest

```text
GET https://trade.nebulaecn.com/api/v2/auth/account/balances/
```

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| limit | query | Limit the number of returned paginations. Defaults to 100. | No | integer |
| page | query | Specify the page of paginated results. | No | integer |
| nonzero | query | Filter non zero balances. | No | Boolean |
| search | query |  | No | json |
| search\[currency\_code\] | query |  | No | string |
| search\[currency\_name\] | query |  | No | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | Get list of user accounts | \[ Account \] |











Get your transactions history.

/account/stats/pnl

/account/transactions

/account/withdraws

/account/withdraws/sums

/account/beneficiaries/{id}

/account/beneficiaries/{id}/activate

/account/beneficiaries/{id}/resend\_pin

/account/beneficiaries

/account/deposit\_address/{currency}

/account/deposits/{txid}

/account/deposits

/account/balances/{currency}

/account/balances

