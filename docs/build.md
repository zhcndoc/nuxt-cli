---
title: "nuxt build"
description: "构建 Nuxt 应用"
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/build.ts
    size: xs
---

<!--build-cmd-->
```bash [Terminal]
npx nuxt build [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--prerender] [--target=<target>] [--dotenv=<path>...] [--envName=<environment>] [-e, --extends=<layer-name>...] [--profile=<verbose>]
```
<!--/build-cmd-->

`build` 命令会创建一个 `.output` 目录，其中包含已准备好用于生产环境的全部应用、服务器和依赖项，并报告构建耗时。

## 参数

<!--build-args-->
| 参数      | 描述                                            |
|-----------|-------------------------------------------------|
| `ROOTDIR` | Nuxt 项目的根目录（默认值：.）                  |
<!--/build-args-->

## 选项

<!--build-opts-->
| 选项                                | 默认值 | 描述                                                                                                                                              |
|-------------------------------------|---------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| `--cwd=<directory>`                 |         | 指定 Nuxt 项目的根目录                                                                                                                             |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时的日志级别                                                                                                                              |
| `--prerender`                       |         | 构建 Nuxt 并预渲染静态路由                                                                                                                         |
| `--target=<target>`                 |         | 为配置的服务器构建器指定部署目标（例如：`node-server`、`vercel`、`netlify`）                                                                      |
| `--dotenv=<path>...`                |         | 要加载的 `.env` 文件路径，相对于根目录。可以重复使用，后面的文件优先级更高。                                                                       |
| `--envName=<environment>`           |         | 解析配置覆盖项时使用的环境（构建时默认为 `production`，运行开发服务器时默认为 `development`）                                                       |
| `-e, --extends=<layer-name>...`     |         | 从 Nuxt layer 扩展                                                                                                                                |
| `--profile=<verbose>`               |         | 分析性能，在退出时写入 V8 CPU profile 和 JSON 报告。使用 `--profile=verbose` 可获取完整的控制台报告。                                               |
<!--/build-opts-->

::note
此命令会将 `process.env.NODE_ENV` 设置为 `production`。
::

::note
`--prerender` 始终会将 target 设置为 `static`
::

`--preset` 仍可作为 `--target` 的另一个名称接受。如果两者都未传入，则按此顺序使用 `NITRO_PRESET` 和 `SERVER_PRESET` 环境变量。

`--profile` 会将 V8 CPU profile 写入项目中的 `nuxt-build.cpuprofile`。它报告的构建耗时，以及构建目录中的 `perf-report.json` 和 `perf-trace.json`，均来自 Nuxt 自身的构建性能分析，并且需要 Nuxt v4.4 或更高版本。
