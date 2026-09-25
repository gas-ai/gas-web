# GasStation：租 TRON 能量，降手续费（文档 + FAQ）

[English](README.md) | 简体中文

在 TRON 上转 USDT 要消耗 Energy。发送地址没有 Energy 的话，网络会燃烧 TRX 来付这笔费用。按目前的参数，对方地址已经持有 USDT 时大约烧 7 TRX，对方没有 USDT 时大约 14 TRX。

GasStation 把 Energy 和 Bandwidth 租给你的地址，一般几秒到账。手续费最高能省约 90%，具体省多少看交易类型和用量。你也不用为了拿资源去质押 TRX，质押的 TRX 解冻通常要等 14 天。

[去官网租](https://www.gasstation.ai/buy) · [API 文档](https://gasdocs-zh.gasstation.ai/api-references/gas-apis/contact)

## 三种租法

**快捷租赁**。在官网填地址，选租多少、租多久，也可以让系统按交易估算用量。适合偶尔转账、手动操作。

**自动租赁**。给地址设一个阈值，Energy 低于阈值时系统自动补上。适合一直在跑的收款、出款地址。

**API 租赁**。钱包、交易所、支付系统可以在发交易前调接口补资源，支持多个地址批量下单。生产环境地址是 `https://openapi.gasstation.ai`。

三种方式都只需要收资源的地址。资源通过 TRON 原生的资源代理到账，GasStation 拿不到你的私钥，也不托管资产，租期结束后资源自动收回。

## 文档

| 你想解决的问题 | 推荐文档 |
|---|---|
| 想先搞懂 Energy、Bandwidth、质押、代理与租赁 | [TRON 资源与手续费 FAQ](resources/faq.zh-CN.md) |
| 想比较几种降低 TRON 手续费的办法 | [如何降低 TRON 交易手续费](guides/how-to-reduce-tron-transaction-fees.zh-CN.md) |
| 想降低 TRC20-USDT 转账手续费 | [如何降低 TRC20-USDT 转账手续费](guides/reduce-usdt-trc20-fees.zh-CN.md) |
| 想知道 Energy 租赁怎么运作、什么时候该用 | [TRON Energy 租赁是怎么工作的](guides/how-tron-energy-rental-works.zh-CN.md) |

租赁也有不划算的时候。地址每天的 Energy 用量稳定、利用率又高，自己质押 TRX 可能更便宜，[如何降低 TRON 交易手续费](guides/how-to-reduce-tron-transaction-fees.zh-CN.md)里写了怎么比较。

## 链接

| | |
|---|---|
| 官网 | https://www.gasstation.ai |
| 开发者文档 | https://gasdocs-zh.gasstation.ai |
| API（生产环境） | `https://openapi.gasstation.ai` |
| 博客 | https://www.gasstation.ai/blog |
| 客服（7×24） | [Telegram](https://t.me/GASstation_Service) · [service@gasstation.ai](mailto:service@gasstation.ai) |
