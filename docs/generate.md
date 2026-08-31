---
title: "nuxt generate"
description: 预渲染应用程序的每个路由，并将结果存储为普通 HTML 文件
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/3.x/packages/nuxi/src/commands/generate.ts
    size: xs
---

<!--generate-cmd-->
```bash [Terminal]
npx nuxt generate [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--preset] [--dotenv] [--envName] [-e, --extends=<layer-name>] [--profile[=verbose]]
```
<!--/generate-cmd-->

`generate` 命令会预渲染应用程序的每个路由，并将结果存储为普通 HTML 文件，你可以将这些文件部署到任何静态托管服务。该命令会触发 `nuxt build` 命令，并将 `prerender` 参数设置为 `true`

## 参数

<!--generate-args-->
| 参数          | 描述                                  |
|---------------|---------------------------------------|
| `ROOTDIR="."` | 指定工作目录（默认：`.`） |
<!--/generate-args-->

## 选项

<!--generate-opts-->
| 选项                                | 默认值 | 描述                                                                                                                                          |
|--------------------------------------|---------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--cwd=<directory>`                  |         | 指定工作目录，此选项的优先级高于 ROOTDIR（默认：`.`）                                                                     |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时的日志级别                                                                                                                         |
| `--preset`                           |         | Nitro 服务器预设                                                                                                                                  |
| `--dotenv`                           |         | 要加载的 `.env` 文件路径，相对于根目录                                                                                          |
| `--envName`                          |         | 解析配置覆盖项时使用的环境（构建时默认为 `production`，运行开发服务器时默认为 `development`） |
| `-e, --extends=<layer-name>`         |         | 从 Nuxt 层扩展                                                                                                                             |
| `--profile[=verbose]`                |         | 分析性能。使用 `--profile` 仅分析 CPU，使用 `--profile=verbose` 获取完整报告。                                                              |
<!--/generate-opts-->

::read-more{to="/docs/getting-started/deployment#static-hosting"}
详细了解预渲染和静态托管
:::
