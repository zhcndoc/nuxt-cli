---
title: "nuxt curl"
description: curl 命令会向正在运行的 Nuxt 开发服务器发送 HTTP 请求
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/curl.ts
    size: xs
---

<!--curl-cmd-->
```bash [Terminal]
npx nuxt curl <URL> [ROOTDIR] [--cwd=<directory>] [-X, --method=<method>] [-H, --header=<header>...] [-d, --data=<data>] [-i, --include] [-I, --head] [-v, --verbose] [--pretty]
```
<!--/curl-cmd-->

`curl` 命令会向项目正在运行的 `nuxt dev` 服务器发送 HTTP 请求并打印响应。路径会根据该服务器进行解析，因此你无需知道它最终使用了哪个端口

![nuxt curl](/capture/output/nuxt-curl.svg)

## 参数

<!--curl-args-->
| 参数               | 描述                                                         |
|-------------------|--------------------------------------------------------------|
| `URL=<url\|path>` | 绝对 URL，或根据正在运行的开发服务器解析的路径                 |
| `ROOTDIR`         | Nuxt 项目的根目录（默认值：.）                                 |
<!--/curl-args-->

## 选项

<!--curl-opts-->
| 选项                      | 默认值 | 描述                                                                                                                               |
|----------------------------|---------|-----------------------------------------------------------------------------------------------------------------------------------|
| `--cwd=<directory>`        |         | 指定 Nuxt 项目的根目录                                                                                                            |
| `-X, --method=<method>`    |         | HTTP 方法（默认值：GET，或在提供请求体时使用 POST）                                                                               |
| `-H, --header=<header>...` |         | `Name: Value` 格式的请求标头，可重复使用                                                                                           |
| `-d, --data=<data>`        |         | 请求体。使用 `@-` 读取标准输入，使用 `@<file>` 读取文件                                                                           |
| `-i, --include`            |         | 在输出中包含响应状态行和标头                                                                                                       |
| `-I, --head`               |         | 发送 `HEAD` 请求，仅显示响应标头                                                                                                   |
| `-v, --verbose`            |         | 将请求和响应标头打印到标准错误                                                                                                     |
| `--pretty`                 |         | 重新缩进并进行语法高亮（默认值：终端中开启，通过管道传输时关闭）。使用 `--pretty`/`--no-pretty` 强制重新缩进。 |
<!--/curl-opts-->

开发服务器通过它写入 [构建目录](/docs/directory-structure/nuxt) 中的 `nuxt.lock` 文件查找，因此只有在该项目运行 `nuxt dev` 时，此命令才有效。传入绝对 URL 即可与其他服务器通信

**示例：**

```bash [Terminal]
# Request a path on the running dev server
npx nuxt curl /api/hello

# Include the status line and response headers
npx nuxt curl /api/hello -i

# Send JSON
npx nuxt curl /api/todos -X POST -H "Content-Type: application/json" -d '{"title":"Buy milk"}'

# Read the body from a file, or from stdin with `@-`
npx nuxt curl /api/todos -d @todo.json
```

当输出目标是终端时，JSON、HTML、XML 及其他文本响应会重新缩进并进行语法高亮；通过管道传输时，则会逐字节传递。使用 `--no-pretty` 可选择退出，或在通过管道传输时使用 `--pretty` 强制启用

::note
当服务器返回 HTTP 错误状态时，该命令会以 `22` 退出，与 `curl --fail` 的行为一致
::
