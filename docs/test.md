---
title: "nuxt test"
description: test 命令使用 @nuxt/test-utils 运行测试
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/test.ts
    size: xs
---

<!--test-cmd-->
```bash [Terminal]
npx nuxt test [ROOTDIR] [--cwd=<directory>] [--dev] [--watch]
```
<!--/test-cmd-->

`test` 命令使用 [`@nuxt/test-utils`](/docs/getting-started/testing) 运行测试。如果尚未设置，此命令会将 `process.env.NODE_ENV` 设置为 `test`。

## 参数

<!--test-args-->
| 参数       | 描述                                  |
|------------|---------------------------------------|
| `ROOTDIR`  | Nuxt 项目的根目录（默认值：.）        |
<!--/test-args-->

## 选项

<!--test-opts-->
| 选项                | 默认值 | 描述                     |
|---------------------|--------|--------------------------|
| `--cwd=<directory>` |        | 指定 Nuxt 项目的根目录   |
| `--dev`             |        | 以开发模式运行           |
| `--watch`           |        | 监视模式                 |
<!--/test-opts-->

::note
此命令会将 `process.env.NODE_ENV` 设置为 `test`。
:::
