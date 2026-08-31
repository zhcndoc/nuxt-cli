---
title: "nuxt typecheck"
description: typecheck 命令运行 vue-tsc 或 Golar 来检查整个应用中的类型
links:
  - label: Source
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/typecheck.ts
    size: xs
---

<!--typecheck-cmd-->
```bash [Terminal]
npx nuxt typecheck [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--dotenv=<path>...] [-e, --extends=<layer-name>...] [--checker=<vue-tsc|golar>] [-b, --build]
```
<!--/typecheck-cmd-->

`typecheck` 命令运行 [`vue-tsc`](https://github.com/vuejs/language-tools/tree/master/packages/tsc) 或 [Golar](https://golar.dev/languages/vue/) 来检查整个应用中的类型。如果两者都未安装，系统会提供适用于你的包管理器的安装命令。

## 参数

<!--typecheck-args-->
| Argument  | Description                                          |
|-----------|------------------------------------------------------|
| `ROOTDIR` | Nuxt 项目的根目录（默认：。） |
<!--/typecheck-args-->

## 选项

<!--typecheck-opts-->
| Option                               | Default | Description                                                                                                       |
|--------------------------------------|---------|-------------------------------------------------------------------------------------------------------------------|
| `--cwd=<directory>`                  |         | 指定 Nuxt 项目的根目录                                                                   |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时的日志级别                                                                                      |
| `--dotenv=<path>...`                 |         | 要加载的 `.env` 文件路径，相对于根目录。可以重复指定，后面的文件优先级更高。 |
| `-e, --extends=<layer-name>...`      |         | 从 Nuxt 层扩展                                                                                          |
| `--checker=<vue-tsc\|golar>`         |         | 要使用的类型检查器                                                                                               |
| `-b, --build`                        |         | 在构建模式下进行类型检查，使用 TypeScript 项目引用（默认会自动检测）                 |
| `--no-build`                         |         | 不使用 TypeScript 项目引用进行类型检查                                                                  |
<!--/typecheck-opts-->

## 类型检查器

`--checker golar` 会运行 [Golar](https://golar.dev/languages/vue/)，而不是 `vue-tsc`，并且项目中的 `golar.config.*` 文件会使其成为默认检查器。如果缺少配置文件，系统会为你写入一个。

## 构建模式

解决方案样式的 `tsconfig.json`（只列出 `references` 的配置文件）会自动在构建模式下进行类型检查。`--build` 会强制启用构建模式，而 `--no-build` 会将其关闭。

::note
此命令会将 `process.env.NODE_ENV` 设置为 `production`。要覆盖此设置，请在 [`.env`](/docs/directory-structure/env) 文件中定义 `NODE_ENV`，或将其作为命令行参数传入。
::

::read-more{to="/docs/guide/concepts/typescript#type-checking"}
详细了解如何在构建或开发时启用类型检查。
::
