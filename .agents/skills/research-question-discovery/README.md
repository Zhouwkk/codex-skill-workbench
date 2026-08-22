# Research Question Discovery 使用指南

Research Question Discovery 是一个帮助研究者把模糊科研直觉逐步加工成高质量 Research Question 的 Codex Skill。它以第一性原理拆解寻找更基础的解释，用科学压力测试和定向证据检索挑战解释，并把直觉更新权保留给用户。

它最终交付的是：

```text
Candidate Research Question + 简洁的认知演化记录
```

它不判断问题是否新颖、能否发表、适合什么 venue，也不负责最终方法和完整实验设计。

## 安装

Skill 源码位于：

```text
.agents/skills/research-question-discovery/
```

在本仓库目录中启动 Codex 时可以直接发现它。也可以使用 `$skill-installer` 从下面的 GitHub 目录安装为个人 Skill：

```text
https://github.com/Zhouwkk/codex-skill-workbench/tree/main/.agents/skills/research-question-discovery
```

本仓库只维护 Skill 源码，不会自动复制或链接到用户级目录。

## 调用示例

从一个尚未成形的直觉开始：

```text
$research-question-discovery 我感觉多智能体系统中的很多通信并没有真正改善最终决策，但我还说不清问题本质在哪里。
```

从一个较明确的因果判断开始：

```text
$research-question-discovery 我怀疑多智能体协作的主要瓶颈不是没有产生有价值的信息，而是接收者没有利用已经产生的信息。请从这个直觉开始挑战我。
```

继续已有讨论：

```text
$research-question-discovery 继续上一轮。我的当前直觉是：在 compute-matched 条件下，协作收益取决于互补信息能否改变接收 agent 的决策。当前未解决的是信息生成不足与信息利用失败如何区分。
```

如果暂时不希望检索证据，可以明确说明：

```text
$research-question-discovery 先只做第一性原理拆解和科学压力测试，Evidence Check 暂时标记为 Pending。
```

## 运行方式

Skill 会根据当前认知状态选择下一步，而不是机械地一次问完所有问题。普通对话通常只推进一个关键判断：

- 当前直觉究竟声称了什么；
- 哪个因素是必要机制，哪个只是具体表现；
- 候选基础解释能否重新解释原现象；
- 当前解释最强的替代解释、边界或混淆因素是什么；
- 什么证据能够区分它们；
- 用户在看到推理和证据后是否保留、修正或暂缓判断。

Evidence Check 是围绕当前 hypothesis 定向查证，不是系统综述，也不是 novelty search。即使现有证据很少，Skill 也只会把状态标记为 Under-explored，不会据此声称问题具有创新性。

## 完成输出

只有当问题能够带来明确的 understanding gain、触及机制或决定条件、具有可区分的证据路径，并且继续向下拆解的收益已经较低时，Skill 才会输出 Candidate Research Question。

输出还会说明：

- 该问题为何能增加理解；
- 它背后的机制张力或边界；
- 什么观察能够区分当前解释；
- 证据目前是充分、混合、有条件、探索不足还是尚未检查；
- novelty 和 publishability 尚未评估。

## 当前边界

v0.1 是 instruction-only Skill，没有脚本、模板资产或持久状态文件。最好在同一对话中完成多轮推理；换到新对话时，提供上一次的 Intuition、Core Challenge、Hypothesis、Evidence 和 User Revision 即可恢复。
