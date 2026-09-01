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

## Further evaluation

The next entries will cover Agent Teams, context analysis, vision routing, the sidebar workbench, and model-routing presets. They remain separate because each has different dependencies and profile effects.
