---
description: 'This is the official Nebula API document, and will be continue updating.'
---

# Introduction

## General

![](.gitbook/assets/image%20%286%29.png)

* `Aggregative Order Book (Order Book)` is a solution within , which provides services for Clients for professional trading. It allows Clients to view liquidity, place orders, cancel orders and view order status.
* `Client / User` is a company, institution, or high-volume trader \(Broker, Bank, Payment System, Trade institution, etc\)
* `Liquidity` — current open orders \(order book\) from liquidity providers, which may be filled by Client’s orders based on his trading terms.
* `Provider` is an external business entity that Aggregator can use to place orders and view liquidity. Order is a Client’s instruction to Order Book to buy or sell something on Client’s behalf.

### Features

* Liquidity aggregation from all network participants
* Simplified price discovery
* One account 
* One API with easy integration
* One partner for fiat settlements
* Physical delivery of cryptocurrencies online

### Clients, Providers and Liquidity

![](.gitbook/assets/image%20%283%29.png)

Clients get the access to all providers or other network participants and their liquidity inside one platform via fast API or user interface.

### Aggregative Order Book

![](.gitbook/assets/image%20%282%29.png)

Nebula aggregates all liquidity in one place offering you best price, not just routing your order to one of the exchanges. You completely gain directly access to whole market with any order.

### The single wallet

![](.gitbook/assets/image%20%285%29.png)

The funds are debited centrally and directly upon execution of the order. You do not need to preallocate funds to each provider participating in the network.

### Features

* Liquidity aggregation from all network participants
* Simplified price discovery
* One account 
* One API with easy integration
* One partner for fiat settlements
* Physical delivery of cryptocurrencies online



### Order types

`Market` — an order that the Client makes through Order Book to buy or sell Symbol immediately at the best price currently available. The Price field should be missing if the order type is Market. 

`Limit` — an order placed by Client through Order Book to buy or sell an amount of current trading pair at a specified price or better. Both quantity and price fields should be filled if the order type is Limit.  Because the limit order is not a market order, it may not be executed if the price set by the Client cannot be met during the period of time, in which the order is left open.  After being placed, Limit orders can be:

1. Fully executed immediately
2. Not executed immediately, and left open to be fully of partially executed, or cancelled
3. Partially executed immediately and have open outstanding amount waiting to be fully or partially executed, or cancelled.
4. Fill-or-Kill - cancelled completely if not executed immediately.





## API Introduction

Welcome to Nebula API！

This is the official Nebula API document, and will be continue updating. All changes are available in [Change Log section](changel-log.md).

The best option to get to know the API is to start with the [Getting Start section](getting-start.md).



### Contact Us <a id="contact-us"></a>

If you have any other questions on API, or a question about getting an API key,  you can contact us by below ways:

* Send email to [**hello@nebulaecn.com**](mailto:hello@nebulaecn.com)\*\*\*\*



