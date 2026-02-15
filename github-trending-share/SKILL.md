---
name: github-trending-share
description: 关键词：GitHub、热榜、Trending、每日收藏、项目链接、Stars、趋势分析、归档、飞书推送
allowed-tools: exec, feishu_doc, memory_search
version: 1.0.0
---

# GitHub热榜收集技能

## 核心原则
- 链接必须可点击溯源
- 格式简洁清晰
- 自动推送到GitHub
- 飞书只推送链接

## 执行步骤（严格按顺序执行）

1. **获取热榜数据**
   - 调用GitHub API获取Top 10
   - 命令：`curl -s "https://api.github.com/search/repositories?q=created:>$(date -v-7d +%Y-%m-%d)&sort=stars&order=desc"`

2. **生成Markdown**
   - 项目名转为Markdown链接格式：`[用户名/项目名](链接)`
   - 保存为 `YYYY-MM-DD.md`

3. **推送到GitHub**
   - cd ~/awesome-daily-trending
   - git add . && git commit -m "Add: GitHub热榜Top10" && git push

4. **更新README索引**
   - 在README.md顶部添加当日链接

5. **飞书推送**
   - 只推送链接，不加额外分析
   - 格式：`📊 GitHub热榜 YYYY-MM-DD\n\n🔗 链接`

## 示例

**输入**：执行GitHub热榜收集

**输出**：
```
✅ 已推送！
链接：https://github.com/JAY5CXSDMY14/awesome-daily-trending/blob/main/2026-02-16.md
```

**飞书推送**：
```
📊 GitHub热榜 2026-02-16

🔗 https://github.com/JAY5CXSDMY14/awesome-daily-trending/blob/main/2026-02-16.md
```

## 自检清单

- [ ] 项目名是否转为Markdown链接？
- [ ] 是否保存为正确日期格式？
- [ ] 是否推送到GitHub？
- [ ] 飞书是否只推送链接？

## 文件位置
- 脚本：`~/scripts/github-trending-to-repo.sh`
- 仓库：https://github.com/JAY5CXSDMY14/awesome-daily-trending

## 依赖
- curl
- python3
- git
