---
title: 'nuxt dev'
description: dev 命令会在 http://localhost:3000 启动一个支持热模块替换的开发服务器
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/dev.ts
    size: xs
---

<!--dev-cmd-->
```bash [Terminal]
npx nuxt dev [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--dotenv=<path>...] [--envName=<environment>] [-e, --extends=<layer-name>...] [--inspect] [--inspect-brk] [--tui] [--clear] [-f, --fork] [-p, --port=<port>] [--takeover] [--strictPort] [-h, --host=<host>] [-o, --open] [--open.url=<url|path>] [--clipboard] [--qr] [--tunnel] [--public] [--publicURL=<url>] [--https] [--https.cert=<path>] [--https.key=<path>] [--https.pfx=<path>] [--https.passphrase=<passphrase>] [--https.validityDays=<days>] [--https.domains=<domain>...] [--profile=<verbose>]
```
<!--/dev-cmd-->

`dev` 命令会在[http://localhost:3000](http://localhost:3000)启动一个支持热模块替换的开发服务器

![nuxt dev](/capture/output/nuxt-dev-static.svg)

## 参数

<!--dev-args-->
| 参数       | 描述                                  |
|------------|---------------------------------------|
| `ROOTDIR`  | Nuxt 项目的根目录（默认：.） |
<!--/dev-args-->

## 选项

<!--dev-opts-->
| 选项                                | 默认值            | 描述                                                                                                                                                 |
|-------------------------------------|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| `--cwd=<directory>`                 |                   | 指定 Nuxt 项目的根目录                                                                                                      |
| `--logLevel=<silent\|info\|verbose>` |                   | 指定构建时日志级别                                                                                                                         |
| `--dotenv=<path>...`                |                   | 要加载的 `.env` 文件路径，相对于根目录。可以重复指定，后面的文件具有更高优先级。                                    |
| `--envName=<environment>`           |                   | 解析配置覆盖时使用的环境（构建时默认为 `production`，运行 dev 服务器时默认为 `development`） |
| `-e, --extends=<layer-name>...`     |                   | 从 Nuxt layer 扩展                                                                                                                             |
| `--inspect`                         |                   | 为服务于应用的进程启用 Node.js inspector（`--inspect=[host:]port`）                                                              |
| `--inspect-brk`                     |                   | 启用 Node.js inspector，并等待调试器连接（`--inspect-brk=[host:]port`）                                                         |
| `--tui`                             | `true`            | 交互式终端 UI（固定状态面板、折叠日志和单键快捷键）                                                                  |
| `--no-tui`                          |                   | 禁用交互式终端 UI，改为直接输出日志                                                                                          |
| `--clear`                           | `false`           | 重启时清空控制台                                                                                                                             |
| `-f, --fork`                        | runtime-dependent | 从 fork 的子进程中提供应用服务（在运行时支持的情况下默认开启）                                                           |
| `--no-fork`                         |                   | 禁用 fork 模式                                                                                                                                  |
| `-p, --port=<port>`                 |                   | 要监听的端口（默认：`NUXT_PORT \|\| NITRO_PORT \|\| PORT \|\| nuxtOptions.devServer.port`）                                                   |
| `--takeover`                        |                   | 停止当前项目中已运行的 dev 服务器并接管它                                                                                 |
| `--no-takeover`                     |                   | 永不停止当前项目中已运行的 dev 服务器                                                                                              |
| `--strictPort`                      | `false`           | 如果请求的端口不可用则退出，而不是使用其他端口                                                                               |
| `-h, --host=<host>`                 |                   | 要监听的主机（默认：`NUXT_HOST \|\| NITRO_HOST \|\| HOST \|\| nuxtOptions.devServer?.host`）                                                  |
| `-o, --open`                        | `false`           | 在浏览器中打开 URL                                                                                                                          |
| `--open.url=<url\|path>`            |                   | 要打开的路径或 URL，而不是 dev 服务器根目录                                                                                                   |
| `--clipboard`                       | `false`           | 将 URL 复制到剪贴板                                                                                                                        |
| `--qr`                              |                   | 为公共 URL 打印二维码（有可用公共 URL 时默认启用）                                                                        |
| `--tunnel`                          |                   | 通过 Cloudflare quick tunnel 暴露服务器                                                                                                      |
| `--public`                          |                   | 监听所有网络接口                                                                                                                     |
| `--publicURL=<url>`                 |                   | 要显示的公共 URL（用于二维码和剪贴板）                                                                                               |
| `--https`                           |                   | 使用本地信任的开发证书启用 HTTPS                                                                                          |
| `--https.cert=<path>`               |                   | TLS 证书路径                                                                                                                              |
| `--https.key=<path>`                |                   | TLS 密钥路径                                                                                                                                      |
| `--https.pfx=<path>`                |                   | PKCS#12（.p12/.pfx）密钥库路径                                                                                                                 |
| `--https.passphrase=<passphrase>`   |                   | TLS 密钥或密钥库的密码                                                                                                               |
| `--https.validityDays=<days>`       |                   | 生成的自签名证书的有效天数                                                                                             |
| `--https.domains=<domain>...`       |                   | 生成证书的域名。可以重复指定，也可以以逗号分隔的列表形式提供。                                                             |
| `--profile=<verbose>`               |                   | 分析性能，在退出时写入 V8 CPU profile 和 JSON 报告。使用 `--profile=verbose` 获取完整的控制台报告。                          |
<!--/dev-opts-->

也可以通过 `NUXT_PORT`、`NITRO_PORT`、`PORT`、`NUXT_HOST`、`NITRO_HOST` 或 `HOST` 环境变量设置端口和主机。

此命令会将 `process.env.NODE_ENV` 设置为 `development`。

## 交互式终端 UI

在交互式终端中，`nuxt dev` 会渲染一个固定面板：服务器 URL、启动进度、当前状态和一行快捷键，其上方的日志会折叠显示。当输出不是终端输出、处于 CI 环境、连接了调试器或终端过小时，它会回退为普通的日志流。

| 按键        | 操作                                          |
|-------------|-----------------------------------------------|
| `r`         | 重启 dev 服务器                        |
| `shift-r`   | 使用已清除的缓存重启                  |
| `o`         | 在浏览器中打开应用                  |
| `y`         | 将服务器 URL 复制到剪贴板          |
| `i`         | 显示版本、URL、二维码和会话信息 |
| `l`         | 浏览日志历史                        |
| `e`         | 打开最后一个错误处的日志               |
| `n`         | 浏览已提供服务的请求                        |
| `p`         | 浏览页面和服务器路由                |
| `c`         | 清除日志、请求和控制台          |
| `?`         | 显示所有快捷键                            |
| `q`         | 退出                                          |

传入 `--no-tui` 可改为直接输出日志，`NUXT_TUI=plain` 也会永久执行相同操作。`NUXT_TUI=1` 会在环境检查本来会将其关闭的情况下强制开启 UI，但当输出通过管道传输或重定向时除外。

![带有普通输出的 nuxt dev](/capture/output/nuxt-dev-plain-static.svg)

普通输出提供的快捷键更少：`r` 重启，`o` 打开，`u` 显示 URL，`qr` 显示二维码，`copy` 复制 URL，`c` 清除控制台，`h` 获取帮助，`q` 退出。

## 重启

当 dev 服务器重新加载或重启时，它会说明触发原因；对 `nuxt.config` 的更改还会列出实际不同的键，因此可以区分仅由格式更改触发的重启和更改了配置的重启。重新加载会在原进程中进行；重启会替换进程，这是更改 `nuxt.config` 或已安装依赖所需的操作。

## 接管正在运行的 dev 服务器

dev 服务器会将自身记录在[构建目录](/docs/directory-structure/nuxt)中的 `nuxt.lock` 内，因此同一项目的第二个 `nuxt dev` 会报告已经运行的服务器，而不是与其争抢端口。传入 `--takeover` 可停止它并接管其位置，或设置 `NUXT_IGNORE_LOCK=1` 以无论如何运行第二个服务器（不受支持）。

[`nuxt curl`](/docs/api/commands/curl) 和 [`nuxt task`](/docs/api/commands/task) 也是通过同一个锁文件查找要与之通信的服务器。

## HTTPS

`--https` 会通过 TLS 提供服务：安装了 `mkcert` 时使用它生成本地信任的证书，否则生成自签名证书。`--https.cert` 和 `--https.key` 使用已有证书，`--https.pfx` 与 `--https.passphrase` 则使用 PKCS#12 密钥库。

::note
Node 不会读取系统信任存储，因此从 Node 向使用生成证书的服务器发出的请求不会信任该证书。请将 `NODE_EXTRA_CA_CERTS` 设置为签发该证书的证书颁发机构。
::

## 调试

`--inspect` 会在实际为应用提供服务的进程上打开 Node.js inspector，`--inspect-brk` 则会等待调试器连接后再运行。两者都接受可选的 `[host:]port`。

`--profile` 会在进程退出时，将 V8 CPU profile 写入项目中的 `nuxt-dev.cpuprofile`。`--profile=verbose` 还会将完整报告打印到控制台。

::note
构建计时、`perf-report.json` 和 `perf-trace.json` 来自 Nuxt 自带的构建性能分析功能，该功能需要 Nuxt v4.4 或更高版本。在更早版本中仍会写入 CPU profile。
::

## 环境变量

| 变量                         | 用途                                                               |
|------------------------------|----------------------------------------------------------------------|
| `NUXT_PORT`、`NITRO_PORT`、`PORT` | 按此优先级顺序监听端口               |
| `NUXT_HOST`、`NITRO_HOST`、`HOST` | 按此优先级顺序监听主机               |
| `NUXT_TUI`                   | `1` 强制开启交互式 UI，`plain` 选择退出               |
| `NUXT_TERM_THEME`            | 当无法检测终端背景时，使用 `light` 或 `dark`  |
| `NUXT_IGNORE_LOCK`           | `1` 忽略当前项目中已经运行的 dev 服务器           |
| `NUXT_IGNORE_UPDATE_CHECK`   | `1` 停止 CLI 检查更新版本的 Nuxt                  |
