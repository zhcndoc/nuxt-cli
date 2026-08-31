---
title: "nuxt module"
description: "使用命令行在 Nuxt 应用中搜索和移除模块。"
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/tree/3.x/packages/nuxi/src/commands/module
    size: xs
---

Nuxt 提供了一些实用工具，可无缝地使用 [Nuxt 模块](/modules)。

::read-more{to="/docs/api/commands/add"}
详细了解 `nuxt add`，它可以将模块安装到你的应用中。
::

## `nuxt module remove`

<!--module-remove-cmd-->
```bash [Terminal]
npx nuxt module remove [MODULENAME] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--skipInstall] [--skipConfig]
```
<!--/module-remove-cmd-->

### 参数

<!--module-remove-args-->
| 参数         | 描述                                   |
|--------------|----------------------------------------|
| `MODULENAME` | 指定一个或多个要移除的模块名称，以空格分隔 |
<!--/module-remove-args-->

### 选项

<!--module-remove-opts-->
| 选项                                | 默认值 | 描述             |
|-------------------------------------|---------|------------------|
| `--cwd=<directory>`                 | `.`     | 指定工作目录     |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时日志级别 |
| `--skipInstall`                     |         | 跳过卸载依赖     |
| `--skipConfig`                      |         | 跳过更新 nuxt.config.ts |
<!--/module-remove-opts-->

该命令会卸载模块（除非设置了 `--skipInstall`），并将其从你的 [`nuxt.config`](/docs/directory-structure/nuxt-config) 文件中移除（除非设置了 `--skipConfig`）。如果未传入模块名称，系统会提示你从已在 `nuxt.config` 中注册的模块中进行选择。设置 `--skipConfig` 时必须提供模块名称。

**示例：**

```bash [Terminal]
npx nuxt module remove pinia
```

## `nuxt module search`

<!--module-search-cmd-->
```bash [Terminal]
npx nuxt module search <QUERY> [--cwd=<directory>] [--nuxtVersion=<2|3>]
```
<!--/module-search-cmd-->

### 参数

<!--module-search-args-->
| 参数    | 描述       |
|---------|------------|
| `QUERY` | 要搜索的关键词 |
<!--/module-search-args-->

### 选项

<!--module-search-opts-->
| 选项                  | 默认值 | 描述                                                                     |
|-----------------------|---------|--------------------------------------------------------------------------|
| `--cwd=<directory>`   | `.`     | 指定工作目录                                                             |
| `--nuxtVersion=<2\|3>` |         | 按 Nuxt 版本进行筛选，仅列出兼容的模块（默认自动检测） |
<!--/module-search-opts-->

该命令会搜索与你的查询匹配且兼容你的 Nuxt 版本的 Nuxt 模块。

**示例：**

```bash [Terminal]
npx nuxt module search pinia
```
