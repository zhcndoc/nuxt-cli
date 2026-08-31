---
title: "nuxt test"
description: test 命令使用 @nuxt/test-utils 运行测试。
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/3.x/packages/nuxi/src/commands/test.ts
    size: xs
---

<!--test-cmd-->
```bash [Terminal]
npx nuxt test [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--dev] [--watch]
```
<!--/test-cmd-->

`test` 命令使用 [`@nuxt/test-utils`](/docs/getting-started/testing) 运行测试。如果尚未设置，此命令会将 `process.env.NODE_ENV` 设置为 `test`。

## 参数

<!--test-args-->
| 参数          | 描述                         |
|---------------|------------------------------|
| `ROOTDIR="."` | 指定工作目录（默认：`.`） |
<!--/test-args-->

## 选项

<!--test-opts-->
| 选项                                | 默认值 | 描述                                             |
|-------------------------------------|---------|--------------------------------------------------|
| `--cwd=<directory>`                 |         | 指定工作目录，此项优先于 ROOTDIR（默认：`.`） |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时日志级别                               |
| `--dev`                             |         | 在开发模式下运行                               |
| `--watch`                           |         | 监视模式                                       |
<!--/test-opts-->

::note
此命令会将 `process.env.NODE_ENV` 设置为 `test`。
::
