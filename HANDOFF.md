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

### Default view（主视图）
- **列顺序**: Area | Task | Status | Priority | Due | Next step | Notes | Project | Waiting for
- **筛选**: Status ≠ 已完成（自动隐藏已完成的任务）
- **排序**: Priority ASC（优先级升序）
- **用途**: 所有进行中的任务一览

### Today 视图 ✅
- **ID**: view://32bf3252-684f-8155-b9ee-000c49b1fd4a
- **筛选**: Status ≠ 已完成
- **排序**: Priority ASC（优先级升序）
- **用途**: 快速查看所有未完成的任务，按优先级排序

### Waiting 视图 ✅
- **ID**: view://32bf3252-684f-81c0-aced-000c292a6c4a
- **筛选**: Status = 等待中
- **排序**: Due ASC（截止日期升序）
- **用途**: 追踪等待他人响应/反馈的任务

### 已完成 视图 ✅
- **ID**: view://32bf3252-684f-81bc-827a-000c7fb2b4b6
- **筛选**: Status = 已完成
- **排序**: Due DESC（截止日期降序）
- **用途**: 查看已完成的任务历史

### 工作 视图 ✅
- **ID**: view://32bf3252-684f-8194-b7b0-000cdc592053
- **筛选**: Area = 工作 AND Status ≠ 已完成
- **排序**: Priority ASC（优先级升序：高→中→低）
- **用途**: 查看所有工作类任务，按优先级排序

### 生活 视图 ✅
- **ID**: view://32bf3252-684f-81b5-8787-000c2cd9e949
- **筛选**: Area = 生活 AND Status ≠ 已完成
- **排序**: Priority ASC（优先级升序：高→中→低）
- **用途**: 查看所有生活类任务，按优先级排序

---

## 任务列表（22 条，初始创建于 2026-03-21，持续更新）

| Task | Status | Area | Project | Priority | Due |
|------|--------|------|---------|----------|-----|
| 测试住宅线路下旧 Gemini 账号是否可登录 | 待办 | 排障 | Gemini / Codex | 高 | 2026-03-22 |
| 验证住宅线路是否会影响 Claude/Codex 仓库访问 | 待办 | 排障 | Gemini / Codex | 高 | 2026-03-22 |
| 整理 Gemini 线路测试记录 | 待办 | 排障 | Gemini / Codex | 中 | 2026-03-23 |
| 确认 codex-cloud-todo 的 Cloud 工作流是否顺手 | 待办 | 工作 | Codex Cloud | 中 | 2026-03-24 |
| 回看 HANDOFF 记录并清理过期结论 | 待办 | 工作 | Codex Cloud | 低 | 2026-03-24 |
| 处理一个本周最重要的工作事项 | 待办 | 工作 | Weekly focus | 高 | 2026-03-21 |
| 整理本周个人待办 | 待办 | 生活 | Weekly planning | 中 | 2026-03-22 |
| 预约牙齿清洁 | 待办 | 生活 | Personal admin | 中 | 2026-03-28 |
| 检查 3 月账单和信用卡还款 | 待办 | 财务 | Monthly admin | 高 | 2026-03-25 |
| 购买家用消耗品 | 待办 | 生活 | Home | 低 | 2026-03-23 |
| 等待某人回复项目问题 | 等待中 | 工作 | Team follow-up | 中 | 2026-03-24 |
| 整理云端仓库和本地仓库的差异 | 进行中 | 工作 | Codex Cloud | 中 | 2026-03-23 |
| 完成今天最小可交付事项 | 进行中 | 工作 | Daily execution | 高 | 2026-03-21 |
| 为 Notion 任务库建立 Today 视图 | 已完成 | 生活 | Notion setup | 中 | 2026-03-21 |
| 为 Notion 任务库建立 Waiting 视图 | 已完成 | 生活 | Notion setup | 低 | 2026-03-21 |
| 把Google 文档里的订阅列表加入notion的提醒功能 | 待办 | 生活 | Notion setup | 中 | 2026-03-24 |
| EW Tax Return Form Check | 待办 | 生活 | Tax/Finance | 高 | 2026-04-01 |
| 增加Office龙虾一个 | 待办 | 工作 | Office Setup | 高 | 2026-03-26 |
| 增加Sound Miner软件复刻 | 待办 | 工作 | Tool Development | 中 | 2026-04-05 |
| 学习Claude Course | 待办 | 工作 | Learning | 高 | - |
| 在Cowork里完成任务 | 待办 | 工作 | Work Location | 中 | - |
| 把Obsidian用起来 | 待办 | 工作 | Tools Setup | 高 | - |

---

## 自动化配置

### Git Auto-Push Hook（Notion 任务变更）
- **配置文件**: `.claude/settings.json`（项目级）
- **事件**: PostToolUse（Notion 工具执行后）
- **触发条件**: 每次添加或修改 Notion 任务后
- **执行命令**: `git add -A && git commit -m "Update Notion tasks" && git push`
- **执行模式**: 后台异步执行（不阻塞工作）

### Auto-Handoff Hook（手动触发）
- **配置文件**: `~/.claude/settings.json`（全局）
- **事件**: UserPromptSubmit（用户提交 prompt 时）
- **触发条件**: prompt 包含 "handoff" 或 "Handoff"（不区分大小写）
- **执行命令**: `git add -A && git commit -m "Auto-commit: Handoff command" && git push`
- **执行模式**: 后台异步执行
- **用途**: 快速保存和推送所有改动到 GitHub

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
