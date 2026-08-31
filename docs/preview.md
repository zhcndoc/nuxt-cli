---
title: "nuxt preview"
description: preview 命令会启动一个服务器，用于在 build 命令执行后预览你的应用程序
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/preview.ts
    size: xs
---

<!--preview-cmd-->
```bash [Terminal]
npx nuxt preview [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--envName=<environment>] [-e, --extends=<layer-name>...] [-p, --port=<port>] [-h, --host=<host>] [--dotenv=<path>...]
```
<!--/preview-cmd-->

`preview` 命令会在运行 `build` 命令后启动一个服务器，用于预览你的 Nuxt 应用程序。`nuxt start` 是该命令的另一个名称。在生产环境中运行应用程序时，请参阅[部署部分](/docs/getting-started/deployment)。

当配置的 `server.builder` 完全不生成服务器时（例如，仅客户端构建），就没有可运行的内容：此时会直接提供静态输出，并将不匹配的路径回退到客户端入口，从而使客户端路由正常工作。

某些 Nitro 预设不会生成可在本地运行的服务器。对于这些预设，会改为运行预设自身的预览命令，并且命令会告知你正在运行的内容。

## 参数

<!--preview-args-->
| 参数       | 描述                                             |
|------------|--------------------------------------------------|
| `ROOTDIR`  | Nuxt 项目的根目录（默认值：.）                  |
<!--/preview-args-->

## 选项

<!--preview-opts-->
| 选项                                | 默认值 | 描述                                                                                                                                             |
|-------------------------------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `--cwd=<directory>`                 |        | 指定 Nuxt 项目的根目录                                                                                                                           |
| `--logLevel=<silent\|info\|verbose>` |        | 指定构建时日志级别                                                                                                                               |
| `--envName=<environment>`           |        | 解析配置覆盖时使用的环境（构建时默认为 `production`，运行开发服务器时默认为 `development`）                                                     |
| `-e, --extends=<layer-name>...`     |        | 从 Nuxt layer 扩展                                                                                                                               |
| `-p, --port=<port>`                 |        | 要监听的端口（默认值：`NUXT_PORT \|\| NITRO_PORT \|\| PORT`）                                                                                    |
| `-h, --host=<host>`                 |        | 要监听的主机（默认值：`NUXT_HOST \|\| NITRO_HOST \|\| HOST`）                                                                                    |
| `--dotenv=<path>...`                |        | 要加载的 `.env` 文件路径，相对于根目录。可以重复指定，后面的文件优先级更高。                                                                      |
<!--/preview-opts-->

此命令会将 `process.env.NODE_ENV` 设置为 `production`。如需覆盖该设置，请在 `.env` 文件中定义 `NODE_ENV`，或将其作为命令行参数传入。

::note
为方便起见，在预览模式下，你的 [`.env`](/docs/directory-structure/env) 文件会被加载到 `process.env` 中。（不过，在生产环境中，你需要自行确保环境变量已设置。例如，使用 Node.js 20+ 时，可以运行 `NODE_ENV=production node --env-file .env .output/server/index.mjs` 来启动服务器。）
::
