---
title: "nuxt add-template"
description: "在 Nuxt 应用中构建实体脚手架"
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/main/packages/nuxt-cli/src/commands/add-template.ts
    size: xs
---

<!--add-template-cmd-->
```bash [Terminal]
npx nuxt add-template <TEMPLATE> <NAME> [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--force] [--mode=<client|server>] [--method=<connect|delete|get|head|options|patch|post|put|trace>] [--global] [--api] [--pages] [--client] [--server] [--connect] [--delete] [--get] [--head] [--options] [--post] [--put] [--trace] [--patch]
```
<!--/add-template-cmd-->

`add-template` 命令会根据项目结构，在正确的目录中构建文件脚手架。它取代了 `nuxt add <template> <name>`，后者仍可运行，但已被弃用。

::read-more{to="/docs/api/commands/add"}
详细了解 `nuxt add`，它可以向你的应用添加模块和层。
::

## 参数

<!--add-template-args-->
| Argument                                                                                                                                                                      | Description                        |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| `TEMPLATE=<api\|app\|app-config\|component\|composable\|error\|layer\|layout\|middleware\|module\|page\|plugin\|server-middleware\|server-plugin\|server-route\|server-util>` | 指定要生成的模板 |
| `NAME`                                                                                                                                                                        | 指定生成文件的名称 |
<!--/add-template-args-->

## 选项

<!--add-template-opts-->
| Option                                                                    | Default | Description                                            |
|---------------------------------------------------------------------------|---------|--------------------------------------------------------|
| `--cwd=<directory>`                                                       | `.`     | 指定 Nuxt 项目的根目录        |
| `--logLevel=<silent\|info\|verbose>`                                      |         | 指定构建时的日志级别                           |
| `--force`                                                                 | `false` | 如果文件已存在则覆盖                |
| `--mode=<client\|server>`                                                 |         | 为组件或插件添加客户端或服务器后缀 |
| `--method=<connect\|delete\|get\|head\|options\|patch\|post\|put\|trace>` |         | 为 API 路由添加 HTTP 方法后缀              |
| `--global`                                                                |         | 创建全局路由中间件                         |
| `--api`                                                                   |         | 在 API 目录中创建服务器路由             |
| `--pages`                                                                 |         | 在 app 模板中包含 NuxtPage 和 NuxtLayout    |
| `--client`                                                                |         | `--mode client` 的简写                          |
| `--server`                                                                |         | `--mode server` 的简写                          |
| `--connect`                                                               |         | `--method connect` 的简写                       |
| `--delete`                                                                |         | `--method delete` 的简写                        |
| `--get`                                                                   |         | `--method get` 的简写                           |
| `--head`                                                                  |         | `--method head` 的简写                          |
| `--options`                                                               |         | `--method options` 的简写                       |
| `--post`                                                                  |         | `--method post` 的简写                          |
| `--put`                                                                   |         | `--method put` 的简写                           |
| `--trace`                                                                 |         | `--method trace` 的简写                         |
| `--patch`                                                                 |         | `--method patch` 的简写                         |
<!--/add-template-opts-->

**修饰符：**

某些模板接受一个额外的标志，用于向生成文件名添加后缀（例如 `.client` 或 `.get`）。`--mode` 和 `--method` 接受的每个值也都有对应的独立标志，因此 `--mode client` 和 `--client` 的作用相同。

文件会相对于你的 [`srcDir`](/docs/api/nuxt-config#srcdir) 写入，该目录默认为 `app/`；服务器文件则会相对于你的 [`serverDir`](/docs/api/nuxt-config#serverdir) 写入。以下路径均假定使用这些默认值。

```bash [Terminal]
# Generates `app/plugins/sockets.client.ts`
npx nuxt add-template plugin sockets --mode client
```

## `nuxt add-template component`

* 修饰符标志：`--mode`，或 `--client` / `--server`

```bash [Terminal]
# Generates `app/components/TheHeader.vue`
npx nuxt add-template component TheHeader
```

## `nuxt add-template composable`

```bash [Terminal]
# Generates `app/composables/foo.ts`
npx nuxt add-template composable foo
```

## `nuxt add-template layout`

```bash [Terminal]
# Generates `app/layouts/custom.vue`
npx nuxt add-template layout custom
```

## `nuxt add-template plugin`

* 修饰符标志：`--mode`，或 `--client` / `--server`

```bash [Terminal]
# Generates `app/plugins/analytics.ts`
npx nuxt add-template plugin analytics
```

## `nuxt add-template page`

```bash [Terminal]
# Generates `app/pages/about.vue`
npx nuxt add-template page about
```

```bash [Terminal]
# Generates `app/pages/category/[id].vue`
npx nuxt add-template page "category/[id]"
```

## `nuxt add-template middleware`

* 修饰符标志：`--global`

```bash [Terminal]
# Generates `app/middleware/auth.ts`
npx nuxt add-template middleware auth
```

## `nuxt add-template api`

* 修饰符标志：`--method`，或将方法作为独立标志（`--get`、`--post` 等）

```bash [Terminal]
# Generates `server/api/hello.ts`
npx nuxt add-template api hello
```

## `nuxt add-template server-route`

* 修饰符标志：`--api`，用于将路由写入 `server/api` 而不是 `server/routes`

```bash [Terminal]
# Generates `server/routes/webhook.ts`
npx nuxt add-template server-route webhook
```

## `nuxt add-template layer`

```bash [Terminal]
# Generates `layers/subscribe/nuxt.config.ts`
npx nuxt add-template layer subscribe
```

::note
解析后会位于项目外部的名称将被拒绝，因此请传入相对于项目的路径，且开头不能有斜杠，也不能包含 `..` 片段。
::
