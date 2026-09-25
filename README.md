# GasStation: Rent TRON Energy, Cut Fees (Docs + FAQ)

English | [简体中文](README.zh-CN.md)

Sending USDT on TRON uses Energy. If the sending address has none, the network burns TRX to pay for it. At current parameters that comes to about 7 TRX when the recipient already holds USDT, and about 14 TRX when the recipient holds none.

GasStation rents Energy and Bandwidth to your address, usually within seconds. You can cut fees by up to 90%, depending on the transaction type and your volume. You also skip staking TRX for resources, which locks your funds for about 14 days when you unstake.

[Rent on gasstation.ai](https://www.gasstation.ai/en/buy) · [API docs](https://gasdocs-en.gasstation.ai/api-references/gas-apis/contact)

## Three ways to rent

**Quick Rent.** Enter the address on the website and pick the amount and rental period, or let GasStation estimate what the transaction needs. Good for occasional transfers and manual work.

**Auto Rent.** Set a threshold on an address. When its Energy drops below that line, GasStation tops it up. Good for deposit and payout addresses that run all day.

**API Rent.** Wallets, exchanges, and payment systems call the API to top up resources before they send a transaction, with batch orders across multiple addresses. The production endpoint is `https://openapi.gasstation.ai`.

All three need only the receiving address. Resources arrive through TRON's native resource delegation, so GasStation has no access to your private key and never holds your assets. When the rental ends, the resources go back.

## Docs

| What you want to do | Doc |
|---|---|
| Get the basics of Energy, Bandwidth, staking, delegation, and rental | [TRON resources and fees FAQ](resources/faq.md) |
| Compare the main ways to reduce TRON transaction fees | [How to reduce TRON transaction fees](guides/how-to-reduce-tron-transaction-fees.md) |
| Reduce TRC20-USDT transfer costs | [How to reduce TRC20-USDT transfer fees](guides/reduce-usdt-trc20-fees.md) |
| See how Energy rental works and when to use it | [How TRON Energy rental works](guides/how-tron-energy-rental-works.md) |

Renting doesn't always win. If an address uses a steady, high volume of Energy every day, staking your own TRX may cost less. [How to reduce TRON transaction fees](guides/how-to-reduce-tron-transaction-fees.md) walks through the comparison.

## Links

| | |
|---|---|
| Website | https://www.gasstation.ai |
| Developer docs | https://gasdocs-en.gasstation.ai |
| API (production) | `https://openapi.gasstation.ai` |
| Blog | https://www.gasstation.ai/en/blog |
| Support (24/7) | [Telegram](https://t.me/GASstation_Service) · [service@gasstation.ai](mailto:service@gasstation.ai) |
