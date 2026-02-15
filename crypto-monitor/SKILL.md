---
name: crypto-monitor
description: 关键词：加密货币、比特币、以太坊、ETH、BTC、价格监控、交易、止损、止盈、交易所API、Binance、OKX
allowed-tools: exec, memory_search
version: 1.0.0
---

# 加密货币监控技能

## 核心原则
- 严格遵守止损止盈规则
- 每天交易≤2笔
- 记录每一笔交易
- 非必要不交易

## 凭证管理
- OKX API位置：~/.openclaw/credentials/okx-api-key.txt
- 读取方式：`API_KEY=$(cat ~/.openclaw/credentials/okx-api-key.txt)`

## 执行步骤（严格按顺序执行）

1. **获取价格**
   - ETH: `curl -s "https://api.binance.com/api/v3/ticker/24hr?symbol=ETHUSDT"`
   - BTC: `curl -s "https://api.binance.com/api/v3/ticker/24hr?symbol=BTCUSDT"`

2. **计算波动**
   - 对比上一小时价格
   - 计算涨跌幅

3. **判断信号**
   - 波动>3%：生成交易信号
   - 涨幅>5%：考虑止盈
   - 跌幅>5%：考虑加仓

4. **执行交易**（如有明确信号）
   - 读取OKX API：~/.openclaw/credentials/okx-api-key.txt
   - 先汇报，等待确认
   - 严格遵守止损/止盈

5. **记录日志**
   - 写入交易日志
   - 包含：时间、币种、操作、价格、数量、备注

## 风控规则

| 规则 | 值 |
|------|-----|
| 止损 | -10% |
| 止盈 | +30% |
| 每天交易 | ≤2笔 |
| 单笔仓位 | ≤10% |
| 杠杆 | 0x |

## 示例

**输入**：监控ETH价格

**输出**：
```
价格: $2,050 (+3.5%)
波动: <3°，无交易信号
决策: 继续持有
```

**输入**：ETH跌幅6%

**输出**：
```
⚠️ 交易信号：ETH跌幅6%
价格: $1,980 (-6%)
建议：考虑加仓
等待确认后执行
```

## 自检清单

- [ ] 是否正确读取了API Key？
- [ ] 是否遵守止损规则？
- [ ] 是否遵守止盈规则？
- [ ] 今日交易次数≤2？
- [ ] 单笔仓位≤10%？
- [ ] 是否记录到日志？

## 文件位置
- 凭证：~/.openclaw/credentials/okx-api-key.txt
- Market CLI：~/market-cli/
- 交易脚本：~/crypto-trader/src/smart-trader.js
- 日志：memory/crypto-trading-log.md
- 仓库：https://github.com/JAY5CXSDMY14/crypto-trader

## 依赖
- curl
- Node.js 18+
- OKX API / Binance API
