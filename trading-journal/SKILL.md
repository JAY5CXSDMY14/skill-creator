---
name: trading-journal
description: 关键词：交易日记、加密货币、持仓、浮盈、止损、止盈、OKX、Binance、日志
allowed-tools: exec, feishu_doc, memory_search
version: 1.0.0
---

# 交易日记技能

## 核心原则
- 每日23:30执行
- 记录当日交易
- 分析市场状态
- 制定明日计划

## 执行步骤（严格按顺序执行）

1. **获取账户状态**
   - 运行：`node ~/crypto-trader/src/smart-trader.js balance`
   - 获取余额、持仓、数量

2. **获取市场价格**
   - ETH: `curl -s "https://api.binance.com/api/v3/ticker/24hr?symbol=ETHUSDT"`
   - BTC: `curl -s "https://api.binance.com/api/v3/ticker/24hr?symbol=BTCUSDT"`

3. **生成日记**
   - 运行：`bash ~/crypto-trader/scripts/generate-journal.sh`
   - 保存到 journal/目录

4. **推送到GitHub**
   - git add . && git commit && git push

5. **汇报摘要**
   - 发送到飞书

## 日记格式

```markdown
# 交易日记 - 2026-02-16

## 市场状态
- BTC: $68,900 (+1.2%)
- ETH: $2,050 (+3.5%)

## 账户状态
- 初始资金: 11 USDT
- 当前余额: 0 USDT
- 持仓: 0.000075 BTC

## 今日交易
| 时间 | 币种 | 操作 | 价格 | 数量 |
|------|------|------|------|------|
| 14:30 | ETH | 买入 | $2,000 | 0.01 |

## 明日计划
1. 继续监控支撑位
2. 到达支撑位执行买入
3. 记录每笔交易
```

## 自检清单

- [ ] 是否获取了账户状态？
- [ ] 是否获取了市场价格？
- [ ] 是否推送到GitHub？
- [ ] 是否发送到飞书？

## 文件位置
- 脚本：~/crypto-trader/scripts/generate-journal.sh
- 仓库：https://github.com/JAY5CXSDMY14/crypto-trader

## 依赖
- curl
- node
- git
