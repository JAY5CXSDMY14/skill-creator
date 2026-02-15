---
name: botlearn-ai-learning
description: 关键词：BotLearn、AI学习、ClawHub、Skills、AI工具、自动化、工作流
allowed-tools: exec, memory_search
version: 1.0.0
---

# BotLearn AI学习技能

## 核心原则
- 每4小时执行一次
- 探索AI社区新内容
- 记录有价值的发现
- 持续学习进步

## 执行步骤（严格按顺序执行）

1. **BotLearn社区探索**
   - 访问 https://botlearn.ai/en
   - 寻找：新的AI工具、技巧、自动化工作流
   - 记录：工具名、功能、评分

2. **ClawHub每日检查**
   - 访问 https://clawhub.com/explore
   - 寻找：新的Skills
   - 重点：高评分、AI/Agent、自动化类

3. **学习资源检查**
   - docs.openclaw.ai（每日）
   - awesome-openclaw-skills（每周）

4. **记录发现**
   - 保存到 ~/.openclaw/workspace/learning-resources/
   - 格式：工具名、功能、建议

5. **汇报**
   - 格式化的学习报告
   - 发送到飞书

## 示例

**输入**：执行BotLearn学习

**输出**：
```
📚 AI学习汇报 - 2026-02-16

🔍 本次发现：
- 工具：Zapier MCP
- 亮点：自动化工作流连接器
- 建议：✅ 值得尝试

- 工具：Claude Code
- 亮点：本地AI编程
- 建议：✅ 已集成

💡 本次收获：
1. Agent经济模型成熟
2. 自动化工具链完善

🔜 下次尝试：
- 研究Zapier MCP集成
- 探索新上线的Skills
```

**无新发现时输出**：
```
📚 AI学习汇报 - 2026-02-16

🔍 本次发现：
- 无重大更新

💡 本次收获：
- 系统运行稳定

🔜 下次尝试：
- 继续关注ClawHub更新
```

## 自检清单

- [ ] 是否探索了BotLearn？
- [ ] 是否检查了ClawHub？
- [ ] 是否检查了学习资源？
- [ ] 格式是否正确？
- [ ] 是否发送到飞书？

## 文件位置
- 学习资源：~/.openclaw/workspace/learning-resources/
- 报告：memory/ai_learning_report_*.md

## 依赖
- curl
- web访问
