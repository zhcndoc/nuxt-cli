---
title: "nuxt add"
description: "向应用中添加 Nuxt 模块和层"
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/add.ts
    size: xs
---

<!--add-cmd-->
```bash [Terminal]
npx nuxt add <MODULENAME...> [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--skipInstall] [--skipConfig] [--dev] [--packageManager=<npm|pnpm|yarn|bun|deno|aube|nub>]
```
<!--/add-cmd-->

`add` 命令会将 [Nuxt 模块](/modules) 和 [层](/docs/getting-started/layers) 安装到你的应用中。它与 [`nuxt module add`](/docs/api/commands/module#nuxt-module-add) 命令相同，同时包含层。

## 参数

<!--add-args-->
| 参数            | 描述                                             |
|-----------------|--------------------------------------------------|
| `MODULENAME...` | 指定要按名称安装的一个或多个模块或层，名称之间以空格分隔 |
<!--/add-args-->

## 选项

<!--add-opts-->
| 选项                                                       | 默认值 | 描述                                 |
|------------------------------------------------------------|---------|--------------------------------------|
| `--cwd=<directory>`                                        | `.`     | 指定 Nuxt 项目的根目录                |
| `--logLevel=<silent\|info\|verbose>`                       |         | 指定构建时日志级别                    |
| `--skipInstall`                                            |         | 跳过 npm install                      |
| `--skipConfig`                                             |         | 跳过 nuxt.config.ts 更新               |
| `--dev`                                                    |         | 将模块安装为开发依赖                   |
| `--packageManager=<npm\|pnpm\|yarn\|bun\|deno\|aube\|nub>` |         | 用于安装的软件包管理器                 |
<!--/add-opts-->

运行命令时，它将：

- 使用你的软件包管理器将软件包安装为依赖，除非你传入 `--skipInstall`
- 将其添加到你的 [`package.json`](/docs/directory-structure/package) 文件中
- 将其注册到你的 [`nuxt.config`](/docs/directory-structure/nuxt-config) 文件中，对于模块注册到 `modules`，对于层注册到 `extends`，除非你传入 `--skipConfig`

**示例：**

```bash [Terminal]
npx nuxt add pinia
```

可以一次添加多个软件包，并且模块将根据你的项目所使用的 Nuxt 版本进行解析：

```bash [Terminal]
npx nuxt add @nuxt/image @nuxt/fonts
```

不指定名称运行该命令，可以交互式浏览可用模块。

::note
`nuxt add <template> <name>` 已弃用。请使用 [`nuxt add-template`](/docs/api/commands/add-template) 来搭建文件。
::

::read-more{to="/docs/api/commands/module"}
详细了解如何搜索和移除模块。
::
