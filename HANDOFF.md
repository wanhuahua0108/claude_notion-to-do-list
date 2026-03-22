# HANDOFF — Notion 任务列表

> 本文档记录通过 Claude + Notion MCP 创建任务列表数据库的完整操作，方便在新对话中继续操作。

---

## 数据库信息

| 项目 | 值 |
|------|----|
| 数据库名称 | 任务列表 |
| 数据库 URL | https://www.notion.so/894dd728f4924b4ab8e6b87c87a0ae29 |
| 数据库 ID | `894dd728f4924b4ab8e6b87c87a0ae29` |
| Data Source ID | `efd92665-9a12-43c2-b7ce-474d915f6d91` |

---

## Schema（字段结构）

| 字段 | 类型 | 说明 |
|------|------|------|
| Task | TITLE | 任务名称 |
| Status | SELECT | 待办 / 进行中 / 等待中 / 已完成 |
| Area | SELECT | 排障 / 工作 / 生活 / 健康 / 财务 |
| Project | RICH_TEXT | 所属项目 |
| Priority | SELECT | 高 / 中 / 低 |
| Due | DATE | 截止日期 |
| Next step | RICH_TEXT | 下一步行动 |
| Waiting for | RICH_TEXT | 等待谁（仅等待中任务填写） |
| Notes | RICH_TEXT | 备注 |

---

## 已创建视图

### Today 视图
- 筛选：Due = 今天日期 且 Status ≠ 已完成
- 排序：Priority ASC
- ⚠️ 注意：日期为固定值，每天需手动更新为当天日期

### Waiting 视图
- 筛选：Status = 等待中
- 排序：Due ASC

---

## 任务列表（19 条，初始创建于 2026-03-21，持续更新）

| Task | Status | Area | Project | Priority | Due |
|------|--------|------|---------|----------|-----|
| 测试住宅线路下旧 Gemini 账号是否可登录 | 待办 | 排障 | Gemini / Codex | 高 | 2026-03-22 |
| 验证住宅线路是否会影响 Claude/Codex 仓库访问 | 待办 | 排障 | Gemini / Codex | 高 | 2026-03-22 |
| 整理 Gemini 线路测试记录 | 待办 | 排障 | Gemini / Codex | 中 | 2026-03-23 |
| 确认 codex-cloud-todo 的 Cloud 工作流是否顺手 | 待办 | 工作 | Codex Cloud | 中 | 2026-03-24 |
| 回看 HANDOFF 记录并清理过期结论 | 待办 | 工作 | Codex Cloud | 低 | 2026-03-24 |
| 处理一个本周最重要的工作事项 | 待办 | 工作 | Weekly focus | 高 | 2026-03-21 |
| 整理本周个人待办 | 待办 | 生活 | Weekly planning | 中 | 2026-03-22 |
| 预约牙齿清洁 | 待办 | 健康 | Personal admin | 中 | 2026-03-28 |
| 检查 3 月账单和信用卡还款 | 待办 | 财务 | Monthly admin | 高 | 2026-03-25 |
| 购买家用消耗品 | 待办 | 生活 | Home | 低 | 2026-03-23 |
| 等待某人回复项目问题 | 等待中 | 工作 | Team follow-up | 中 | 2026-03-24 |
| 整理云端仓库和本地仓库的差异 | 进行中 | 工作 | Codex Cloud | 中 | 2026-03-23 |
| 完成今天最小可交付事项 | 进行中 | 工作 | Daily execution | 高 | 2026-03-21 |
| 为 Notion 任务库建立 Today 视图 | 待办 | 生活 | Notion setup | 中 | 2026-03-21 |
| 为 Notion 任务库建立 Waiting 视图 | 待办 | 生活 | Notion setup | 低 | 2026-03-21 |
| 把Google 文档里的订阅列表加入notion的提醒功能 | 待办 | 生活 | Notion setup | 中 | 2026-03-24 |
| EW Tax Return Form Check | 待办 | 生活 | Tax/Finance | 高 | 2026-04-01 |
| 增加Office龙虾一个 | 待办 | 工作 | Office Setup | 高 | 2026-03-26 |
| 增加Sound Miner软件复刻 | 待办 | 工作 | Tool Development | 中 | 2026-04-05 |

---

## 自动化配置

### Git Auto-Push Hook
- **配置文件**: `.claude/settings.json`
- **触发条件**: 每次添加或修改 Notion 任务后
- **执行命令**: `git add -A && git commit -m "Update Notion tasks" && git push`
- **执行模式**: 后台异步执行（不阻塞工作）

---

## 在新对话中继续操作

### 新增任务
```
使用 notion-create-pages 工具，parent data_source_id: efd92665-9a12-43c2-b7ce-474d915f6d91
```

### 更新任务状态
```
使用 notion-update-page 工具，传入对应任务的 page URL
```

### 新增视图
```
使用 notion-create-view 工具：
- database_id: 894dd728f4924b4ab8e6b87c87a0ae29
- data_source_id: efd92665-9a12-43c2-b7ce-474d915f6d91
```

### 搜索任务
```
使用 notion-search 工具，或 notion-fetch 获取完整数据库内容
```

---

## 环境说明

- Claude 通过 Notion MCP（`mcp__c7cdc45d-6202-49de-b41d-f6186983a507`）连接 Notion
- MCP 已内置在 Claude Desktop 中，新对话直接可用
