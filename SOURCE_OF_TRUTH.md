# SOURCE_OF_TRUTH.md

数据权威索引。解决「AI 找不到文件」和「同一数据多个版本不知道以哪个为准」的问题。

---

## GitHub 发布（权威源）

| 路径 | 说明 | 权威性 |
|------|------|--------|
| `skills/dbs*/SKILL.md` | 6 个 Skill 的权威定义 | **最高** — 所有 chatbot 版本、知识包都从这里派生 |
| `知识库/原子库/atoms.jsonl` | 4,176 个知识原子（全量） | **最高** — 按季度拆分的 jsonl 是子集 |
| `知识库/原子库/atoms_*Q*.jsonl` | 按季度拆分的知识原子 | 派生自 atoms.jsonl |
| `知识库/Skill知识包/*.md` | 10 个方法论文档（每 Skill 2 个） | **最高** — Skill 运行时读取的深度参考 |
| `知识库/高频概念词典.md` | 高频概念定义 | **最高** |
| `README.md` | 项目说明（面向 GitHub 用户） | — |
| `LICENSE` | CC BY-NC 4.0 | — |

## 本地私有（不发 GitHub）

| 路径 | 说明 | 权威性 |
|------|------|--------|
| `chatbot/system-prompt-v9-yuanqi.md` | v9 腾讯元器版系统提示词 | **最高** — 元器平台的当前版本 |
| `chatbot/system-prompt-v9-doubao.md` | v9 豆包版系统提示词 | **待填充** |
| `chatbot/system-prompt-v1~v8*.md` | 历史版本存档 | 仅存档，不使用 |
| `chatbot/README.md` | chatbot 目录说明 + 版本演进发现 | — |
| `plans/` | 内部计划文档 | — |
| `skills 版本管理/` | v1/v2 版本对比和测试报告 | 仅存档 |

## 知识库（不发 GitHub 的部分）

| 路径 | 说明 | 权威性 |
|------|------|--------|
| `知识库/legacy/` | 旧版知识库 | **已废弃** — 被原子库 + Skill 知识包替代 |
| `知识库/主题索引/` | 主题索引 | 辅助工具 |
| `知识库/_预处理/` | 预处理文件 | 中间产物 |

## 项目外相关位置

| 路径 | 说明 | 权威性 |
|------|------|--------|
| `~/.claude/skills/dbs*` | Skill 实际安装位置 | **派生** — 从 `skills/` 同步而来 |
| `~/.claude/skills/` (其他) | gstack 等非 dbs 的 skill | 不属于本项目 |
| `.../dontbesilent 的商业/gstack/` | gstack skill 中英文翻译参考 | **非权威** — 仅供查看，权威源在 `~/.claude/skills/gstack/` |

## 数据流向

```
skills/SKILL.md（权威源）
    ↓ 合并 + 平台适配
chatbot/system-prompt-v9-*.md（chatbot 部署版）

知识库/原子库/atoms.jsonl（权威源）
    ↓ 提炼
知识库/Skill知识包/*.md（方法论文档）
    ↓ 被 Skill 引用
skills/SKILL.md 运行时读取
```

## 冲突规则

1. Skill 内容以 `skills/*/SKILL.md` 为准，chatbot 版本是派生物
2. 知识数据以 `知识库/原子库/atoms.jsonl` 为准
3. 方法论以 `知识库/Skill知识包/*.md` 为准
4. `legacy/` 下的任何内容不再作为参考
