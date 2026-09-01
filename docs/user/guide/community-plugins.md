# Community plugin integrations

English | [中文](community-plugins.zh.md)

This page lists high-star DeepSeek Harness plugins that can be evaluated without changing the core runtime. Each entry names the repository, the package or bundle it publishes, and the integration route that matches the current profile architecture. Stars are indicative only and change over time.

## Plugin market

[dsh-market](https://github.com/dsh-market/dsh-market) (2,823 stars at review time) publishes the `dshmarket` Web bundle. It provides a searchable catalog, install and update actions, hot enable/disable controls, and load diagnostics for community bundles.

Use it as an opt-in Web profile layer:

```sh
dsh plugin --profile web add dshmarket
```

The market installs third-party code with the permissions of the Harness process. Review each plugin before installing it, and do not enable automatic restart or installation in a profile that holds production credentials.

## Agent Teams

[NanmiCoder/dsh-agent-teams](https://github.com/NanmiCoder/dsh-agent-teams) (1,198 stars at review time) publishes `@nanmicoder/dsh-agent-teams` (`0.1.14`). It adds durable teammates, dependency-aware tasks, direct messages, quality gates, and a Web activity panel.

Install it in a disposable Web profile for comparison with the repository's experimental Agent Teams packages:

```sh
dsh plugin --profile web add @nanmicoder/dsh-agent-teams@latest
```

The plugin owns its own task and roster model. Do not enable it together with `@deepseek-ai/dsh-experimental-agent-team-profile` until tool-name and persistence interactions have been tested.

## Context analysis

[bowenliang123/dsh-context](https://github.com/bowenliang123/dsh-context) (1,178 stars at review time) publishes `dsh-context` (`0.38.3`, Apache-2.0). Its Web dashboard explains prompt composition, token and timing usage, context trends, file activity, and the live agent network.

Install it as an optional Web bundle:

```sh
dsh plugin --profile web add dsh-context@latest
```

The plugin reads the session and token-meter projections; it does not replace the session log or compaction provider. Verify its package version against the running Harness release before enabling it in a long-lived profile.

## Further evaluation

The next entries cover context analysis, vision routing, the sidebar workbench, and model-routing presets. They remain separate because each has different dependencies and profile effects.
