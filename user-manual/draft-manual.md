# Draft Manual



*   * Phone verification - is a step where a user needs to verify his phone number. First, a user needs to enter phone number than the platform sends SMS with verification code. Second, a user needs to submit a verification code to verify the phone number.

  ![kyc-phone](https://www.openware.com/sdk/images/guides/baseapp/kyc-phone.png) 

  * Complete profile - is a step where a user needs to provide his personal information: `First name`, `Last name`, `Address`, `Nationality`, `City`, `Citizenship`, `Postcode` and `Date of birth`.

    ![kyc-identity](https://www.openware.com/sdk/images/guides/baseapp/kyc-identity.png) - Documents verification - is a step where a a user needs to provide a government-issued document that proves his/her identity. As a proof of identity, a user can upload a photo of a passport or an identity card \(front and back sides\) and, a selfie image of him/her holding the document.

    ![kyc-docs](https://www.openware.com/sdk/images/guides/baseapp/kyc-docs.png) - Address verification - is a procedure needed to verify the user's address. For this, a user needs to fill in the address and upload a utility bill to prove it.

    ![profile](https://www.openware.com/sdk/images/guides/baseapp/kyc-address.png) - The status of the Profile verification process is displayed as a progress bar. Additionally, a status is assigned to each verification procedure \(email verification, phone verification, identity verification, document verification and residence verification\): - `Verified` \(verification passed successfully\);

    ![kyc-verified](https://www.openware.com/sdk/images/guides/baseapp/kyc-verified.png) - `Pending` \(verification in progress\);

    ![kyc-pending](https://www.openware.com/sdk/images/guides/baseapp/kyc-pending.png) - `Rejected` \(verification failed\). In this case, Reverify button is displayed, and a user can re-enter/reupload data for verification.

    ![kyc-rejected](https://www.openware.com/sdk/images/guides/baseapp/kyc-rejected.png) - If the data necessary to perform verification haven't been submitted yet, 'Verify' button is displayed near the corresponding procedure.

    ![kyc-active](https://www.openware.com/sdk/images/guides/baseapp/kyc-active.png) - By default identity, document and address verifications are done via third-party KYC provider KYCAid.

#### Description of the `My API Keys` window: <a id="description-of-the-my-api-keys-window"></a>

`My API Keys` is a window for API keys management. To be able to create and manage API keys, a user needs to enable 2FA.

![API\_2](https://www.openware.com/sdk/images/guides/baseapp/my_api_keys_no_2fa.png)

To create a new API key a user needs to click the `Create new` button, then pops up a window for 2FA code in which a user needs to enter 2FA code.

![API\_3](https://www.openware.com/sdk/images/guides/baseapp/my_api_keys_no_keys.png)

After that, a window with a new API key appears. A user needs to copy the `Access key`, the `Secret key` and to click the `CONFIRM` button. The `Secret key`shows only once. If a user forgot or lost `Secret key`, he can delete that API key and generate a new one.

![API\_4](https://www.openware.com/sdk/images/guides/baseapp/api_key_profile.png)

The new API key appears in the `My API Keys` window where a user can manage that API key. To disable an API key a user needs to click the switch button than a user needs to enter 2FA code. To delete an API key a user needs to click the `X` button than a user needs to enter 2FA code.

![API\_5](https://www.openware.com/sdk/images/guides/baseapp/my_api_keys.png)

#### Description of the `Account activity` window: <a id="description-of-the-account-activity-window"></a>

Account activity is a window that contains information about a resent action of a user on the platform.

​ **Field name description:**

* **Date:** shows the date of an activity.
* **Action**: shows the action type performed by a user.
* **Result**: shows the result of an action. The result can be `Succeed` and `Failed`.
* **Address IP**: shows the IP address of a user computer from which the action was performed.

![account\_activity](https://www.openware.com/sdk/images/guides/baseapp/account_activity.png)

### 3. Trade <a id="3-trade"></a>

The trading page contains components that are essential for trading. A user can customize the size and position of components of all components on the trading page.

#### **Chart** <a id="chart"></a>

The chart shows a graphical representation of an asset price for a certain time frame. The platform uses the TradingView chart component.

The TradingView chart is customizable and provides the next functionality to a user:

* to draw using drawing toolbar;
* to change chart timeframe and to zoom it using scroll;
* to change chart representation \(Bars, Candles, Hollow Candles, Heikin Ashi, Line, Area, Baseline\);
* to do chart comparison of different markets;
* to add multiple indicators to market chart;
* to undo or redo chart editing;
* to take instant snapshots. The user can save snapshot locally or share a snapshot link;
* to save chart layout;
* to change chart properties;
* to open chart in fullscreen mode.

![chart](https://www.openware.com/sdk/images/guides/baseapp/chart.png)

#### **Order book** <a id="order-book"></a>

The order book shows detailed information about orders that are waiting for fulfilment. This component resizable and can be in one of two modes: vertical and horizontal. The order book consists of `Buy` and `Sell` orders separated by the last market price. If the order book set in the vertical mode `Sell` orders located in the upper part of the order book and `Buy` orders located in the lower part of the order book. If the order book set in the horizontal mode `Sell` orders located on the right part of the order book and `Buy` orders located on the left part of the order book. The order book consists of three columns: `Price`, `Total` and `Amount`.

`Price` column in the order book shows price levels of orders. If the order book in the vertical mode `Buy` orders with the highest price and `Sell` orders with the lowest price located next to the field of the last market price.

`Amount` column shows the quantity of base currency that a user wants to sell or buy at the certain price level.

`Total` column shows the cumulative amount of a base currency placed in the orders at a certain price level. The `Total` column shows the market depth. Alongside with the `Total` column, the order book has a graphical representation of the market depth in the way of coloured horizontal bars.

Below, you can find examples of the order book in vertical and horizontal mode.

![order\_book](https://www.openware.com/sdk/images/guides/baseapp/order_book.png) ![order\_book](https://www.openware.com/sdk/images/guides/baseapp/order_book_horizontal.png)

A user can use the `order book` to prefill the `order form` with a price and an amount. A user can fill the `order form` with a certain price by clicking the price field of a certain order in the `order book`. A user can fill the `order form` with a certain price and a certain amount by to clicking the amount field of a certain order in the `order book`. Also, a user can fill the `order form` with a certain price and a certain amount \(that represent liquidity at a certain price level\) by clicking the total field of a certain order in the `order book`.

#### **Market Depth** <a id="market-depth"></a>

The Market depth window shows a grid with buy and sells orders at a certain price level. Market depth has two sides the left side shows Bids \(coloured green\) and the right side shows Asks \(coloured red\). On hovers pops up a window with detailed information on liquidity level of a certain price level.

![market\_depth](https://www.openware.com/sdk/images/guides/baseapp/market_depth.png)

#### **Markets** <a id="markets"></a>

The markets window shows trading pairs that are supported by the platform. Header part of the markets window contains tabs. The `All` tabs show all market pairs. The rest tabs represent market pair of a certain quote currency. The table part of the market window has `Markets`, `Last Price`, `Volume` and `Change`:

* **Market**: shows market pairs that are supported by the platform.
* **Last Price**: shows the price of the last trade of a certain market pair.
* **Volume**: shows a cumulative trading volume of a certain pair for the last 24 hours \(showed in a quote currency\).
* **Change:** shows a change of a price in the certain market pair for the last 24 hours.

The search field allows searching for a certain market pair or a ticker.

![markets\_list](https://www.openware.com/sdk/images/guides/baseapp/markets.png)

#### **Open Orders** <a id="open-orders"></a>

The open orders window shows information about active orders. That window contains open orders that are related to the chosen market pair. The open window table has the next column: `Time`, `Price`, `Amount`, `Value`, and `Field`:

* **Time**: shows date and time of order creation.
* **Price \(a quote currency\)**: shows a price at which a user wants to buy or sell an asset.
* **Amount \(base currency\)**: shows an amount that a user wants to sell or to buy.
* **Value \(a quote currency\)**: shows order an approximated value of an order in a quote currency.
* **Field**: shows the execution percentage of an order.

Clicking the `X` button allows cancellation of the user's open order.

![open\_orders](https://www.openware.com/sdk/images/guides/baseapp/open_orders.png)

### 4. Wallet page <a id="4-wallet-page"></a>

Wallet page has a list of wallets and provides functionality for depositing and withdrawal. This page consists of two blocks. The left side block represents wallets of different currencies. Wallet field contains a logo, a ticker, a full name of a currency, available and locked balances. The right side block serves for wallet interaction and has `Deposit` and `Withdraw` tabs. Wallets of crypto and FIAT currencies differentiates by required data for withdrawal creation.

**Deposit tab - Crypto**

The `Deposit` tab of cryptocurrency shows balances, a deposit address and a deposit history. To make a deposit, a user needs to use a deposit wallet. User can scan QR-code or can press the `COPY` button to copy a deposit wallet address. `Deposit history` is a table with recent deposits. Deposit record contains a date of deposit, a status of deposit and deposited amount. Deposits that are waiting for confirmation has a `pending` status.

![wallets\_user](https://www.openware.com/sdk/images/guides/baseapp/wallets/crypto/deposit.png)

**Withdrawal tab - Crypto**

Withdrawal functionality from version 2.3 working with beneficiaries. That adds a layer of security by whitelisting withdrawal wallet addresses and accounts. To be able to withdraw, a user needs to have a certain KYC level and needs to enable 2FA.

The `Withdraw` tab of cryptocurrency shows balances, a beneficiary field, a withdrawal amount field, a 2FA code field, the `Withdraw` button and withdrawal history. To make a withdrawal, a user needs to have a beneficiary account. If a user doesn't have a beneficiary, he should add at least one beneficiary by clicking `Add Account` field.

![wallets\_user\_1](https://www.openware.com/sdk/images/guides/baseapp/wallets/crypto/withdrawal/no_beneficiary.png)

Clicking the `Add Account` field prompts a modal window. In that window, a user needs to write:

* a withdrawal address in the `Blockchain Address` field;
* a name for withdrawal address in the `Beneficiary Name` field;
* description for that withdrawal address in the `Description` field. That field is optional.

After filling the form, a user needs to click the `SUBMIT FOR CONFIRMATION` button. After submitting, the platform sends an email with a pin code and prompts a modal window for that pin code.

![wallets\_user\_1](https://www.openware.com/sdk/images/guides/baseapp/crypto_beneficiary_form.png)

A user needs to enter the received pin code into the `Confirm new account` modal window and to press the `CONFIRM` button.

![wallets\_user](https://www.openware.com/sdk/images/guides/baseapp/beneficiary_confirmation.png)

If a beneficiary account added successfully, a user can create a withdrawal specifying a withdrawal amount and 2FA code. After pressing the `WITHDRAW` button, confirmation windows appears. On the left side of `WITHDRAW` button, a user can see a withdrawal fee and amount that he will get on his wallet. `Withdrawal History` is a table of recent withdrawals. Withdrawal record contains a date of withdrawal request, the status of a withdrawal request and a withdrawal amount.

![wallets\_user\_1](https://www.openware.com/sdk/images/guides/baseapp/wallets/crypto/withdrawal/beneficiary.png)

To confirm a withdrawal request a user needs to click on the `WITHDRAW` button. If a user wants to cancel a withdrawal request he needs to press the `CANCEL` button.

![withdrawal\_conf](https://www.openware.com/sdk/images/guides/baseapp/withdrawal_confirmation.png)

User can have more than one whitelisted address. To see detail information, a user can click the info circle icon. Also, a user can delete whitelisted addresses by clicking the bucket icon.

![wallets\_user\_1](https://www.openware.com/sdk/images/guides/baseapp/wallets/crypto/withdrawal/beneficiary_list.png)

**Deposit tab - FIAT**

The `Deposit` tab of FIAT currency shows balances, a deposit address and a deposit history. To make a deposit, a user needs to use credential from the right side menu.

![wallets\_user](https://www.openware.com/sdk/images/guides/baseapp/wallets/fiat/deposit.png)

**Withdrawal tab - FIAT**

The `Withdraw` tab of FIAT has the same structure as a wallet of cryptocurrency. To make a FIAT withdrawal, a user needs to have a beneficiary account for FIAT. A user can add FIAT beneficiary by clicking `Add Account` field.

![wallets\_user](https://www.openware.com/sdk/images/guides/baseapp/wallets/fiat/withdrawal/no_beneficiary.png)

Clicking the `Add Account` field prompts a modal window. In that window, a user needs to write:

* `Description` is a field for beneficiary description;
* `Full Name` is a field for user full name of that beneficiary;
* `Account number` is a field for the bank account number of a user;
* `Bank Name` is a field for the name of bank of the account number;
* `Bank Swift Code` is a field for SWIFT code. That field is optional;
* `Intermediary Bank Name` is a field for intermediary bank name. That field is optional;
* `Intermediary Bank Swift Code` is a field for SWIFT code intermediary bank. That field is optional;

After filling the form, a user needs to click the `SUBMIT FOR CONFIRMATION` button. After submitting, the platform sends an email with a pin code and prompts a modal window for that pin code.

![wallets\_user](https://www.openware.com/sdk/images/guides/baseapp/fiat_beneficiary_form.png)

If a beneficiary account added successfully, a user can create a withdrawal. A user can create new FIAT beneficiaries and manage them in the same way as crypto beneficiaries.

![wallets\_user](https://www.openware.com/sdk/images/guides/baseapp/wallets/fiat/withdrawal/beneficiary.png)

### 5. Orders <a id="5-orders"></a>

Orders page represent user’s orders information. Page has two tabs: `Open` and `All`. The `Open` tab shows open orders. The `All` tab shows the orders history. A user can cancel all open orders by clicking `Stop all` button.

![orders](https://www.openware.com/sdk/images/guides/baseapp/orders/open.png)

**Field name description:**

* **Date:** shows the date and time of order creation or date of the last update.
* **Order type**: shows the type of an open order.
* **Pair**: shows the market pair name of an open order.
* **Price**: shows the price of an order.
* **Amount**: shows the amount that placed in an order.
* **Executed**: shows an order amount that was executed \(base currency equivalent\).
* **Remaining**: shows an order amount to be executed \(base currency equivalent\).
* **Cost remaining**: shows remaining cost of the order to be executed \(quote currency equivalent\).
* **Status**: shows the status of an order. The `Open` tab contains only orders with `Open` status, the `All` tab contains orders with statuses `Open`, `Stopped`, `Executed`.
* **X**: is a cancel button. A user can cancel an open order by clicking that button.

![orders\_all](https://www.openware.com/sdk/images/guides/baseapp/orders/all.png)

### 6. History <a id="6-history"></a>

`History` page contains historical data related to the user's finance movement. This page consists of three tabs: `Deposit History`, `Withdraw History` and `Trade History`.

**Deposit history tab**

**Field name description:**

* **txID:** shows the hash of a deposit transaction on a blockchain.
* **Date**: shows the date and time of a deposit.
* **Currency**: shows a ticker of deposited currency.
* **Amount**: shows a deposited amount.
* **Status**: shows the status of deposit. A deposit can can have one of the next statuses:
  * **Submitted** is the initial state of a deposit. That status assigns to a deposit that was just detected.
  * **Accepted** state means that the minimal number of confirmation blocks were successfully mined above the block with the deposit transaction.
  * **Collected** state means that funds were collected to one or few platform wallets.
  * **Skipped** state means that the platform tried to collect funds from deposit to platform wallet and fail.
  * **Rejected** means that a deposit was rejected by the admin during the confirmation process.
  * **Canceled** means that a deposit was cancelled automatically by some platform services.

![history\_deposits](https://www.openware.com/sdk/images/guides/baseapp/history/deposits.png)

**Withdrawal history tab**

That tab contains the user's withdrawal history.

**Field name description:**

* **Address:** shows a user withdrawal address.
* **Date**: shows the date of withdrawal.
* **Currency**: shows the currency ticker of withdrawal.
* **Amount**: shows a withdrawal amount.
* **Fee**: shows the fee that the platform charged from a withdrawal.
* **Status**: shows the status of withdrawal. A withdrawal can have one of the next statuses:
  * **Submitted** status means that the platform received withdrawal request for a user.
  * **Accepted** status means that the request is waiting for further processing. If a withdrawal stuck with that status, it means that request exceeds some of the withdrawal limits.
  * **Processing** status means that the platform prepares withdrawal to send it to a blockchain network.
  * **Confirming** status means that a withdrawal was written into a blockchain and waiting for `Min Confirmations` number.
  * **Failed** status means that a withdrawal faced some issues during the processing.
  * **Succeed** status means that a withdrawal was successfully recorded into a blockchain and reached `Min Confirmations` number.
  * **Rejected** status means that a withdrawal rejected manually, by the admin. Admin can reject a withdrawal that exceeds some of the withdrawal limits.

![history\_withdrawals](https://www.openware.com/sdk/images/guides/baseapp/history/withdrawals.png)

**Trade history tab**

That tab contains the user's trades history.

**Field name description:**

* **Date:** shows the date and time of a trade.
* **Side**: shows the side of a trade \('Buy' or 'Sell'\).
* **Market**: shows a market pair of a trade.
* **Price**: shows the price at which an order was executed.
* **Amount**: shows an amount of a base currency that was exchanged in a trade.
* **Total**: shows an amount of a quote currency that was exchanged in a trade.

