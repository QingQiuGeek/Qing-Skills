# Qing-Skills

**语言 / Language**: [简体中文](#中文介绍) | [English](#english)

> 一个持续扩展的 Agent Skill 集合。目前包含 `frontend-dev`，后续会增加更多 skill。
>
> A growing collection of Agent Skills. Currently contains `frontend-dev`; more skills will be added over time.

---

## 中文介绍

[English](#english) | [返回顶部](#qing-skills)

Qing-Skills 是面向 AI 编码助手（如 Claude Code）的技能仓库，每个 skill 封装一套可复用的工作方法论，让 AI 在处理特定类型任务时遵循统一的流程与质量标准。

### 安装

```bash
npx skills add https://github.com/QingQiuGeek/Qing-Skills -g -y
```

- `-g` 装到用户级技能目录（所有项目可用）；不加则只装进当前项目。
- `-y` 跳过交互、直接安装全部；不加会逐个询问要装哪些 skill。

### 已收录的 Skill

#### frontend-dev — 前端文档驱动开发

把「做什么 / 长什么感觉 / 怎么设计 / UI 怎么搭 / 每个页面怎么搭 / 什么不要做」从口头讨论固化成六份文档，让编码有唯一事实源，并在需求变化后持续回写。

**核心理念：先有文档，再写代码。**

六份文档各司其职（一件事只写在一份文档里，其它文档只引用不复述）：

| 文件 | 回答的问题 |
| --- | --- |
| `prd.md` | 做什么：定位、目标用户、站点页面层级、功能清单、业务规则、技术栈 |
| `visual.md` | 长什么感觉：视觉方向、品牌气质、参考站、不追求的风格 |
| `design.md` | 具体怎么设计：颜色、字体、间距、圆角、阴影、响应式（含适配优先级）、主题 |
| `ui-patterns.md` | UI 怎么搭：Tokens → Components → Blocks → Pages、目录结构、组件规范、导航信息架构与 URL 约定、文案规范 |
| `page-specs.md` | 每个页面怎么搭：Route、结构、状态、跳转、验收点 |
| `avoid.md` | 什么不要做：反模式清单、默认套路、AI 常见问题 |

典型工作流：`prd → visual → design → ui-patterns → page-specs（+ avoid 贯穿）→ accept（先搭代码，再整体验收）`。

编码阶段遵循**一次只动一个模块，做完先让用户验收，通过后再进入下一个**；交付时给出可复核的证据，而不是一句「已完成」。

本 skill 只管流程与文档，不提供具体技术知识：动手前先复用环境里已有的专项 skill（组件库、Tailwind、React 性能等），
没有再按项目现有约定自行判断，不为此引入新技术栈；视觉方向始终以 `visual.md` / `design.md` 为准。

**适用场景**：启动前端项目 / 新页面 / 新功能，或需要编写、维护上述规格文档时。不适用于纯后端、脚本等无 UI 任务。

**目录结构**：

```
frontend-dev/
├── SKILL.md                 # skill 入口：使用纪律、文档分工、变更回写规则
├── agents/
│   └── openai.yaml          # agent 接口定义
└── references/              # 各模式的详细参考（按需读取）
    ├── prd.md
    ├── visual.md
    ├── design.md
    ├── ui-patterns.md
    ├── page-specs.md
    ├── avoid.md
    └── acceptance.md        # 编码纪律与验收标准
```

### 后续规划

本仓库将持续扩展，增加更多领域的 skill（如后端、测试、文档等方向），欢迎期待。

---

## English

[简体中文](#中文介绍) | [Back to top](#qing-skills)

Qing-Skills is a repository of Agent Skills for AI coding assistants (such as Claude Code). Each skill packages a reusable methodology, so the AI follows a consistent workflow and quality bar for a specific type of task.

### Install

```bash
npx skills add https://github.com/QingQiuGeek/Qing-Skills -g -y
```

- `-g` installs to the user-level skills directory (usable in every project); drop it to install into the current project only.
- `-y` skips the prompts and installs everything; drop it to pick which skills to install.

### Available Skills

#### frontend-dev — Spec-Driven Frontend Development

Turns "what to build / how it should feel / how to design it / how to structure the UI / how to build each page / what to avoid" from verbal discussion into six spec documents, giving implementation a single source of truth that is kept in sync as requirements change.

**Core principle: docs first, code second.**

The six documents each own exactly one concern (write each thing once, reference it elsewhere — duplication inevitably drifts):

| File | Question it answers |
| --- | --- |
| `prd.md` | What to build: positioning, target users, page hierarchy, feature list, business rules, tech stack |
| `visual.md` | How it should feel: visual direction, brand tone, reference sites, styles to avoid |
| `design.md` | How to design it: colors, typography, spacing, radii, shadows, responsive (with adaptation priority), theming |
| `ui-patterns.md` | How to structure the UI: Tokens → Components → Blocks → Pages, directory layout, component specs, navigation IA and URL conventions, copy rules |
| `page-specs.md` | How to build each page: route, structure, states, navigation, acceptance points |
| `avoid.md` | What NOT to do: anti-patterns, default tropes, common AI pitfalls |

Typical workflow: `prd → visual → design → ui-patterns → page-specs (+ avoid throughout) → accept (build, then acceptance)`.

During implementation: **one module at a time, user acceptance before moving to the next**. Deliverables come with verifiable evidence, not just "done".

This skill owns process and docs only, not domain technical knowledge: reuse an existing domain-specific skill (component library, Tailwind, React performance, etc.) when one is available, otherwise follow the project's existing conventions instead of pulling in a new stack. Visual direction always comes from `visual.md` / `design.md`.

**When to use**: starting a frontend project, page, or feature; writing or maintaining the spec docs above. Not for backend-only, scripting, or other non-UI work.

**Directory layout**:

```
frontend-dev/
├── SKILL.md                 # Skill entry point: discipline, doc responsibilities, write-back rules
├── agents/
│   └── openai.yaml          # Agent interface definition
└── references/              # Detailed per-mode references (read on demand)
    ├── prd.md
    ├── visual.md
    ├── design.md
    ├── ui-patterns.md
    ├── page-specs.md
    ├── avoid.md
    └── acceptance.md        # Coding discipline and acceptance criteria
```

### Roadmap

This repository will keep growing with skills for other domains (backend, testing, documentation, etc.). Stay tuned.
