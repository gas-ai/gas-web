# What Are TRON Energy and Bandwidth?

English | [简体中文](tron-energy-and-bandwidth.zh-CN.md)

Bandwidth and Energy are the two resources TRON uses to measure resource consumption for on-chain transactions: Bandwidth corresponds to transaction data size, while Energy corresponds to the computation involved in smart contract execution. An ordinary TRX transfer requires Bandwidth; a TRC20-USDT transfer also requires Energy. GasStation offers rentals of both resources. Understanding their purpose, limits, and currently available amounts helps you determine what an address needs before sending a transaction.

## Which Resources Do These Two Transfer Scenarios Require?

An ordinary TRX transfer moves the network's native asset. Its main resource requirement is recording transaction data on-chain, so it consumes Bandwidth. Sending TRC20-USDT requires calling the token contract and updating its balance records, consuming Energy as well as Bandwidth.

Think of Bandwidth as the resource used by transaction data and Energy as the resource used for contract computation. They serve different purposes and cannot replace each other. Read-only queries do not create on-chain transactions and should not be confused with actually sending a transaction. See the [TRON Resource Model](https://developers.tron.network/docs/resource-model) for definitions.

If you are preparing to send USDT, check both resources. For an ordinary TRX transfer, focus on Bandwidth. Specific requirements still depend on the actual transaction.

## How Do a TRX Balance, Resource Limits, and Available Resources Differ?

A TRX balance represents the native asset held by an address. A resource limit represents the resource capacity allocated to the account, while available resources are the portion still usable at the time of the query. Holding TRX does not automatically produce an equivalent amount of Energy.

For example, an address may have an Energy allocation but have just completed several contract transactions. It still has an Energy limit, yet may have only a small amount of usable Energy left. To determine whether existing resources can support the next transaction, check the remaining available amount rather than relying only on the limit or an earlier screenshot.

Bandwidth also includes a free allowance and staking-related allocations, whose usage should be checked separately. Energy has no network-provided free allowance. When resources are insufficient, the network can burn TRX to cover the relevant costs under on-chain rules; this does not mean the address has acquired a resource allocation that will continue to recover. See the [TRON Bandwidth and Energy explanation](https://developers.tron.network/docs/bandwidth-and-energy).

For example, GasStation's [Quick Rent guide](https://gasdocs-en.gasstation.ai/product-description/product-introduction/quick-rental-of-trx-energy) explains that connecting a wallet displays the wallet address balance, platform account balance, available and total Energy, and available and total Bandwidth. The wallet address balance describes on-chain assets, the platform account balance is used for payments within the platform, and resource information helps assess on-chain resource readiness. Read these figures separately.

## Where Do Resources Come From, and How Does Delegation Relate to Rental?

An address can obtain Bandwidth or Energy by staking TRX, or receive resources delegated by another account. The resource type selected when staking determines which resource is obtained; staking for Energy should not be treated as also providing enough Bandwidth.

Resource delegation allows the recipient address to use resources obtained through the provider's staking. The underlying TRX remains staked and managed by the provider. The recipient gains the ability to use resources, rather than receiving a TRX transfer. The [TRON resource delegation documentation](https://developers.tron.network/docs/delegation) explains this relationship.

Resource rental is a paid service for resource use, typically specifying an amount, duration, and fee. Through rental, users can purchase temporary access to resources from a provider; resource delegation is an on-chain mechanism that such a service can use. The two are not equivalent: a delegation alone does not establish that a paid rental order exists.

The [official GasStation introduction](https://gasdocs-en.gasstation.ai/product-description/Overview/about-gasstation) describes Energy and Bandwidth rental. Before using the service, confirm the target address, resource type, and service duration, then check whether the resources are usable after delivery. For the rental mechanism, read [How TRON Energy Rental Works](../guides/how-tron-energy-rental-works.md).

## When Do Consumed Resources Recover?

Consumed resources gradually become available again over a rolling 24-hour window rather than resetting for every account at midnight. If further transactions are sent, new consumption affects the account's recovery state, so the available amount changes with time and transaction activity. The [official TRON resource documentation](https://developers.tron.network/docs/bandwidth-and-energy) describes this mechanism.

Recovery of usage does not mean the account retains its resource allocation permanently. After delegation is withdrawn or a rental service ends, you cannot assume the original rented resources will continue recovering to their previous limit simply because 24 hours have not yet passed. The resource recovery cycle is also distinct from the rental service duration; check them separately. GasStation's [Quick Rent documentation](https://gasdocs-en.gasstation.ai/product-description/product-introduction/quick-rental-of-trx-energy) provides separate settings for rental duration and the resource recipient address, illustrating that both the rental period and the destination address need to be checked before use.

## How Can I Check Currently Available Resources?

Users can look for an Energy, Bandwidth, or resources page in a wallet that supports resource displays. If the wallet has no such option, query the sending address in a block explorer. An interface may display total limits, usage, and remaining amounts together, so confirm which metric you are viewing.

Developers can query account resources through [`wallet/getaccountresource`](https://developers.tron.network/reference/getaccountresource). Query the actual sending address on the same network as the transaction. Evaluate resource limits together with usage, and check free Bandwidth separately from staking-related Bandwidth. Do not assume every displayed figure can necessarily cover resource consumption for a single transaction.

A query captures resource status at that moment. If the address sends another transaction or its resource delegation changes after the query, check again before sending. A resource query tells you what is available now; a transaction estimate tells you how much this transaction needs. Compare the two to determine whether there is a shortfall.

For systems that need automated resource preparation, GasStation's [API capabilities overview](https://gasdocs-en.gasstation.ai/product-description/product-introduction/API) describes rental order creation and queries for order and resource delegation status. Platform order status and the sending address's available on-chain resources are different information and should be checked separately. An order having been created does not replace a check that resources have arrived.

## Frequently Asked Questions

### Does Having Enough Energy Guarantee There Will Be No Fees?

Energy covers only contract computation requirements. A transaction also consumes Bandwidth and may involve other applicable on-chain fees; renting resources also has a cost. Sufficient Energy does not mean total cost will necessarily be zero. For other on-chain charging scenarios, see the [TRON resource payment explanation](https://developers.tron.network/docs/paying-for-resources). GasStation's [fee estimation API](https://gasdocs-en.gasstation.ai/api-references/gas-apis/apis/gas-estimate) also explicitly estimates Energy fees only, excluding Net (Bandwidth) fees. This estimate should not be treated as the total cost of the transaction.

### Can Energy and Bandwidth Be Transferred Like USDT?

These resources are not ordinary TRC20 tokens. GasStation's [Energy acquisition explanation](https://www.gasstation.ai/en/blog/tron-energy-buying-guide-reduce-transfer-cost-4099) likewise defines Energy as a network resource for contract execution rather than a conventional token. An account can delegate resources for another address to use, but this differs from sending tokens. Check resource information in the wallet rather than looking for an incoming token transfer named Energy.

## Conclusion

If the sending address has a temporary resource shortfall, you can evaluate GasStation rental to supplement the relevant resources before the transaction, comparing requirements, duration, and total cost. Additional rental is unnecessary when existing resources are sufficient; staking can be evaluated for stable, ongoing demand. For specific methods, continue with [How to Reduce TRON Transaction Fees](../guides/how-to-reduce-tron-transaction-fees.md). If you have already encountered a high charge, start with [Why Are TRON Transaction Fees High?](why-tron-transaction-fees-are-high.md) to investigate the cause.
