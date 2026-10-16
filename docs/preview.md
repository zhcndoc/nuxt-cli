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
npx nuxt preview [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--envName=<environment>] [-e, --extends=<layer-name>...] [-p, --port=<port>] [-h, --host=<host>] [--takeover] [--strictPort] [--dotenv=<path>...]
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
| 选项                                  | 默认值 | 描述                                                                                                                                             |
|---------------------------------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `--cwd=<directory>`                   |        | 指定 Nuxt 项目的根目录                                                                                                                           |
| `--logLevel=<silent\|info\|verbose>` |        | 指定构建时日志级别                                                                                                                               |
| `--envName=<environment>`             |        | 解析配置覆盖时使用的环境（构建时默认为 `production`，运行开发服务器时默认为 `development`）                                                     |
| `-e, --extends=<layer-name>...`       |        | 从 Nuxt layer 扩展                                                                                                                               |
| `-p, --port=<port>`                   |        | 要监听的端口（默认值：`NUXT_PORT \|\| NITRO_PORT \|\| PORT`）                                                                                    |
| `-h, --host=<host>`                   |        | 要监听的主机（默认值：`NUXT_HOST \|\| NITRO_HOST \|\| HOST`）                                                                                    |
| `--takeover`                          |        | 停止此项目中已运行的预览服务器并接管其端口                                                                                                       |
| `--no-takeover`                       |        | 绝不停止此项目中已运行的预览服务器                                                                                                               |
| `--strictPort`                        | `false` | 如果请求的端口不可用，则退出而不是使用其他端口                                                                                                   |
| `--dotenv=<path>...`                  |        | 要加载的 `.env` 文件路径，相对于根目录。可以重复指定，后面的文件优先级更高。                                                                      |
<!--/preview-opts-->

## 接管正在运行的预览服务器

预览服务器会将自身记录在 `node_modules/.cache/nuxt/preview` 中，因此，同一项目再次运行 `nuxt preview` 时，会像 [`nuxt dev`](/docs/api/commands/dev#taking-over-a-running-dev-server) 处理正在运行的开发服务器一样处理现有预览服务器：

| 运行中的预览启动方式 | 新预览启动方式 | 处理方式 |
|----------------------|----------------|----------|
| 未使用终端           | 未使用终端     | 停止现有预览，并由新预览接管其端口。 |
| 未使用终端           | 在终端中       | 询问你是否接管，默认选择接管。 |
| 在终端中             | 未使用终端     | 新预览退出，并告知正在运行的预览位于何处。 |
| 在终端中             | 在终端中       | 询问你是否启动，默认选择不启动。 |

传入 `--takeover` 可始终停止现有预览并在其位置启动，传入 `--no-takeover` 则始终不接管。在提示中选择“仍要启动”，或传入不同的 `--port`，即可同时运行第二个预览。

如果请求的端口正被其他服务器（包括 `nuxt dev`）使用，预览会自动改用其他空闲端口，而不会停止该服务器。传入 `--strictPort` 可让命令直接退出。请求的端口依次取自 `--port`、`NUXT_PORT`、`NITRO_PORT` 或 `PORT`，默认为 `3000`。

端口选择适用于静态预览，以及由 Node.js、Bun 或 Deno 直接运行的预览命令。其他预览命令会自行选择端口。

此命令会将 `process.env.NODE_ENV` 设置为 `production`。如需覆盖该设置，请在 `.env` 文件中定义 `NODE_ENV`，或将其作为命令行参数传入。

::note
为方便起见，在预览模式下，你的 [`.env`](/docs/directory-structure/env) 文件会被加载到 `process.env` 中。（不过，在生产环境中，你需要自行确保环境变量已设置。例如，使用 Node.js 20+ 时，可以运行 `NODE_ENV=production node --env-file .env .output/server/index.mjs` 来启动服务器。）
::
