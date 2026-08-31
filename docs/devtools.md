---
title: "nuxt devtools"
description: devtools 命令允许你按项目启用或禁用 Nuxt DevTools。
links:
  - label: Source
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/devtools.ts
    size: xs
---

<!--devtools-cmd-->
```bash [Terminal]
npx nuxt devtools <COMMAND> [ROOTDIR] [--cwd=<directory>]
```
<!--/devtools-cmd-->

运行 `nuxt devtools enable` 将全局安装 Nuxt DevTools，同时在你正在使用的特定项目中启用它。它会作为偏好设置保存在用户级别的 `.nuxtrc` 中。如果你想移除特定项目的 devtools 支持，可以运行 `nuxt devtools disable`。

## 参数

<!--devtools-args-->
| 参数                        | 描述                                  |
|-----------------------------|---------------------------------------|
| `COMMAND=<enable\|disable>` | 要运行的命令                          |
| `ROOTDIR`                   | Nuxt 项目的根目录（默认：.）          |
<!--/devtools-args-->

## 选项

<!--devtools-opts-->
| 选项                | 默认值 | 描述                              |
|---------------------|---------|-----------------------------------|
| `--cwd=<directory>` |         | 指定 Nuxt 项目的根目录            |
<!--/devtools-opts-->

::read-more{icon="i-simple-icons-nuxtdotjs" to="https://devtools.nuxt.com" target="\_blank"}
详细了解 **Nuxt DevTools**。
::
