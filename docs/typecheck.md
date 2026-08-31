---
title: "nuxt typecheck"
description: typecheck 命令运行 vue-tsc 或 Golar，以检查整个应用中的类型
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/3.x/packages/nuxi/src/commands/typecheck.ts
    size: xs
---

<!--typecheck-cmd-->
```bash [Terminal]
npx nuxt typecheck [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--dotenv] [-e, --extends=<layer-name>] [--checker]
```
<!--/typecheck-cmd-->

`typecheck` 命令运行 [`vue-tsc`](https://github.com/vuejs/language-tools/tree/master/packages/tsc) 或 [Golar](https://golar.dev/languages/vue/)，以检查整个应用中的类型。如果两者都未安装，系统会提示你安装其中一个；如果在非交互式终端中运行，则会显示安装说明。

## 参数

<!--typecheck-args-->
| 参数          | 描述                                    |
|---------------|----------------------------------------|
| `ROOTDIR="."` | 指定工作目录（默认：`.`） |
<!--/typecheck-args-->

## 选项

<!--typecheck-opts-->
| 选项                                | 默认值 | 描述                                                                             |
|--------------------------------------|---------|----------------------------------------------------------------------------------|
| `--cwd=<directory>`                  |         | 指定工作目录，其优先级高于 ROOTDIR（默认：`.`） |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时日志级别                                                     |
| `--dotenv`                           |         | 要加载的 `.env` 文件路径，相对于根目录                      |
| `-e, --extends=<layer-name>`         |         | 从 Nuxt 层扩展                                                         |
| `--checker` |         | 要使用的类型检查器（`vue-tsc` 或 `golar`）                                       |
<!--/typecheck-opts-->

::note
此命令会将 `process.env.NODE_ENV` 设置为 `production`。要覆盖此设置，请在 [`.env`](/docs/directory-structure/env) 文件中或作为命令行参数定义 `NODE_ENV`。
::

::read-more{to="/docs/guide/concepts/typescript#type-checking"}
详细了解如何在构建时或开发时启用类型检查。
::
