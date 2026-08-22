# Research OS 使用指南

Research OS 是一个面向科研工作的 Codex Skill。它不把科研管理成普通待办清单，而是围绕研究状态、当前问题、反馈和下一步行动，帮助你安排每周重点、选择今天的 Primary，并在实验结束后更新判断。

它尤其适合下面的工作方式：

- 同时推进多个科研课题，需要区分 Push、Keep-alive 和暂缓项目；
- 代码、数据和实验运行在远程服务器，本地只维护研究判断与索引；
- 希望几天后重新进入项目时，能快速恢复上下文；
- 希望通过每日收尾和每周复盘逐步改进自己的科研工作方式。

## 1. 安装

最简单的方式是在 Codex 中调用 `$skill-installer`，并让它从这个 GitHub 目录安装：

```text
使用 $skill-installer，从下面的 GitHub 地址安装 research-os：
https://github.com/Zhouwkk/codex-skill-workbench/tree/main/.agents/skills/research-os
```

也可以克隆整个仓库。在仓库目录中启动 Codex 时，Codex 会自动发现 `.agents/skills/research-os`。

如果安装后没有出现在 Skills 列表中，重启 Codex。

## 2. 准备本地状态目录

Research OS 把本地 Mac 目录当作研究的控制中心。你可以选择任意位置，例如：

```text
~/Documents/Research-OS
```

第一次使用时，在 Codex 中说：

```text
使用 $research-os，在 ~/Documents/Research-OS 初始化我的科研状态目录。
现在还没有项目信息，只创建第一版 Dashboard 和必要的基础文件。
```

初始化后，目录会按需形成下面的结构：

```text
Research-OS/
├── Dashboard.md       # 日常入口和当前总览
├── projects/          # 每个课题的当前研究状态
├── sessions/          # 有证据和状态变化的研究 session
├── weekly/            # 每周控制卡
├── reviews/           # 周复盘
├── inbox.md           # 工作中临时捕获的想法
└── rules.md           # 稳定规则与正在测试的工作方式
```

不需要手动把所有文件一次建完。Research OS 会根据当前操作创建需要的文件。

## 3. 添加第一个课题

你可以用自然语言描述课题，不必先整理成固定表格：

```text
使用 $research-os，把下面这个课题加入我的 Research OS：

课题名称：……
目前已经确认：……
当前最不确定的是：……
我下一步准备做：……
截止时间或合作约束：……
```

如果课题运行在服务器上，可以补充远程定位信息：

```text
这个项目在远程服务器运行：
- SSH alias：gpu-a
- 项目目录：/data/projects/example
- 调度系统：Slurm
- 当前实验：job 18432，用于比较两个配置
- 结果位置：/data/projects/example/outputs/run-07

请把这些信息记录为 Remote Context，不要复制代码、数据或原始日志到本地。
```

不要提供密码、私钥、访问令牌或其他秘密信息。

## 4. 日常怎么使用

你不需要记忆复杂命令。直接描述当前需求，Codex 会选择合适的 Research OS 工作模式。

### 安排本周

```text
使用 $research-os，根据当前所有项目状态安排这一周。
我这周有三天可以完整做研究，周四要向合作者汇报。
```

Research OS 会建议最多两个 Push，必要时保护一个 Keep-alive，并为每条主线定义本周希望发生的研究状态变化。

### 决定今天先做什么

```text
使用 $research-os，帮我确定今天的 Primary、Secondary 和 Fallback。
我今天上午精力较好，但下午只有零散时间。
```

### 开始一次研究 session

```text
使用 $research-os，我现在开始今天的 Primary。请确认 Current Question、Expected Feedback 和第一个可执行动作。
```

### 工作中出现新想法

```text
我在做 Primary 时想到一个新的数据增强方案。请判断它应该 Stay、Capture 还是 Interrupt。
```

### 实验结束后更新状态

```text
服务器上的 job 18432 已完成。
主要结果：……
与预期相比：……
结果文件：/data/projects/example/outputs/run-07/metrics.json
观察时间：2026-08-22 16:30

使用 $research-os 记录这次反馈，判断它对当前假设的影响，并更新下一步。
```

只有“任务跑完了”而没有结果解释时，Research OS 会把它记录为执行状态变化，不会虚构研究结论。

### 每日收尾

```text
使用 $research-os 帮我做今天的收尾：同步项目状态、处理 Inbox，并留下明天可以直接开始的 Next Action。
```

### 每周复盘

```text
使用 $research-os 做本周复盘。重点检查哪些研究状态真正发生了变化、系统哪里失灵，以及下周只测试哪一条规则改进。
```

## 5. 本地与服务器如何分工

Research OS 使用“两层结构”：

```text
本地控制层
  Dashboard、研究问题、结论、计划、复盘、远程定位信息
                         ↓
远程执行层
  代码、数据、环境、实验任务、原始日志、模型与大型结果
```

默认情况下，你在服务器上运行或检查实验，然后把最小必要反馈告诉 Codex。Research OS 会记录：

- 执行状态：Pending、Running、Completed 等；
- 研究反馈：结果支持、挑战、解决或意外改变了什么；
- 证据位置：服务器、版本、任务编号、结果路径和观察时间。

如果你希望 Codex 直接通过 SSH 检查某个任务或日志，需要在当次请求中明确授权，并指出服务器、项目路径和希望检查的对象。

## 6. 推荐的长期使用方式

把本地状态目录作为一个长期 Codex 项目。以后关于科研状态、实验反馈、项目想法、每日安排和周复盘，都可以在这个项目中继续沟通。

Research OS 会把信息分流到合适的位置：

- 已验证的判断进入 Project State；
- 一次 session 的证据进入 Session Record；
- 暂时偏离当前问题的想法进入 Inbox；
- 本周资源分配进入 Weekly Control Card；
- 重复出现的工作方式问题进入规则实验。

你始终保留最终决定权。Research OS 会给出默认建议，但不会替你判断一个研究方向是否值得继续或应该被另一个方向取代。

## 7. 数据与隐私边界

这个 GitHub 仓库只保存 Skill 本身。你的本地 Research OS 状态目录不需要放进本仓库，也不应因为使用这个 Skill 而自动上传。

建议始终遵守下面的边界：

- 不在研究状态文档中保存密码、密钥、令牌或凭证文件；
- 本地只保存研究所需的摘要和稳定定位信息；
- 大型数据、模型、日志和实验产物继续留在服务器；
- 在公开分享状态文档前，自行移除未公开课题信息和服务器定位信息。

## 8. 调用方式

你可以显式写出 `$research-os`，也可以直接提出与科研规划、研究状态恢复、远程实验跟踪或科研复盘相关的请求。Codex 可以根据 Skill 的描述自动选择它。首次使用和重要操作建议显式调用，便于确认正在使用正确的工作流。

更多关于 Codex Skills 的安装、发现与调用机制，可参阅 [OpenAI 官方文档](https://learn.chatgpt.com/docs/build-skills)。
