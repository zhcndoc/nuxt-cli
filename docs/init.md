---
title: "创建 Nuxt"
description: init 命令初始化一个全新的 Nuxt 项目
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/create-nuxt/src/init.ts
    size: xs
---

<!--init-cmd-->
```bash [Terminal]
npm create nuxt@latest [DIR] -- [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [-t, --template=<template-name>] [-f, --force] [--offline] [--preferOffline] [--install] [--gitInit] [--shell] [--packageManager=<npm|pnpm|yarn|bun|deno|aube|nub>] [-M, --modules=<module-names>] [--nightly=<dist-tag>]
```
<!--/init-cmd-->

`create-nuxt` 命令使用 [unjs/giget](https://github.com/unjs/giget) 初始化一个全新的 Nuxt 项目。它会询问要从哪个模板开始、是否安装模块以及使用哪个包管理器，然后安装依赖并打印接下来要运行的命令。

![npm create nuxt](/capture/output/nuxt-init.svg)

::note
`nuxt init` 已从 `@nuxt/cli` 中移除。请使用 `npm create nuxt@latest`，或使用包管理器对应的等效命令。
::

## 参数

<!--init-args-->
| 参数       | 描述         |
|------------|--------------|
| `DIR=""` | 项目目录 |
<!--/init-args-->

## 选项

<!--init-opts-->
| 选项                                                     | 默认值 | 描述                                                                          |
|------------------------------------------------------------|---------|--------------------------------------------------------------------------------------|
| `--cwd=<directory>`                                        | `.`     | 指定创建项目的目录                                       |
| `--logLevel=<silent\|info\|verbose>`                       |         | 指定构建时日志级别                                                         |
| `-t, --template=<template-name>`                           |         | 模板名称                                                                        |
| `-f, --force`                                              |         | 覆盖现有目录                                                          |
| `--offline`                                                |         | 强制离线模式                                                                   |
| `--preferOffline`                                          |         | 优先使用离线模式                                                                  |
| `--install`                                                | `true`  | 项目脚手架创建完成后安装依赖                            |
| `--no-install`                                             |         | 跳过安装依赖                                                         |
| `--gitInit`                                                |         | 初始化 git 仓库                                                            |
| `--no-gitInit`                                             |         | 跳过 git 仓库初始化                                                   |
| `--shell`                                                  |         | 在项目目录中安装完成后启动 shell                                  |
| `--packageManager=<npm\|pnpm\|yarn\|bun\|deno\|aube\|nub>` |         | 包管理器选择                                                               |
| `-M, --modules=<module-names>`                             |         | 要安装的 Nuxt 模块（以逗号分隔，且不包含空格）                             |
| `--no-modules`                                             |         | 跳过模块安装提示                                                      |
| `--nightly=<dist-tag>`                                     |         | 使用 Nuxt nightly 发布渠道（一个 `nuxt-nightly` dist tag，默认为 `latest`） |
<!--/init-opts-->

## 非交互式使用

如果没有终端来进行提示，则必须将它原本会询问的答案作为参数传入：目录、`--template`、`--packageManager` 和 `--gitInit`。任何缺失的内容都会与可用模板一同报告，并且命令会以 `2` 退出。

```bash [Terminal]
npm create nuxt@latest my-app -- --template minimal --packageManager pnpm --no-gitInit
```

::note
使用 `npm create` 时需要 `--`，因为 npm 会将初始化程序之后的任何类似标志的内容读取为 npm 自己的配置，并发出 `Unknown cli config` 警告，而不是将其传递下去。其他包管理器会原样转发完整命令行，因此请直接将标志传递给它们：`pnpm create nuxt@latest my-app --template minimal`。
::

## 环境变量

- `NUXI_INIT_REGISTRY`：设置自定义模板注册表（[详细了解](https://github.com/unjs/giget#custom-registry)）。
  - 默认注册表从 [nuxt/starter/templates](https://github.com/nuxt/starter/tree/templates/templates) 加载。
