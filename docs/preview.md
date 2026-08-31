---
title: "nuxt preview"
description: preview 命令会在 build 命令执行后启动服务器，以预览你的应用
links:
  - label: 源代码
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/3.x/packages/nuxi/src/commands/preview.ts
    size: xs
---

<!--preview-cmd-->
```bash [Terminal]
npx nuxt preview [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--envName] [-e, --extends=<layer-name>] [-p, --port] [--dotenv]
```
<!--/preview-cmd-->

`preview` 命令会在运行 `build` 命令后启动服务器，以预览你的 Nuxt 应用。`start` 命令是 `preview` 的别名。在生产环境中运行应用时，请参阅[部署部分](/docs/getting-started/deployment)。

## 参数

<!--preview-args-->
| 参数          | 描述                         |
|---------------|------------------------------|
| `ROOTDIR="."` | 指定工作目录（默认值：`.`） |
<!--/preview-args-->

## 选项

<!--preview-opts-->
| 选项                                | 默认值 | 描述                                                                                                                                                   |
|--------------------------------------|---------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--cwd=<directory>`                  |         | 指定工作目录，其优先级高于 ROOTDIR（默认值：`.`）                                                                                                    |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时日志级别                                                                                                                                    |
| `--envName`                          |         | 解析配置覆盖项时使用的环境（构建时默认为 `production`，运行开发服务器时默认为 `development`） |
| `-e, --extends=<layer-name>`         |         | 从 Nuxt layer 扩展                                                                                                                                   |
| `-p, --port`                         |         | 要监听的端口                                                                                                                                           |
| `--dotenv`                           |         | 要加载的 `.env` 文件路径，相对于根目录                                                                                                                 |
<!--/preview-opts-->

如果未提供 `--port`，则按顺序使用 `NUXT_PORT`、`NITRO_PORT` 和 `PORT` 环境变量。

此命令会将 `process.env.NODE_ENV` 设置为 `production`。若要覆盖此设置，请在 `.env` 文件中或作为命令行参数定义 `NODE_ENV`。

::note
为方便起见，在预览模式下，你的[`.env`](/docs/directory-structure/env) 文件会被加载到 `process.env` 中。（但是，在生产环境中，你需要自行确保环境变量已设置。例如，使用 Node.js 20+ 时，可以运行 `NODE_ENV=production node --env-file .env .output/server/index.mjs` 来启动服务器。）
::
