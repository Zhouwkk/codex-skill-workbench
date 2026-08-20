# Skill Workbench

用于创建、测试和维护个人 Codex skills 的本地项目。

## 目录

```text
.agents/skills/   可被 Codex 自动发现的项目级 skills
notes/            跨 skill 的设计记录和索引
AGENTS.md         本项目的协作与质量约定
```

每个 skill 都是 `.agents/skills/<skill-name>/` 下的独立目录，至少包含
`SKILL.md`。按需增加 `agents/openai.yaml`、`scripts/`、`references/` 或
`assets/`，不要预先创建无用途的空目录。

## 创建一个 skill

在本项目中对 Codex 说：

> 使用 `$skill-creator`，在当前项目的 `.agents/skills/<skill-name>` 中创建一个 skill。

请始终明确目标路径，避免把仍在开发的 skill 直接写入用户级全局目录。

## 推荐流程

1. 在 `notes/skill-index.md` 写下目标、触发场景和当前状态。
2. 使用 `$skill-creator` 创建或修改 skill。
3. 验证 frontmatter、目录结构以及需要执行的脚本。
4. 用真实请求测试触发和输出质量。
5. 提交到 Git；成熟后再决定是否链接到用户级 skills 目录或打包为 plugin。

