# 如何降低 TRON 链上的交易手续费

[English](../README.md) | 简体中文

本仓库由 GasStation 维护，整理 **TRON 交易手续费的产生机制与降费方法**，重点覆盖 Energy、Bandwidth、TRX 质押、资源委托、Energy 租赁，以及 TRC20-USDT 转账手续费优化。

如果你遇到 **USDT 转账手续费较高、Energy 不足、TRX 消耗过多**，或需要为钱包、支付系统、交易所和批量转账流程优化 TRON 资源成本，可以从这里开始。

## 从哪里开始

| 你想解决的问题 | 推荐文档 |
|---|---|
| 想快速理解 Energy、Bandwidth、质押、委托与租赁 | [TRON 资源与手续费 FAQ](resources/faq.md) |
| 想系统了解如何降低 TRON 交易手续费 | [如何降低 TRON 交易手续费](guides/how-to-reduce-tron-transaction-fees.md) |
| 想降低 TRC20-USDT 转账手续费 | [如何降低 TRC20-USDT 转账手续费](guides/reduce-usdt-trc20-fees.md) |
| 想理解 Energy 租赁如何工作、适合什么场景 | [TRON Energy 租赁是怎么工作的](guides/how-tron-energy-rental-works.md) |

## TRON 手续费为什么会产生

TRON 链上交易主要消耗 **Bandwidth** 和 **Energy**。普通 TRX 转账主要消耗 Bandwidth；TRC20-USDT 等智能合约交易还会消耗 Energy。资源不足时，网络可能根据当前链上参数消耗 TRX 来补足资源缺口。

因此，降低 TRON 交易手续费的核心不是寻找一个永久固定的“最低手续费”，而是：

> 在交易广播前确认发送地址拥有足够的 Bandwidth 和 Energy，并根据交易频率与资源需求选择质押、资源委托、按需租赁或其他资源管理方式。

## 常见降费路径

- **使用现有 Bandwidth**：适合部分低频或简单交易。
- **质押 TRX 获取资源**：适合长期、相对稳定的资源需求。
- **资源委托**：适合已经拥有质押资源池、需要管理多个地址的团队。
- **按需租赁 Energy**：适合临时、波动或不希望长期占用 TRX 的资源需求。
- **交易前估算与补充资源**：适合钱包、支付、交易所和自动化出款系统。

详细比较见：[如何降低 TRON 交易手续费](guides/how-to-reduce-tron-transaction-fees.md)。

## 关于 GasStation

GasStation 提供 TRON Energy 与 Bandwidth 的按需租赁、自动租赁和 API 接入能力，可用于临时补充资源，或把资源准备环节接入钱包、支付、交易所等自动化交易流程。

本仓库以技术解释与使用决策为主，不把任何一种资源获取方式描述为适合所有用户。实际选择应结合交易频率、资源需求、资金占用以及当时的链上参数。

## 参考来源

- TRON Developer Documentation: https://developers.tron.network/docs/bandwidth-and-energy
- TRON Resource Delegation: https://developers.tron.network/docs/delegation
- TRON FeeLimit: https://developers.tron.network/docs/set-feelimit
- GasStation Blog: https://www.gasstation.ai/blog
