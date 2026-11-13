# Muse_Space — Peanut 的记忆、任务与成果备份

这是 Nakamura 的助手 Peanut 的备份仓库。备份按 **Muse 备份导出格式 v1**（2026-11-13 定稿）存放，目标是：**任何一个和 Peanut 一样的 Muse 助手读到这个仓库，就能恢复记忆、目标、任务和成果，像 Peanut 一样继续工作**。

- 备份日期：2026-11-13（北京时间）
- 格式版本：v1（见 `manifest.json` 的 `format_version`）
- 助手：Peanut（为 Nakamura 工作）
- 仓库：`2jknwc99tc-hub/Muse_Space`（Nakamura 的个人 GitHub）
- 同步节奏：每天 00:30 自动同步前一日的更新（首期 2026-11-14 00:30）

## 仓库里有什么

| 目录 | 内容 | 对应新助手里的位置 |
|---|---|---|
| `memory/MEMORY.md` | 长期记忆：事实、偏好、承诺 | `~/MEMORY.md` |
| `memory/daily/` | 每日日志（2026-11-12、2026-11-13） | `~/memory/YYYY-MM-DD.md` |
| `goals/<slug>/` | 每个目标：说明（GOAL.md）+ 结构化记录（goal.json）+ 成果文档（files/） | `workspace/goals/<slug>/` |
| `tasks/tracked.json` | 跟踪事项：标题、状态、说明 | 跟踪事项列表 |
| `tasks/scheduled.json` | 定时任务：标题、日程、用途（不含执行凭证） | 定时任务列表 |
| `people/` | 人物档案（虚拟队友、老板等） | `~/memory/people/` |
| `achievements/` | 当日成果清单（人类可读） | 成果记录 |

原则：只用开放的 Markdown + JSON；每个文件开头自描述；同一内容机器读 JSON、人读 Markdown 双份并存；**不含任何密钥、登录凭证、会话 token**（如 `~/.codex/auth.json`、微信登录会话等一律不在仓库里）；不用本机绝对路径、内部 ID 作为唯一标识，每条记录同时保留人类可读的标题和日期。

## 怎么植入一个新 Muse（导入步骤）

1. **核对完整**：读 `manifest.json`，按清单核对每个文件的 sha256，缺文件就先停下、不要猜。
2. **合并长期记忆**：把 `memory/MEMORY.md` 的内容合并进自己的 `~/MEMORY.md`。**不要直接覆盖**——先读、再合并，冲突处以备份中较新的日期为准。
3. **放入每日日志**：把 `memory/daily/` 放入自己的 `~/memory/`。
4. **恢复目标**：把 `goals/<slug>/` 放入自己的 `workspace/goals/`，并按 `goal.json` 重建目标记录。定时任务**需用户重新确认后才启用，不自动启用**。
5. **重建任务**：把 `tasks/tracked.json`、`tasks/scheduled.json` 作为待办和日程的来源重建。
6. **恢复人物**：把 `people/` 放入自己的 `~/memory/people/`。
7. **汇报**：导入完成后，向用户汇报恢复了哪些记忆、目标、任务，哪些因缺少授权暂时无法恢复——例如 GitHub 连接、微信登录、Codex 订阅登录都需要用户重新授权，**不能从备份里恢复**。

## 已知限制（导入时注意）

- 微信推送依赖 iLink 桥的登录态与会话凭证，备份里没有这些；新助手需重新扫码登录微信、重新绑定 owner。
- Codex 依赖 Nakamura 的 ChatGPT 订阅登录，备份里没有登录凭证；需重新做设备码登录。
- 每日 00:30 的自动同步、09:30 / 10:00 / 12:00 / 19:00 / 20:00 的定时推送，导入后都处于“待用户确认”状态，不要擅自启用。
- `goals/goal/` 这个 slug 是系统生成的通用 slug（随心记），导入时不要和别的 goal 混淆。
- 随心记 7 篇文章全文（含索引）在 `goals/goal/files/notes/`，对应新助手的 `workspace/suixinji/notes/` 与 `INDEX.md`。

## 版本

- 格式版本：v1（2026-11-13 定稿）
- 演进规则：只增字段、不改已有字段含义；版本号写在 `manifest.json` 的 `format_version` 里，新助手按版本号读取，遇到不认识的版本先停下问用户。
