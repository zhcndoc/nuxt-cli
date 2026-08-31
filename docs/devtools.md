---
title: "nuxt devtools"
description: devtools 命令允许你针对每个项目启用或禁用 Nuxt DevTools
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/3.x/packages/nuxi/src/commands/devtools.ts
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
| 参数          | 描述                                   |
|---------------|----------------------------------------|
| `COMMAND`     | 要运行的命令（选项：<enable\|disable>） |
| `ROOTDIR="."` | 指定工作目录（默认为：`.`）            |
<!--/devtools-args-->

## 选项

<!--devtools-opts-->
| 选项                | 默认值 | 描述                                                     |
|---------------------|---------|----------------------------------------------------------|
| `--cwd=<directory>` |         | 指定工作目录，其优先级高于 ROOTDIR（默认为：`.`） |
<!--/devtools-opts-->

::read-more{icon="i-simple-icons-nuxtdotjs" to="https://devtools.nuxt.com" target="\_blank"}
进一步了解 **Nuxt DevTools**。
:::
