# 行测考点讲义 Skill

复习的时候看到一道题目不会，拿着看，太难受了，诶，我有一计！
我把除了语言之外的主要考点都按目录列了出来，有不会的题目先看个大概，然后再对着目录里面找，找到目录之后，直接点上面的词条，就可以转到相对应的详细说明了。
当然，首先你得先学一遍，不然看到题目不知道考的是什么题型。
望诸君青云恒通，不忘初心。

- **172 个考点**，45 个题型章节
- 每个考点：识别信号 → 解题步骤 → 规则 / 公式 → 易错 → 1–2 道例题
- 附 **51 条「题干特征 → 考点」路由表**，支持「这道题考什么」式提问

## 安装

Agent Skills 是开放标准，任何支持 `SKILL.md` 的宿主都能用。

```bash
# 跨 Agent 目录（Copilot CLI / Codex / Amp / OpenCode）
git clone https://github.com/banxiadw/xingce-skill ~/.agents/skills/xingce

# Claude Code
git clone https://github.com/banxiadw/xingce-skill ~/.claude/skills/xingce

# DSH（DeepSeek Harness）
git clone https://github.com/banxiadw/xingce-skill ~/.dsh/skills/xingce
```

也可以直接用 skills CLI：

```bash
npx skills add banxiadw/xingce-skill
```

装完在新会话里 `/xingce`，或直接问：

```
xingce 这道题考什么：甲单独 10 天、乙单独 15 天完成某工程，甲做 4 天后乙接手……
xingce 类比推理里种属和组成怎么区分
xingce 图推的笔画数怎么数
xingce 数字推理看到分数数列先做什么
```

## 它怎么工作

1. 读题干，在 [`reference/router.md`](reference/router.md) 里匹配「题干特征」；
2. 打开对应章节，核对「识别信号」；
3. 按 [`reference/usage.md`](reference/usage.md) 的五段式输出：**题型 → 考点 → 判据 → 方法 → 易错**。

路由表只是入口，最终以章节里的识别信号为准，避免关键词误判。

## 结构

```
xingce-skill/
├── SKILL.md                  # 入口：用法、七部分总纲、45 章索引、考点速查
├── chapters/ch01–ch45.md     # 题型章节，按需加载（每章 2–4 KB）
├── reference/
│   ├── router.md             # 题干特征 → 考点
│   ├── points.json           # 考点字典（id / 名称 / 星级 / 章节）
│   └── usage.md              # 五段式输出约定
├── examples/worked-examples.md
└── LICENSE
```

## 覆盖范围

| 板块 | 内容 |
|---|---|
| 判断推理 | 图形推理、定义判断、类比推理、逻辑论证、逻辑推理 |
| 数量关系 | 数字推理（八类数列 + 判别链）、数学运算（工程 / 经济 / 溶液 / 容斥 / 最值 / 周期 / 几何 / 排列组合 / 概率） |

**不含**：行程、牛吃草、年龄等专题；图形推理不含原稿图片，具体图形需另给原图。

## 版权与使用范围

- 仅供个人学习！
## License

MIT（仅覆盖框架、脚本与模板），详见 [LICENSE](LICENSE)。
