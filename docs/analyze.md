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
npx nuxt analyze [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--dotenv=<path>...] [-e, --extends=<layer-name>...] [--name=<name>] [--serve] [--prerender]
```
<!--/analyze-cmd-->

`analyze` 命令会构建 Nuxt 并分析生产构建包（实验性）。构建完成后，结果会在本地服务器上提供，除非你传入 `--no-serve` 或环境中设置了 `CI`

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
<!--/analyze-opts-->

::note
此命令会将 `process.env.NODE_ENV` 设置为 `production`
::
