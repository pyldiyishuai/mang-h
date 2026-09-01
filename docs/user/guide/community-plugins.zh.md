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

## 上下文分析

[bowenliang123/dsh-context](https://github.com/bowenliang123/dsh-context)（审查时 1,178 stars）发布 `dsh-context`（`0.38.3`，Apache-2.0）。它的 Web 仪表板展示提示词组成、token 和耗时、上下文趋势、文件活动以及实时 Agent 网络。

将它作为可选 Web bundle 安装：

```sh
dsh plugin --profile web add dsh-context@latest
```

该插件读取 session 和 token-meter projection，不会替换 session log 或 compaction provider。在长期 profile 中启用前，请将包版本与运行中的 Harness 版本核对。

## 视觉路由

[ysr666/dsh-vision-router](https://github.com/ysr666/dsh-vision-router)（审查时 1,031 stars）发布 `dsh-vision-router`（`2.0.1`，MIT）。它增加按需视觉工具，例如定位、裁剪、像素差异、OCR、SVG 描摹和截图，同时让文本轮次继续使用配置的推理模型。

仅在已经包含 attachment 和支持图片的 LLM service 的 profile 中安装：

```sh
dsh plugin --profile web add dsh-vision-router@latest
```

该插件使用 `puppeteer-core`、`potrace` 等原生依赖，并可能调用外部视觉路由。启用前请审查网络和图片保留设置，并确认每个图片结果都遵守 Harness 的 attachment 与 session 策略。

## 侧边栏工作台

[omdsh-dev/DSH-better-sidebar](https://github.com/omdsh-dev/DSH-better-sidebar)（审查时 3,120 stars）发布 `dsh-better-sidebar`（`0.17.1`，MIT）。它增加可扩展 Web 侧边栏，包含文件查看器、编辑器、终端、Git 工具、浏览器标签，以及供其他插件注册的 API。

需要这些面板时，在 Web profile 中安装：

```sh
dsh plugin --profile web add dsh-better-sidebar@latest
```

该 bundle 包含较大的浏览器依赖和原生 `node-pty` 包。在目标平台上请留意构建脚本授权提示，并在确认兼容性前，让它的侧边栏注册与内置 conversation slot 保持隔离。

## 模型路由 preset

[yjh051108/dsh-routing-suite](https://github.com/yjh051108/dsh-routing-suite)（审查时 6,967 stars）将 `dsh-super-injector`（`0.3.3`，BSD-3-Clause）与 `dsh-router-standard` preset（`0.3.0`，MIT）组合在一起。该 preset 按任务将请求路由到不同 persona，支持分阶段工具披露，并提供路由状态工具。

请把它当作实验性 profile overlay，而不是核心依赖。先安装 injector，再按照上游项目说明复制一个 preset 目录：

```sh
dsh plugin --profile web add github:yjh051108/dsh-routing-suite
```

injector 会改变运行时组合，preset 会增加 prompt section。请在一次性 profile 中测试，检查 `dsh --profile web --dump-config` 的结果，并在测量路由决策和 prompt token 成本前，不要在无人值守的生产会话中启用。

## 集成规则

这些项目都是可选的第三方层，不属于默认 bundle。它们的许可证、依赖范围、网络调用、原生构建步骤和持久化格式仍由上游仓库负责。通用 MCP server 使用现有 MCP client；评估插件时优先使用 profile patch，不要修改包源码。
