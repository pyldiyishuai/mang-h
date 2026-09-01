# 社区插件集成

[English](community-plugins.md) | 中文

本页列出可以在不修改核心运行时的前提下评估的高星 DeepSeek Harness 插件。每项都记录仓库、发布的包或 bundle，以及符合当前 profile 架构的接入方式。星数仅作参考，会随时间变化。

## 插件市场

[dsh-market](https://github.com/dsh-market/dsh-market)（审查时 2,823 stars）发布 `dshmarket` Web bundle，提供可搜索目录、安装和更新、热启用或禁用，以及社区 bundle 的加载诊断。

将它作为可选的 Web profile 层安装：

```sh
dsh plugin --profile web add dshmarket
```

市场会以 Harness 进程的权限安装第三方代码。安装前请审查每个插件；对于持有生产凭据的 profile，不要启用自动重启或自动安装。

## Agent Teams

[NanmiCoder/dsh-agent-teams](https://github.com/NanmiCoder/dsh-agent-teams)（审查时 1,198 stars）发布 `@nanmicoder/dsh-agent-teams`（`0.1.14`）。它提供持久队友、依赖感知任务、直接消息、质量门禁和 Web 活动面板。

请在一次性 Web profile 中安装它，用于和仓库现有的实验性 Agent Teams 包进行对照：

```sh
dsh plugin --profile web add @nanmicoder/dsh-agent-teams@latest
```

该插件拥有自己的任务和成员模型。在完成工具名称和持久化交互测试前，不要与 `@deepseek-ai/dsh-experimental-agent-team-profile` 同时启用。

## 后续评估

后续条目将覆盖上下文分析、视觉路由、侧边栏工作台和模型路由 preset。它们的依赖和 profile 影响不同，因此保持独立评估。
