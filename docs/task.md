---
title: "nuxt task"
description: "在你的开发服务器上列出并运行 Nitro tasks。"
links:
  - label: Source
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/tree/main/packages/nuxt-cli/src/commands/task
    size: xs
---

`task` 命令使用正在运行的 `nuxt dev` 服务器，与项目公开的 [Nitro tasks](https://nitro.build/guide/tasks) 进行交互。传入 `--url` 可指定其他服务器。

## `nuxt task list`

<!--task-list-cmd-->
```bash [Terminal]
npx nuxt task list [ROOTDIR] [--cwd=<directory>] [--url=<url>] [--json]
```
<!--/task-list-cmd-->

![nuxt task list](/capture/output/nuxt-task-list.svg)

### 参数

<!--task-list-args-->
| 参数       | 描述                                             |
|------------|--------------------------------------------------|
| `ROOTDIR`  | Nuxt 项目的根目录（默认值：.）                   |
<!--/task-list-args-->

### 选项

<!--task-list-opts-->
| 选项                | 默认值 | 描述                                                                  |
|---------------------|--------|-----------------------------------------------------------------------|
| `--cwd=<directory>` |        | 指定 Nuxt 项目的根目录                                                |
| `--url=<url>`       |        | 要与之交互的 Nuxt 服务器 URL（默认值：正在运行的开发服务器）          |
| `--json`            |        | 将输出打印为 JSON                                                     |
<!--/task-list-opts-->

## `nuxt task run`

<!--task-run-cmd-->
```bash [Terminal]
npx nuxt task run <NAME> [ROOTDIR] [--cwd=<directory>] [--url=<url>] [--payload=<json>]
```
<!--/task-run-cmd-->

### 参数

<!--task-run-args-->
| 参数          | 描述                                             |
|---------------|--------------------------------------------------|
| `NAME=<name>` | 要运行的任务名称                                 |
| `ROOTDIR`     | Nuxt 项目的根目录（默认值：.）                   |
<!--/task-run-args-->

### 选项

<!--task-run-opts-->
| 选项                | 默认值 | 描述                                                                  |
|---------------------|--------|-----------------------------------------------------------------------|
| `--cwd=<directory>` |        | 指定 Nuxt 项目的根目录                                                |
| `--url=<url>`       |        | 要与之交互的 Nuxt 服务器 URL（默认值：正在运行的开发服务器）          |
| `--payload=<json>`  |        | 任务负载，可以是 JSON 对象，也可以是 `--payload.key=value` 对          |
<!--/task-run-opts-->

任务的结果会以 JSON 形式打印。可以提供单个 JSON 对象，也可以使用单独的键构建负载：

```bash [Terminal]
npx nuxt task run db:seed --payload '{"count":10}'
npx nuxt task run db:seed --payload.count=10
```

::note
Nitro 仅会在启用 tasks 时扫描你的 `tasks` 目录，因此没有公开任何任务的服务器可能只需要添加以下内容：

```ts [nuxt.config.ts]
export default defineNuxtConfig({
  nitro: {
    experimental: {
      tasks: true,
    },
  },
})
```
::

::read-more{to="https://nitro.build/guide/tasks" icon="i-simple-icons-nitro" target="\_blank"}
详细了解 Nitro tasks。
::
