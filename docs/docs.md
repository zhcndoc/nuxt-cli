---
title: "nuxt 文档"
description: docs 命令会搜索与你的项目所使用版本对应的 Nuxt 文档
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/docs.ts
    size: xs
---

<!--docs-cmd-->
```bash [Terminal]
npx nuxt docs [QUERY] [--cwd=<directory>] [--open]
```
<!--/docs-cmd-->

`docs` 命令会搜索 Nuxt 文档，并在浏览器中打开最佳匹配结果。不提供查询时，它会打开文档主页。

## 参数

<!--docs-args-->
| 参数      | 描述             |
|-----------|------------------|
| `QUERY`   | 用于搜索文档的词语 |
<!--/docs-args-->

## 选项

<!--docs-opts-->
| 选项                | 默认值 | 描述                             |
|---------------------|--------|----------------------------------|
| `--cwd=<directory>` | `.`    | 指定 Nuxt 项目的根目录           |
| `--open`            | `true` | 在浏览器中打开最佳匹配结果       |
| `--no-open`         |        | 打印匹配页面而不打开浏览器       |
<!--/docs-opts-->

结果会依次按照页面标题、章节标题和描述进行排名，并且会在打开最佳结果之前打印匹配结果。当有多个页面匹配且终端处于交互模式时，系统会询问你要打开哪一个。

```bash [Terminal]
npx nuxt docs "server routes"
```

搜索针对的是项目所依赖的 Nuxt 版本对应的文档，而不是当前发布的版本，因此得到的答案与你正在使用的版本相匹配。项目中安装了 `@nuxt/docs` 时会使用它，否则会下载该包。
