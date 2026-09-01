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

## 后续评估

后续条目将覆盖 Agent Teams、上下文分析、视觉路由、侧边栏工作台和模型路由 preset。它们的依赖和 profile 影响不同，因此保持独立评估。
