# Skill Workbench

用于创建、测试、分享和维护个人 Codex skills 的项目。

## 已包含的 Skill

- [`research-os`](.agents/skills/research-os/README.md)：用本地状态文档管理科研主线、远程实验、每日推进与每周复盘；查看安装方法、使用示例与数据边界。
- [`blog-as-learning`](.agents/skills/blog-as-learning/README.md)：通过“探 → 学 ↔ 讲 → 写”暴露认知缺口、形成自己的理解，并把理解重构成面向读者的博客。

Skill 源码可以上传到 GitHub；个人研究状态、实验记录和服务器信息不属于本仓库，也不应提交到这里。

## 目录

```text
.agents/skills/   可被 Codex 自动发现的项目级 skills
notes/            跨 skill 的设计记录和索引
AGENTS.md         本项目的协作与质量约定
```

每个 skill 都是 `.agents/skills/<skill-name>/` 下的独立目录，至少包含
`SKILL.md`。按需增加 `agents/openai.yaml`、`scripts/`、`references/` 或
`assets/`，不要预先创建无用途的空目录。准备分享的 skill 还应维护独立的
`README.md`，向使用者说明安装、初始化、典型用法和必要的数据边界。

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

## 使用仓库中的 Skill

在 Codex 中打开本仓库时，`.agents/skills/` 下的 skills 会作为项目级 skills 被发现。要在其他项目中使用，可以将目标 skill 复制到那个项目的 `.agents/skills/`，或安装到个人 skills 目录。
