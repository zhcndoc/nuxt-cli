---
title: "nuxt upgrade"
description: upgrade 命令将 Nuxt 升级到最新版本
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/3.x/packages/nuxi/src/commands/upgrade.ts
    size: xs
---

<!--upgrade-cmd-->
```bash [Terminal]
npx nuxt upgrade [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--dedupe] [-f, --force] [-ch, --channel=<stable|nightly|v3|v4|v4-nightly|v3-nightly>]
```
<!--/upgrade-cmd-->

`upgrade` 命令将 Nuxt 升级到最新版本。

## 参数

<!--upgrade-args-->
| 参数          | 描述                                  |
|---------------|---------------------------------------|
| `ROOTDIR="."` | 指定工作目录（默认：`.`）             |
<!--/upgrade-args-->

## 选项

<!--upgrade-opts-->
| 选项                                                               | 默认值   | 描述                                                                               |
|--------------------------------------------------------------------|----------|------------------------------------------------------------------------------------|
| `--cwd=<directory>`                                                |          | 指定工作目录，此选项优先于 ROOTDIR（默认：`.`）                                   |
| `--logLevel=<silent\|info\|verbose>`                               |          | 指定构建时日志级别                                                                 |
| `--dedupe`                                                         |          | 升级后去重依赖项                                                                   |
| `-f, --force`                                                      |          | 强制升级以重新创建锁文件和 node_modules                                           |
| `-ch, --channel=<stable\|nightly\|v3\|v4\|v4-nightly\|v3-nightly>` | `stable` | 指定要从中安装的频道（默认：stable）                                              |
<!--/upgrade-opts-->
