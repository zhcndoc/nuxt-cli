---
title: "nuxt analyze"
description: "分析生产构建包或你的 Nuxt 应用"
links:
  - label: Source
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/analyze.ts
    size: xs
---

<!--analyze-cmd-->
```bash [Terminal]
npx nuxt analyze [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--dotenv=<path>...] [-e, --extends=<layer-name>...] [--name=<name>] [--serve] [--prerender] [--json]
```
<!--/analyze-cmd-->

`analyze` 命令会构建 Nuxt 并分析生产构建包（实验性）。构建完成后，结果会在本地服务器上提供，除非你传入 `--no-serve` 或环境中设置了 `CI`

服务器会提供指向各报告的链接：客户端构建包和 Nitro 服务端构建包。如果只有一份报告，服务器会直接显示该报告。服务器使用 `PORT` 中设置的端口，或默认使用 3000 端口。如果该端口已被占用，则会在 3000 到 3100 之间选择一个空闲端口。

每次运行都会在 [`analyzeDir`](https://nuxt.com/docs/api/nuxt-config#analyzedir) 中创建独立目录，目录名取自 `--name`（未指定时为 `default`），因此可以并列保留多次运行的结果，例如使用 `--name=before` 和 `--name=after`。使用相同名称再次运行只会替换对应目录。目录名中除字母、数字、`_` 和 `-` 以外的字符都会替换为 `_`，因此 `--name=after/fix` 和 `--name=after_fix` 会使用同一个目录。如果设置了 `build.analyze.filename`，客户端报告会改为写入该路径。对于 Nuxt 3 和 4，`nitro.analyze.filename` 对 Nitro 报告的作用相同。

传入 `--json` 可将报告输出为 JSON，而不是 HTML：文件名为 `client.json` 和 `nitro.json`，格式为 `rollup-plugin-visualizer` 的 `raw-data`。报告包含各模块的大小、所属构建块以及静态和动态导入信息，便于脚本或 AI agent 处理。此模式不会启动服务。如果自定义报告文件名以 `.html` 结尾，实际写入的扩展名会改为 `.json`。使用 webpack 或 rspack 构建器时，`client.json` 是 webpack stats 文件，而不是 `raw-data` 格式。

使用 Nuxt 5 时，Nitro 报告需要在项目中安装 `rollup-plugin-visualizer`。如果未安装，则会跳过 Nitro 报告。使用 Vite 构建器时，Nuxt 还会询问是否将其安装为开发依赖。

分析时不会预渲染路由，因为预渲染会运行构建后的应用，而其输出并不是正在测量的内容。如果分析需要预渲染，请传入 `--prerender`

## 参数

<!--analyze-args-->
| 参数      | 描述                              |
|-----------|--------------------------------------|
| `ROOTDIR` | Nuxt 项目的根目录（默认值：.） |
<!--/analyze-args-->

## 选项

<!--analyze-opts-->
| 选项                                | 默认值    | 描述                                                                                                       |
|--------------------------------------|-----------|-------------------------------------------------------------------------------------------------------------------|
| `--cwd=<directory>`                  |           | 指定 Nuxt 项目的根目录                                                                   |
| `--logLevel=<silent\|info\|verbose>` |           | 指定构建时日志级别                                                                                      |
| `--dotenv=<path>...`                 |           | 要加载的 `.env` 文件路径，相对于根目录。可以重复使用，后面的文件优先级更高 |
| `-e, --extends=<layer-name>...`      |           | 从 Nuxt layer 扩展                                                                                          |
| `--name=<name>`                      | `default` | 分析的名称                                                                                              |
| `--serve`                            | `true`    | 提供分析结果                                                                                        |
| `--no-serve`                         |           | 跳过提供分析结果                                                                                 |
| `--prerender`                        | `false`   | 分析时预渲染路由                                                                                  |
| `--json`                             | `false`   | 将客户端和服务端构建包分析结果写入 JSON，而不是 HTML（隐含 `--no-serve`）                          |
<!--/analyze-opts-->

::note
此命令会将 `process.env.NODE_ENV` 设置为 `production`
::
