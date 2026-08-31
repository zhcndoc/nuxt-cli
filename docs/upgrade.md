---
title: "nuxt upgrade"
description: upgrade 命令将 Nuxt 升级到最新版本
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/upgrade.ts
    size: xs
---

<!--upgrade-cmd-->
```bash [Terminal]
npx nuxt upgrade [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--dedupe] [-f, --force] [-ch, --channel=<stable|nightly|v3|v4|v4-nightly|v3-nightly>]
```
<!--/upgrade-cmd-->

`upgrade` 命令将 Nuxt 升级到最新版本。它会更新你的 [`package.json`](/docs/directory-structure/package) 中的版本，使用你的包管理器重新安装依赖项，并移除构建缓存。

`--channel` 用于选择要升级到的版本：`stable` 表示最新发布版本，`v3` 或 `v4` 表示保持在相应的大版本，`nightly`、`v3-nightly` 或 `v4-nightly` 表示 nightly 发布频道。

`--force` 会从头重新创建锁文件和 `node_modules`，`--dedupe` 则会在之后对依赖项进行去重，前提是包管理器支持此功能。

固定到 pnpm catalog（`"nuxt": "catalog:"`）的依赖项会在 `pnpm-workspace.yaml` 中升级，因为实际版本位于该文件中，而不是 `package.json` 中。

## 参数

<!--upgrade-args-->
| Argument  | Description                                          |
|-----------|------------------------------------------------------|
| `ROOTDIR` | Nuxt 项目的根目录（默认：.） |
<!--/upgrade-args-->

## 选项

<!--upgrade-opts-->
| Option                                                             | Default  | Description                                         |
|--------------------------------------------------------------------|----------|-----------------------------------------------------|
| `--cwd=<directory>`                                                |          | 指定 Nuxt 项目的根目录     |
| `--logLevel=<silent\|info\|verbose>`                               |          | 指定构建时的日志级别                        |
| `--dedupe`                                                         |          | 升级后对依赖项进行去重                 |
| `-f, --force`                                                      |          | 强制升级以重新创建锁文件和 node_modules |
| `-ch, --channel=<stable\|nightly\|v3\|v4\|v4-nightly\|v3-nightly>` | `stable` | 指定要从中安装的频道                   |
<!--/upgrade-opts-->
