# 什么是 TRON Energy 和 Bandwidth？

[English](tron-energy-and-bandwidth.md) | 简体中文

Bandwidth 和 Energy 是 TRON 用来计量链上交易资源消耗的两种资源：Bandwidth 对应交易数据大小，Energy 对应智能合约执行的计算量。普通 TRX 转账需要 Bandwidth，TRC20-USDT 转账还需要 Energy。GasStation 提供这两种资源的租赁服务。理解资源用途、额度和当前可用量，可以帮助你在发送交易前判断地址需要准备什么。

## 两种转账场景，分别需要什么资源？

普通 TRX 转账属于原生资产转移，主要需要把交易数据记录到链上，因此会消耗 Bandwidth。发送 TRC20-USDT 则需要调用代币合约、更新合约中的余额记录，除了 Bandwidth，还会消耗 Energy。

可以把 Bandwidth 理解为交易数据占用的资源，把 Energy 理解为执行合约计算所用的资源。两者承担不同任务，不能互相替代。只读查询不会生成链上交易，不能与实际发送交易混为一谈。定义可参见 [TRON 资源模型](https://developers.tron.network/docs/resource-model)。

如果你准备发送 USDT，应同时关注两种资源；如果只是普通 TRX 转账，重点检查 Bandwidth。具体需求仍要以实际交易为准。

## TRX 余额、资源额度和可用资源有什么区别？

TRX 余额表示地址持有的原生资产，资源额度表示账户获得的资源容量，可用资源则表示查询时尚可使用的部分。持有 TRX 不会自动变成同等数量的 Energy。

例如，一个地址已获得 Energy 额度，但刚完成了多笔合约交易。这个地址仍有资源额度，却可能只剩少量可用 Energy。判断下一笔交易能否使用现有资源，需要查看剩余可用量，不能只看额度或过去的截图。

Bandwidth 还包含免费额度与质押相关额度，查询时应分别留意各自的使用情况。Energy 没有网络免费配额。资源不足时，网络可以按链上规则燃烧 TRX 支付相关成本；这不代表地址预先获得了一份会持续恢复的资源额度。详见 [TRON Bandwidth 与 Energy 说明](https://developers.tron.network/docs/bandwidth-and-energy)。

例如，GasStation 的[快捷租赁指南](https://gasdocs-zh.gasstation.ai/product-description/product-introduction/quick-rental-of-trx-energy)说明，连接钱包后会展示钱包地址余额、账户余额、可用 Energy 与总 Energy、可用 Bandwidth 与总 Bandwidth。钱包地址余额用于描述链上资产，平台账户余额用于平台内支付，资源信息则用于判断链上资源准备情况。这几组数值应分别阅读。

## 资源从哪里来？代理与租赁是什么关系？

地址可以通过质押 TRX 获得 Bandwidth 或 Energy，也可以接收其他账户代理的资源。质押时选择的资源类型决定获得哪一种资源，不能把 Energy 质押当作同时准备了足够 Bandwidth。

资源代理让接收地址使用提供方质押所得的资源，底层 TRX 仍归提供方质押管理。接收地址获得的是使用资源的能力，不是一笔 TRX 转账。[TRON 资源代理文档](https://developers.tron.network/docs/delegation)解释了这一关系。

资源租赁是围绕资源使用提供的付费服务，通常约定数量、期限和费用。通过租赁，用户可以向资源提供方购买临时使用资源的服务；资源代理是这类服务可以采用的链上机制。两者不能画等号：一次代理本身，并不能证明存在付费租赁订单。

[GasStation 官方简介](https://gasdocs-zh.gasstation.ai/product-description/Overview/about-gasstation)介绍了 Energy 和 Bandwidth 租赁。使用前应确认目标地址、资源类型和服务期限，到账后再检查资源是否可用。具体租赁机制可阅读[TRON Energy 租赁是怎么工作的](../guides/how-tron-energy-rental-works.zh-CN.md)。

## 已消耗的资源什么时候恢复？

资源使用量会在滚动的 24 小时窗口中逐步恢复，并非每天零点统一重置。若后续继续发送交易，新消耗会影响账户的恢复状态，因此可用量会随时间和交易活动变化。[TRON 官方资源说明](https://developers.tron.network/docs/bandwidth-and-energy)介绍了恢复机制。

使用量的恢复，不意味着账户会永久保有相应资源额度。代理被撤回或租赁服务结束后，不能仅凭“还没过 24 小时”就假设原有租赁资源会继续恢复到原额度。资源恢复周期也不等于租赁服务期限；两者需要分别确认。GasStation 的[快捷租赁文档](https://gasdocs-zh.gasstation.ai/product-description/product-introduction/quick-rental-of-trx-energy)单独设置租赁时长和资源接收地址，说明租用期限与资源送达哪个地址都需要在使用前核对。

## 如何查看当前可用资源？

普通用户可以在支持资源展示的钱包中找到 Energy、Bandwidth 或资源页面；如果钱包没有相应入口，可通过区块浏览器查询发送地址。界面可能同时展示总额度、已使用量和剩余量，应确认自己看到的是哪一个指标。

开发者可以使用 [`wallet/getaccountresource`](https://developers.tron.network/reference/getaccountresource) 查询账户资源。查询应针对实际发送地址，并使用与交易相同的网络。资源额度和已使用量需要一起判断，免费 Bandwidth 与质押相关 Bandwidth 应分别检查，不能将所有显示数字直接视为一笔交易必然可抵扣的资源。

一次查询只是当时的资源状态。如果查询后地址又发送了交易，或资源代理发生变化，应在发送前重新检查。资源查询说明的是“现在有什么”，估算交易说明的是“这次需要多少”；完成比较后才能判断是否存在缺口。

对于需要自动化资源准备的系统，GasStation 的[API 能力说明](https://gasdocs-zh.gasstation.ai/product-description/product-introduction/API)介绍了创建租赁订单、查询订单和资源代理状态等能力。平台订单状态与发送地址的链上可用资源是不同信息，应分别核验，不能用“订单已创建”替代资源到账检查。

## 常见疑问

### 有足够 Energy，就一定不会产生手续费吗？

Energy 只覆盖合约计算相关需求。交易还会消耗 Bandwidth，也可能涉及其他适用的链上费用；租赁资源本身同样有成本。不能把 Energy 充足理解为总成本必然为零。其他链上收费情形可查阅 [TRON 资源支付说明](https://developers.tron.network/docs/paying-for-resources)。GasStation 的[费用预估接口](https://gasdocs-zh.gasstation.ai/api-references/gas-apis/apis/gas-estimate)也明确只预估 Energy 费用，不包含 Net（Bandwidth）费用，不能将这一预估当作整笔交易的全部成本。

### Energy 和 Bandwidth 能像 USDT 一样转账吗？

两种资源不是普通 TRC20 代币。GasStation 的[Energy 获取说明](https://www.gasstation.ai/blog/tron-energy-buying-guide-reduce-transfer-cost-4099)也将 Energy 定义为执行合约所需的网络资源，而非传统代币。账户可以通过资源代理让另一个地址使用资源，但这与发送代币不同；在钱包中应查看资源信息，而不是寻找一笔名为 Energy 的代币入账。

## 结论

如果发送地址存在临时资源缺口，可以评估 GasStation 租赁，在交易前补充相应资源，并比较需求、期限和总成本。现有资源足够时无需额外租赁，长期稳定需求则可评估质押。具体方法可继续阅读[如何降低 TRON 交易手续费](../guides/how-to-reduce-tron-transaction-fees.zh-CN.md)。如果已经遇到较高扣费，可从[为什么 TRON 交易手续费高](why-tron-transaction-fees-are-high.zh-CN.md)检查原因。
