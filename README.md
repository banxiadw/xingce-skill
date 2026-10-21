# 行测考点讲义 Skill

把「判断推理 + 数量关系」整理成一本可查询的考点讲义，并让 Agent 能用它**把一道题定位到具体考点**、给出解题步骤与易错点。

- 172 个考点，45 个题型章节
- 每个考点：识别信号 → 解题步骤 → 规则/公式 → 易错 → 1–2 道例题
- 附「题干特征 → 考点」路由表（51 条）

## 安装

Agent Skills 是开放标准，任何支持 `SKILL.md` 的宿主都能用（Claude Code、Copilot CLI、Codex、OpenCode、Amp 等）。

```bash
# 方式一：跨 Agent 目录
git clone <this-repo> ~/.agents/skills/xingce

# 方式二：Claude Code
git clone <this-repo> ~/.claude/skills/xingce

# 方式三：DSH（DeepSeek Harness）
git clone <this-repo> ~/.dsh/skills/xingce
```

装完在新会话里 `/xingce`，或直接说：

```
xingce 这道题考什么：甲单独 10 天、乙单独 15 天完成某工程，甲做 4 天后乙接手……
xingce 类比推理里种属和组成怎么区分
xingce 图推的笔画数怎么数
```

## 结构

```
xingce-skill/
├── SKILL.md                  # 技能入口：用法、总纲、章节索引、考点速查
├── chapters/ch01–ch45.md     # 45 个题型章节，按需加载
├── reference/
│   ├── router.md             # 题干特征 → 考点 路由表
│   ├── points.json           # 考点字典（id/名称/星级/章节），便于二次开发
│   └── usage.md              # 输出约定（五段式回答）
├── examples/worked-examples.md
└── LICENSE
```

## 设计取舍

- **按题型切章节，不按考点切**：问一个方法时只加载 2–4 KB，不把整本塞进上下文。
- **路由表只做入口**：最终判断以章节内的「识别信号」为准，避免关键词误判。
- **例题克制**：每个考点 1–2 道，够示范「这题长什么样」即可。

## 版权与使用范围

本仓库内容是对**第三方课程笔记**（花生十三、四海等）的二次整理与结构化，**不是原笔记的复制**，也不包含原稿扫描图。

- 个人学习、自用没问题。
- **公开发布前请自行确认授权**：如果原笔记受版权保护，公开仓库可能构成侵权。更稳妥的做法是**私有仓库**，或只公开框架（`SKILL.md` 结构、路由表、输出约定）而移除具体内容。
- 代码部分（脚本、模板）可按 MIT 使用；讲义内容版权归原作者。

## 重新生成

内容由 `data_*.py` 驱动（不在本仓库内）。若你维护的是完整项目：

```bash
python build.py        # 生成 HTML 讲义
python export.py       # 导出 PDF（含书签与可点击目录）
python build_skill.py  # 生成技能目录
```
