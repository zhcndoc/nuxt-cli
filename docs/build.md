---
title: "nuxt build"
description: "构建你的 Nuxt 应用。"
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/3.x/packages/nuxi/src/commands/build.ts
    size: xs
---

<!--build-cmd-->
```bash [Terminal]
npx nuxt build [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--prerender] [--preset] [--dotenv] [--envName] [-e, --extends=<layer-name>] [--profile[=verbose]]
```
<!--/build-cmd-->

`build` 命令会创建一个 `.output` 目录，其中包含已准备好用于生产环境的全部应用、服务器和依赖项。

## 参数

<!--build-args-->
| 参数          | 描述                                       |
|---------------|--------------------------------------------|
| `ROOTDIR="."` | 指定工作目录（默认：`.`）                 |
<!--/build-args-->

## 选项

<!--build-opts-->
| 选项                               | 默认值 | 描述                                                                                                                                             |
|------------------------------------|---------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `--cwd=<directory>`                |         | 指定工作目录，其优先级高于 ROOTDIR（默认：`.`）                                                                                                  |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时的日志级别                                                                                                                             |
| `--prerender`                      |         | 构建 Nuxt 并预渲染静态路由                                                                                                                        |
| `--preset`                         |         | Nitro 服务器预设                                                                                                                                 |
| `--dotenv`                         |         | 要加载的 `.env` 文件路径，相对于根目录                                                                                                           |
| `--envName`                        |         | 解析配置覆盖时使用的环境（构建时默认为 `production`，运行开发服务器时默认为 `development`）                                                       |
| `-e, --extends=<layer-name>`       |         | 从 Nuxt layer 扩展                                                                                                                               |
| `--profile[=verbose]`              |         | 分析性能。使用 `--profile` 仅分析 CPU，使用 `--profile=verbose` 获取完整报告。                                                                     |
<!--/build-opts-->

::note
此命令会将 `process.env.NODE_ENV` 设置为 `production`。
::

::note
`--prerender` 始终会将 `preset` 设置为 `static`
::
