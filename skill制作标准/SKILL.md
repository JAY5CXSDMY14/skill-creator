---
name: skill制作标准
description: 基于Anthropic官方指南的Skill制作完整流程。关键词：制作Skill、创建技能、SKILL.md、YAML、触发词、执行步骤、示例、测试、发布、ClawHub。
allowed-tools: read, write, exec, memory_search
version: 1.0.0
---

# Skill制作标准流程（2026官方最佳实践）

## 核心原则

### 适合做Skill的场景
- ✅ 重复做5次以上的事
- ✅ 有固定规范/步骤/模板
- ✅ 需要工具/脚本完成

### 不适合做Skill的场景
- ❌ 当前项目背景（用Projects）
- ❌ 个人偏好（用Custom Instructions）

---

## 文件结构规范

```
skill-name/
├── SKILL.md           # 必填，核心文件
├── README.md          # 可选，详细说明
├── scripts/           # 可选，执行脚本
│   └── xxx.sh
├── references/       # 可选，参考文档
└── assets/          # 可选，模板资源
```

---

## SKILL.md编写规范

### 1. YAML前置（必填）

```yaml
---
name: skill-name          # 唯一标识，kebab-case（小写+中划线）
description: 关键词：xxx, xxx, xxx  # 触发关键词，10-20个
allowed-tools: tool1, tool2       # 需要用到的工具，留空则默认全部
version: 1.0.0                   # 版本号
---
```

**命名规则**：
- 小写字母
- 中划线分隔
- 避免数字开头

### 2. Markdown正文结构

```markdown
# Skill名称

## 核心原则
- 原则1
- 原则2

## 执行步骤（Claude必须严格按顺序执行）
1. 第一步
2. 第二步
3. 第三步

## 示例

**输入**：xxx

**输出**：
xxx

## 注意事项
- 自检清单1
- 自检清单2
```

---

## 关键要点

### 1. 精准YAML触发
- 放10-20个高频关键词
- 用户提到这些词时会自动触发Skill

### 2. 清晰步骤指令
- 用编号列表
- Claude会严格按顺序执行

### 3. 丰富示例
- 提供3-5个完整输入→输出对
- 帮助Claude理解预期输出

### 4. 自检清单
- 让Claude输出前自动检查
- 提高输出质量

---

## 测试方法

### 本地测试
1. 放入 `~/.claude/skills/` 或项目 `.claude/skills/`
2. 新会话输入触发关键词
3. 观察是否自动加载
4. 用 `/list-skills` 查看已加载技能

### 调试技巧
- 先让Claude输出 "我检测到触发了XXX Skill"
- 如果不触发，优化description关键词
- 查看Claude的思考过程

---

## 发布流程

1. **收集反馈**：用几次后问Claude改进建议
2. **更新版本**：递增version号
3. **发布渠道**：
   - GitHub
   - ClawHub（OpenClaw技能市场）
   - 官方skills.sh

---

## 示例：crypto-monitor Skill

```yaml
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

## 执行步骤
1. 获取ETH价格：curl "https://api.binance.com/api/v3/ticker/24hr?symbol=ETHUSDT"
2. 计算波动幅度
3. 判断是否触发交易信号
4. 执行交易（如有必要）
5. 记录到日志

## 示例

**输入**：监控ETH价格

**输出**：
价格: $2,050 (+3.5%)
信号: 涨幅>3%，继续持有
```

---

## 官方资源

- 完整指南PDF：https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skills-for-Claude.pdf
- 示例仓库：https://github.com/anthropics/skills-library
- 社区Gallery：https://skills.sh/gallery

---

## 一句话总结

**好的Skill = 精准YAML触发 + 清晰步骤指令 + 丰富示例 + 必要脚本/模板**
