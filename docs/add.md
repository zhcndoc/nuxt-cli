---
title: "nuxt add"
description: "使用命令行将模块添加到 Nuxt 应用程序中。"
links:
  - label: Source
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/3.x/packages/nuxi/src/commands/module/add.ts
    size: xs
---

<!--add-cmd-->
```bash [Terminal]
npx nuxt add <MODULENAME> [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--skipInstall] [--skipConfig] [--dev]
```
<!--/add-cmd-->

## 参数

<!--add-args-->
| 参数         | 描述                                       |
|--------------|--------------------------------------------|
| `MODULENAME` | 指定要安装的一个或多个模块，模块名称以空格分隔 |
<!--/add-args-->

## 选项

<!--add-opts-->
| 选项                                | 默认值 | 描述                     |
|--------------------------------------|---------|--------------------------|
| `--cwd=<directory>`                  | `.`     | 指定工作目录             |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时日志级别       |
| `--skipInstall`                      |         | 跳过 npm install         |
| `--skipConfig`                       |         | 跳过 nuxt.config.ts 更新 |
| `--dev`                              |         | 将模块作为开发依赖安装   |
<!--/add-opts-->

此命令可以在无需手动操作的情况下，将 [Nuxt modules](/modules) 安装到你的应用程序中。

运行此命令时，它将：

- 使用你的包管理器将模块安装为依赖项（除非设置了 `--skipInstall`）
- 将其添加到你的 [package.json](/docs/directory-structure/package) 文件中（除非设置了 `--skipInstall`）
- 更新你的 [`nuxt.config`](/docs/directory-structure/nuxt-config) 文件（除非设置了 `--skipConfig`）

如果未传入模块名称，系统会提示你搜索并选择要添加的模块。

**示例：**

安装 [`Pinia`](/modules/pinia) 模块

```bash [Terminal]
npx nuxt add pinia
```

::note
`nuxt module add` 是 `nuxt add` 的别名。
::

::read-more{to="/docs/api/commands/module"}
详细了解其他 `nuxt module` 命令。
::
