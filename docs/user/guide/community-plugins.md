# Community plugin integrations

English | [中文](community-plugins.zh.md)

This page lists high-star DeepSeek Harness plugins that can be evaluated without changing the core runtime. Each entry names the repository, package or bundle, and profile integration route. Stars are indicative only and change over time.
## Plugin market

[dsh-market](https://github.com/dsh-market/dsh-market) (2,823 stars at review time) publishes the `dshmarket` Web bundle with catalog, install, update, enable/disable, and load diagnostics.
Use it as an optional Web profile layer:

```sh
dsh plugin --profile web add dshmarket
```
The market installs third-party code with the Harness process permissions. Review every plugin before installation, and do not enable automatic restart or installation in profiles holding production credentials.
## Agent Teams

[NanmiCoder/dsh-agent-teams](https://github.com/NanmiCoder/dsh-agent-teams) (1,198 stars at review time) publishes `@nanmicoder/dsh-agent-teams` (`0.1.14`) with durable teammates, dependency-aware tasks, direct messages, quality gates, and a Web activity panel.
Install it in a disposable Web profile for comparison with the repository's experimental Agent Teams packages:

```sh
dsh plugin --profile web add @nanmicoder/dsh-agent-teams@latest
```
The plugin owns its task and roster model. Do not enable it with `@deepseek-ai/dsh-experimental-agent-team-profile` until tool-name and persistence interactions are tested.
## Context analysis

[bowenliang123/dsh-context](https://github.com/bowenliang123/dsh-context) (1,178 stars at review time) publishes `dsh-context` (`0.38.3`, Apache-2.0). Its Web dashboard explains prompt composition, token and timing usage, context trends, file activity, and the live agent network.
Install it as an optional Web bundle:

```sh
dsh plugin --profile web add dsh-context@latest
```
The plugin reads session and token-meter projections; it does not replace the session log or compaction provider. Verify its version against the running Harness release before long-lived use.
## Vision routing

[ysr666/dsh-vision-router](https://github.com/ysr666/dsh-vision-router) (1,031 stars at review time) publishes `dsh-vision-router` (`2.0.1`, MIT) with grounding, crops, pixel diffs, OCR, SVG tracing, and screenshots while text turns remain on the configured reasoning model.
Install it only where attachment and image-capable LLM services are already present:

```sh
dsh plugin --profile web add dsh-vision-router@latest
```
The plugin uses native dependencies such as `puppeteer-core` and `potrace`, and may call external vision routes. Review network and image-retention settings before enabling it.
## Sidebar workbench

[omdsh-dev/DSH-better-sidebar](https://github.com/omdsh-dev/DSH-better-sidebar) (3,120 stars at review time) publishes `dsh-better-sidebar` (`0.17.1`, MIT) with file viewers, an editor, terminal, Git tools, browser tabs, and registration APIs.
Install it in a Web profile when those panels are needed:

```sh
dsh plugin --profile web add dsh-better-sidebar@latest
```
The bundle includes large browser dependencies and native `node-pty`. Check build-script approval on the target platform, and keep its sidebar registration separate from built-in conversation slots until compatibility is verified.
## Model-routing presets

[yjh051108/dsh-routing-suite](https://github.com/yjh051108/dsh-routing-suite) (6,967 stars at review time) combines `dsh-super-injector` (`0.3.3`, BSD-3-Clause) with `dsh-router-standard` (`0.3.0`, MIT). It routes tasks to personas, supports staged tool disclosure, and exposes routing status tools.
Treat it as an experimental profile overlay. Install the injector first, then copy one preset directory as described upstream:

```sh
dsh plugin --profile web add github:yjh051108/dsh-routing-suite
```
The injector changes runtime composition and presets add prompt sections. Test with a disposable profile, inspect `dsh --profile web --dump-config`, and measure routing and token costs before unattended production use.
## Integration rules

These projects are optional third-party layers, not default bundles. Their licenses, dependencies, network calls, native build steps, and persistence formats remain owned upstream. Use the existing MCP client for generic MCP servers, and prefer profile patches over source edits.
