---
title: "nuxt info"
description: info 命令会记录当前或指定 Nuxt 项目的信息
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/info.ts
    size: xs
---

<!--info-cmd-->
```bash [Terminal]
npx nuxt info [ROOTDIR] [--cwd=<directory>] [--json]
```
<!--/info-cmd-->

`info` 命令会记录当前或指定 Nuxt 项目的信息：它解析到的 Nuxt、Nitro 和 Vite 版本、包管理器、加载的模块，以及其配置中的构建模块。当你想从脚本中读取这些信息时，请使用 `--json`。

## 参数

<!--info-args-->
| 参数      | 描述                                               |
|-----------|----------------------------------------------------|
| `ROOTDIR` | Nuxt 项目的根目录（默认：.）                       |
<!--/info-args-->

## 选项

<!--info-opts-->
| 选项                | 默认值 | 描述                                          |
|---------------------|--------|-----------------------------------------------|
| `--cwd=<directory>` |        | 指定 Nuxt 项目的根目录                         |
| `--json`            |        | 将项目信息打印为 JSON                          |
<!--/info-opts-->
