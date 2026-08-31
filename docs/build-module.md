---
title: 'nuxt build-module'
description: '在发布前构建 Nuxt 模块的 Nuxt 命令。'
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/module-builder/blob/main/src/cli.ts
    size: xs
---

<!--build-module-cmd-->
```bash [Terminal]
npx nuxt build-module [ROOTDIR] [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--build] [--stub] [--sourcemap] [--prepare]
```
<!--/build-module-cmd-->

`build-module` 命令运行 `@nuxt/module-builder`，在 `rootDir` 中生成 `dist` 目录，其中包含 **nuxt-module** 的完整构建产物。

## 参数

<!--build-module-args-->
| Argument      | Description                                    |
|---------------|------------------------------------------------|
| `ROOTDIR="."` | 指定工作目录（默认：`.`） |
<!--/build-module-args-->

## 选项

<!--build-module-opts-->
| Option                               | Default | Description                                                                      |
|--------------------------------------|---------|----------------------------------------------------------------------------------|
| `--cwd=<directory>`                  |         | 指定工作目录，其优先级高于 ROOTDIR（默认：`.`） |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时日志级别                                                     |
| `--build`                            | `false` | 构建用于分发的模块                                                    |
| `--stub`                             | `false` | 在开发过程中使用存根替代实际构建 dist                        |
| `--sourcemap`                        | `false` | 生成 sourcemap                                                              |
| `--prepare`                          | `false` | 为本地开发准备模块                                             |
<!--/build-module-opts-->

::read-more{to="https://github.com/nuxt/module-builder" icon="i-simple-icons-github" target="\_blank"}
详细了解 `@nuxt/module-builder`。
::
