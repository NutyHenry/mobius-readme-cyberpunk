<div align="center">

<img src="https://capsule-render.vercel.app/api?type=venom&color=gradient&customColorList=12,14,16,18,20&height=200&section=header&text=M%C3%96BIUS&fontSize=80&fontAlignY=38&fontColor=ffffff&stroke=000000&strokeWidth=2&animation=twinkling" alt="MÖBIUS Banner" />

# ⫷⫸ MÖBIUS · AGENTICOS ⫷⫸

```diff
@@ 不是聊天框，是一台能自己改自己的工作台 @@
```

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=20&pause=1200&color=8B5CF6&center=true&vCenter=true&random=false&width=720&lines=%E2%97%87+Mobius+uses+Mobius+to+develop+Mobius;%E2%97%87+One+idea+%E2%86%92+swarm+of+agents+working+in+parallel;%E2%97%87+See+every+project%2C+every+member+on+one+screen;%E2%97%87+Bring+any+Anthropic%2FOpenAI-compatible+model;%E2%97%87+Blackboard-style+research+with+chief+%2B+assistants" alt="Typing SVG" />

<p>
  <img src="https://img.shields.io/badge/%F0%9F%94%A5_AgenticOS-Mobius-8B5CF6?style=for-the-badge&labelColor=1a1a2e" alt="AgenticOS" />
  <img src="https://img.shields.io/badge/%E2%99%BE_Self--Iterating-Loop-06B6D4?style=for-the-badge&labelColor=1a1a2e" alt="Self-Iterating" />
  <img src="https://img.shields.io/badge/%F0%9F%A7%A0_Cluster_Thinking-Blackboard-EC4899?style=for-the-badge&labelColor=1a1a2e" alt="Cluster" />
  <img src="https://img.shields.io/badge/%F0%9F%8E%AF_Any_Model-Compatible-F59E0B?style=for-the-badge&labelColor=1a1a2e" alt="Any Model" />
  <br/>
  <a href="https://mobius.nutshellai.cn/"><img src="https://img.shields.io/badge/%F0%9F%8C%90_Website-mobius.nutshellai.cn-00FF9F?style=for-the-badge&logo=googlechrome&logoColor=white&labelColor=0d1117" alt="Website" /></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/%F0%9F%93%9C_License-Source_Available-FF6B9D?style=for-the-badge&logo=book&logoColor=white&labelColor=0d1117" alt="License" /></a>
  <img src="https://img.shields.io/badge/%F0%9F%92%9C_Status-Beta-9D4EDD?style=for-the-badge&labelColor=0d1117" alt="Status" />
</p>

```
╔══════════════════════════════════════════════════════════════════════╗
║  🌀  Mobius · 一个用 Issue / Session 流程管理自己代码的 Agent 工作台   ║
╚══════════════════════════════════════════════════════════════════════╝
```

</div>

---

## 🗺️ 这份 README 的导览

> 📍 **[Mobius 是什么](#-mobius-是什么)** · **[8 个能力](#-8-个能力)** · **[工作模型](#-工作模型)** · **[小莫助理](#-小莫助理)** · **[快速开始](#-快速开始)** · **[许可证](#-许可证)**

---

## 🌀 Mobius 是什么

一句话：把"项目 → 任务 → Agent 执行"整条流水线放进一个 Web 工作台，让 Agent 真的进到你代码目录里干活，而不是只在对话框里说话。

普通 Agent 的产出停留在聊天框外；Mobius 会把每次执行的产出（代码、记忆、技能、扩展、研究结果）回灌成系统能力，让下一轮更聪明。Mobius 自己也是这么变好的 —— 团队用 Mobius 开发 Mobius。

```
┌─────────────────────────────────────────────────────────┐
│  旧循环：感知 → 规划 → 执行 → 反思 → 任务结束 → 回原点  │
│  新循环：感知 → 规划 → 执行 → 反思 → 沉淀 ↻ 升一层      │
└─────────────────────────────────────────────────────────┘
```

> 💡 底层是 GLM-5.2（Z.AI 兼容接口），也可以换成任何 Anthropic 兼容的代理端点。一个 Key 就能让 Agent 跑起来。

---

## ⚡ 8 个能力

> 八项能力都在同一条莫比乌斯环上 —— 不是独立功能列表，是同一条流水线的不同环节。

<details>
<summary><b>🔄 [01] 自迭代：Mobius 用 Mobius 改 Mobius</b></summary>

Mobius 自己也是项目。任何 `bind_path` 指向 Mobius 源码目录、被标记为 `is_self_develop` 的项目，都可以通过正常的 Issue / Session 流程修改 Mobius 自己。

**实际怎么运转：**

1. 你（或小莫）发现一个想改进的点，在自迭代项目里提个 Issue
2. 创建 Session，挂上 `mobius-self-iter` 技能
3. Agent 改代码、跑测试、commit
4. 走 `python3 product.py` 重新部署
5. 改进落到生产，下一轮 Mobius 就更强一点

自迭代项目还支持**版本回退**（`hard-reset-version`），改坏了能滚回去。

> 三层进化（用户驱动 / 信息驱动 / 认知驱动）是设计目标，目前主要落地的是第一层。第二、第三层在持续打磨。

</details>

<details>
<summary><b>🧠 [02] 集群思考：一个想法，多 Agent 协同推进</b></summary>

复杂问题单 Agent 跑不动，Mobius 能拉起一支 Agent 编队。每个 Agent 在独立工作站里干自己的子任务，通过 **Blackboard（共享黑板）** 异步交换信息，最后由 Chief 把结果拼起来。

```
       ┌── Agent[0] ──┐
idea ─▶├── Agent[1] ──┼──▶ Chief 收敛 ──▶ 最终成果
       └── Agent[2] ──┘
              ↑
        Blackboard 共享黑板
        （jsonl 文件，每条带作者、时间、可见性）
```

**Blackboard 实际机制：**

- 落地在项目目录的 `.imac/blackboard/<research_id>/blackboard.jsonl`
- 每个 Agent 启动时自动 subscribe，3 秒一次扫描新条目
- Agent 开始/结束动作时都要往黑板上写一条
- 同时维护一个 `research-graph.yml` 作为可视化研究图谱

适合的场景：技术选型、竞品分析、文献综述 —— 任何需要多视角信息汇合的事。

</details>

<details>
<summary><b>👥 [03] 团队协作 MAX：一人成群，协同作战</b></summary>

**一人成群**：你一个人，配一支 Agent 编队。它们独立工作区、独立 Session、并行推进，你只在关键节点点头。

**协同作战**：多人 + 多 Agent 一起干，上下文自动接力。

- **上下文自动注入**：建 Session 时，项目背景、历史 Issue、Memory、Skill、代码工作区都自动 snapshot 进去
- **结构化交接**：当前进展可以打包交给下一个人或 Agent
- **并行隔离**：不同任务在独立工作区跑，互不打架
- **权限与审计**：管理员能管项目可见性、用户组、读写执行权限，跨用户操作有审计日志

人类团队把脑子花在方向、决策、验收上；重复实现、调试、文档这类活交给 Agent。

</details>

<details>
<summary><b>👁️ [04] 鸟瞰全局：项目进度和成员表现一屏看清</b></summary>

管理员后台（`/admin`）能看到整张图：

**能看的东西：**

- 📊 **全局 stats**：总用户数、总 Session 数、活跃 Session 数、已完成数、归档数、消息总数
- 🤖 **Agent 后端状态**：tmux-codex / tmux-claude-code 是否连上
- 📈 **使用强度**：过去 5 小时的 prompt 数（按 backend 拆分）、最近 2 分钟的活跃 prompt
- 👥 **每个成员的 task stats**：session 数、活跃数、完成数、归档数、消息总数
- 🖥️ **所有 tmux session**：哪个用户、哪个项目、跑了多久、状态如何

**自动清理：** `inactive-tmux-cleaner` 会自动收掉 3 小时（完成态 10 分钟）没活动的 tmux session，防止僵尸进程占资源。

> 说白了：谁在跑、跑得勤不勤、卡在哪个 Session，admin 后台都能看见。基于这些原始 stats，"谁是产出王、谁没在动"自然就清楚了 —— 不需要系统主动贴标签。

</details>

<details>
<summary><b>🎯 [05] 模型自由：协议兼容即可接入</b></summary>

Mobius 的 Agent 后端走两条路：

- **Claude 协议**（`tmux-claude-code`）：通过 `ANTHROPIC_BASE_URL` 可以指向任何 Anthropic 兼容端点
- **Codex 协议**（`tmux-codex`）：走 OpenAI Codex CLI

**实际能跑的：**

| 用途 | 协议 | 可接入示例 |
|---|---|---|
| Agent Session | Anthropic | 官方 Claude / Z.AI 的 GLM-5.2 / OpenRouter / 任何兼容代理 |
| Agent Session | OpenAI Codex | 官方 Codex |
| 小莫助理 | OpenAI Chat | GLM-5.2 / DeepSeek / OpenAI / Ollama / vLLM / 任何兼容端点 |

**管理员后台**还可以导入多个 Claude / Codex 渠道（不同 key、不同代理），建 Session 时选。

```bash
# 切换模型 = 改 .env 里的几个变量
ANTHROPIC_AUTH_TOKEN=sk-...
ANTHROPIC_BASE_URL=https://api.z.ai/api/anthropic  # 或官方 Anthropic
ASSISTANT_API_BASE=https://api.z.ai/api/paas/v4     # 小莫的 OpenAI 兼容端点
ASSISTANT_MODEL=glm-5.2
```

不绑死任何厂商，哪个便宜、哪个好用就切哪个。

</details>

<details>
<summary><b>🔬 [06] 深度科研：Blackboard + 算力节点 + 研究图谱</b></summary>

启用 Research 模式后，项目可以从"单 Agent 跑 Issue"切换成"Agent 编队跑课题"。

**核心组件：**

- **Chief Researcher + Research Assistants**：分工跑子课题，异步通过 Blackboard 协作
- **Research Graph**：自动生成 `research-graph.yml`，可视化每个子课题的状态（in_progress / completed / failed / successful）
- **aimux 远程算力**：通过 SSH 纳管远程主机，注册节点 → 测试连接 → 探测硬件 → 分发任务。适合需要远端 GPU / 大内存的科研场景
- **结果落盘**：研究产出（论文、图、笔记）沉淀在项目目录的 `.imac/blackboard/<research_id>/` 下

**典型流程：**

```
1. 项目启用 Research
2. 创建 Research，给一个课题描述
3. 系统拉起 Chief + N 个 Assistants（在各自工作站里跑）
4. 每一步都写 Blackboard
5. 研究图谱实时更新
6. Chief 收敛，输出最终成果
```

适合：技术选型、论文综述、复杂调研、需要远程算力的实验。一句话出文章这件事，目前还做不到，但课题级别的协作调研已经能用。

</details>

<details>
<summary><b>🧩 [07] 扩展系统：独立前端 + 独立后端，不动主代码</b></summary>

每个扩展都是一个完整的小应用，可以独立开发、独立部署：

- 🎨 **独立前端**：`mobius/extension/<name>/frontend/`，自己跑自己的 Vite / React
- ⚙️ **独立后端**：通过 Mobius backend 的 `/ext/<name>/` 统一转发，进程隔离
- 💾 **独立数据**：`${CORE_DATA_PATH}/extension/<name>/`
- 🔄 **构建管线**：`extension-build-pipeline` 自动 npm install + build
- 🗓️ **调度器**：`extension-scheduler` 支持定时任务

**仓库里实际带了的扩展（16 个）：**

| 类型 | 扩展 |
|---|---|
| 📊 生产力 | `ppt-maker`、`jsoncrack`（JSON 可视化）、`finance-news-wall`（财经新闻墙） |
| 📚 研究 / 阅读 | `arxiv`（论文阅读）、`security-audit-report` |
| 🎮 小游戏 | `flappy-bird-3d`、`pacman`、`virtual-pet` |
| 🌌 3D / 仿真 | `dot-logo-3d`、`threebody-sim`（三体仿真）、`traffic-light-plc` |
| 🎉 Demo | `birthday-invite`、`chatgpt`、`project-yongle` |
| 📱 多端 | `momo-mobile` |
| 🏠 Mobius 自己 | `mobius-home`（官网门户） |

每一个都是真实可跑的应用，能直接拿来做二次开发参考。

</details>

<details>
<summary><b>💬 [08] 智能小莫：知道你在哪个页面的助理</b></summary>

小莫是全局浮动助理。**不是 Project，不是 Issue** —— 是每个用户的持久化 Agent Session。它走 OpenAI 兼容协议，可以接 GLM-5.2、DeepSeek、OpenAI、Ollama 等任何模型。

**它能干什么：**

- 📍 **读页面状态**：当前路由、当前 Project / Issue / Session、页面上可见的列表，小莫都看得到
- 🔍 **搜索你的项目和任务**
- ✅ **创建 Project / Issue / Session**（信息够了就直接建）
- 🤔 **给候选方案**：含糊请求先给 2-4 个可点击选项，不瞎猜
- 🛠️ **跑"小莫动作"**：通过 HTTP Endpoint 调后端，建任务、改 Memory、加 Skill 都行
- 🔄 **改进 Mobius 自己**：你说"我想让 Mobius 怎么怎么样"，小莫会判断是不是要改 Mobius 主体，如果是，会在自迭代项目里提 Issue + 建 Session（小莫自己不写代码，开任务让其他 Agent 干）

**边界：** 小莫能开 Session，但不会自动启动业务 Agent —— 正式执行还得你点确认。

</details>

---

## 🧱 工作模型

```
  ┌──────────┐    ┌──────────┐    ┌──────────┐
  │ PROJECT  │ ─▶ │  ISSUE   │ ─▶ │ SESSION  │
  │ 上下文   │    │ 目标 &   │    │ 一次真实 │
  │ 容器     │    │ 验收标准 │    │ Agent 执行│
  └──────────┘    └──────────┘    └──────────┘
       ▲                                │
       │      ┌──────────────┐          │
       └──────│  沉淀回流     │◀─────────┘
              └──────────────┘
```

> ⚠️ **快照保证**：建 Session 时，当前 Issue、项目上下文、Skill、Memory 全部冻结成快照。后面全局配置怎么变，已经创建的 Session 都不受影响。

| **Memory（记忆）** | **Skill（技能）** | **Research（科研）** |
|:---:|:---:|:---:|
| 🔑 高频、易变的环境信息 | 🛠️ 稳定、可复用的技艺 | 🔬 多阶段调研 |
| 启动命令、SSH、密钥位置 | 调试流程、扩展开发规范 | Chief + Assistants |

---

## 💬 小莫助理

小莫的具体能力已经在 **[能力 08](#-08-智能小莫知道你在哪个页面的助理)** 里讲过了，这里补充它的工作模式：

- 第一次打开小莫要配模型、Skill、Memory，配完之后所有对话都进同一个持久 Session
- 前端定时拉小莫的消息和状态
- 小莫走 OpenAI 兼容协议，**只能开任务、不能自己改业务代码**

<details>
<summary><b>📍 引导系统（三条 Demo 路线）</b></summary>

引导系统基于 Driver.js + 稳定的 `data-tour` 标记，根据路由和弹窗状态分段运行。

1. 🎂 **生日邀请页 Demo**：首次登录自动触发，带你走完 Project → Issue → Session 的最小闭环
2. 📥 **导入已有项目 Demo**：用公开 TodoMVC 演示怎么把已有代码塞进 Mobius
3. 🧠 **Memory / Skill / 远程算力 Demo**：演示项目级上下文配置

> **当前状态**：生日 Demo 接到首次登录流程；另外两条路线代码骨架已经在了（状态模型 + 事件监听），但显式 UI 入口还没接到小莫面板上。

</details>

---

## 🚀 快速开始

### 🟢 方式一：容器（推荐）

```bash
git clone https://github.com/nutshellai-tech/mobius.git && cd mobius

# 阶段 1：构建 base 镜像（只装环境，不含代码）
docker build -t imac-mobius-base:latest -f deploy/Dockerfile .

# 阶段 2：构建执行镜像（拷贝代码）
docker build -t imac-mobius-exe:latest .

# 启动
docker compose up
```

### 🟡 方式二：本地开发

依赖：`tmux`、Node.js `18+`、Python 3、至少一个 Agent CLI（Codex 或 Claude Code）

```bash
git clone https://github.com/nutshellai-tech/mobius.git
cd mobius
cp .env.example .env  # 填 API Key、JWT_SECRET、本机路径
```

首次启动前初始化管理员（对应 `.env` 里的 `IMAC_BOOTSTRAP_USERS`）：

```bash
cd mobius
IMAC_BOOTSTRAP_USERS="admin:your-password:admin:Administrator" \
  DB_PATH=<data>/mobius.db \
  WORKSPACE_ROOT=<data>/workspace \
  node scripts/bootstrap-users.js
```

> 这一步在容器部署时由 `docker-entrypoint.sh` 自动跑；本地开发要手动跑一次。格式：`id:password:role:display_name`，多个用户用 `;` 分隔。

回到根目录启动：

```bash
cd ..
python3 start.py --detach
```

| 🌐 服务 | URL |
|---|---|
| Web 前端 | `localhost:45616` |
| 后端 API | `localhost:45614` |
| aimux bridge | `localhost:45615` |
| VS Code Web | `localhost:45617` |

---

## 📈 路线图

> ℹ️ 截至 2026-06，最近落地的：

- ✅ 小莫升级为持久化用户级 Agent Session（支持配模型、Skill、Memory）
- ✅ 小莫前端推送页面状态，后端基于状态调工具
- ✅ 小莫能识别"想改 Mobius 本身"的请求，在自迭代项目里开 Issue + Session
- ✅ 引导系统从单一生日 Demo 扩展到三条路线（生日 / 导入项目 / 上下文配置）
- ✅ 引导支持跨路由分段、表单预填、上下文快照说明、Session 完成推进
- ⚠️ 只有生日 Demo 接到首次登录；另外两条路线还需要补显式 UI 入口
- 🔜 Research、扩展项目、特殊应用也要在总介绍里覆盖到

---

## 📜 许可证

> ⚠️ **Mobius 用自定义的 Source-Available 许可证。**
>
> 源码可用于学习、研究、教育、个人项目、内部评估等非商业用途；**任何商业用途都需要单独授权**。完整条款见 [LICENSE](https://github.com/nutshellai-tech/mobius/blob/main/LICENSE)。

💼 商业授权联系：`business@nutshellai.cn`

---

<div align="center">

```
╔═══════════════════════════════════════════════════════╗
║  ✧  Mobius 用 Mobius 改 Mobius.                       ║
║  ✧  你想到的，它能长出来。                             ║
╚═══════════════════════════════════════════════════════╝
```

### 🌐 [mobius.nutshellai.cn](https://mobius.nutshellai.cn/)

<img src="https://capsule-render.vercel.app/api?type=venom&color=gradient&customColorList=12,14,16,18,20&height=120&section=footer&fontSize=0" alt="Footer" />

</div>
