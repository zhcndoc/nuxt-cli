---
title: "nuxt add-template"
description: "在 Nuxt 应用中构建实体脚手架"
links:
  - label: 来源
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/3.x/packages/nuxi/src/commands/add-template.ts
    size: xs
---

<!--add-template-cmd-->
```bash [Terminal]
npx nuxt add-template <TEMPLATE> <NAME> [--cwd=<directory>] [--logLevel=<silent|info|verbose>] [--force]
```
<!--/add-template-cmd-->

::note
`nuxt add <TEMPLATE> <NAME>` 仍然有效，但已弃用，建议使用 `nuxt add-template`
::

::read-more{to="/docs/api/commands/add"}
详细了解 `nuxt add`，它可以将 Nuxt 模块添加到你的应用中
::

## 参数

<!--add-template-args-->
| 参数       | 描述                                                                                                                                                                                                      |
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TEMPLATE` | 指定要生成的模板（选项：<api\|app\|app-config\|component\|composable\|error\|layer\|layout\|middleware\|module\|page\|plugin\|server-middleware\|server-plugin\|server-route\|server-util>） |
| `NAME`     | 指定生成文件的名称                                                                                                                                                                               |
<!--/add-template-args-->

## 选项

<!--add-template-opts-->
| 选项                                 | 默认值 | 描述                              |
|--------------------------------------|---------|------------------------------------------|
| `--cwd=<directory>`                  | `.`     | 指定工作目录            |
| `--logLevel=<silent\|info\|verbose>` |         | 指定构建时的日志级别             |
| `--force`                            | `false` | 强制覆盖已存在的文件 |
<!--/add-template-opts-->

**修饰符：**

某些模板支持额外的修饰符标志，用于向名称添加后缀（例如 `.client` 或 `.get`）。

生成的文件会写入相对于你的 [`srcDir`](/docs/api/nuxt-config#srcdir) 的路径中，该路径默认为项目根目录。以下路径均假设使用默认设置。

```bash [Terminal]
# Generates `/plugins/sockets.client.ts`
npx nuxt add-template plugin sockets --client
```

## `nuxt add-template component`

* 修饰符标志：`--mode client|server` 或 `--client` 或 `--server`

```bash [Terminal]
# Generates `components/TheHeader.vue`
npx nuxt add-template component TheHeader
```

## `nuxt add-template composable`

```bash [Terminal]
# Generates `composables/foo.ts`
npx nuxt add-template composable foo
```

## `nuxt add-template layout`

```bash [Terminal]
# Generates `layouts/custom.vue`
npx nuxt add-template layout custom
```

## `nuxt add-template plugin`

* 修饰符标志：`--mode client|server` 或 `--client` 或 `--server`

```bash [Terminal]
# Generates `plugins/analytics.ts`
npx nuxt add-template plugin analytics
```

## `nuxt add-template page`

```bash [Terminal]
# Generates `pages/about.vue`
npx nuxt add-template page about
```

```bash [Terminal]
# Generates `pages/category/[id].vue`
npx nuxt add-template page "category/[id]"
```

## `nuxt add-template middleware`

* 修饰符标志：`--global`

```bash [Terminal]
# Generates `middleware/auth.ts`
npx nuxt add-template middleware auth
```

## `nuxt add-template api`

* 修饰符标志：`--method`（可接受 `connect`、`delete`、`get`、`head`、`options`、`patch`、`post`、`put` 或 `trace`），或者你也可以直接使用 `--get`、`--post` 等标志。

```bash [Terminal]
# Generates `server/api/hello.ts`
npx nuxt add-template api hello
```

## `nuxt add-template layer`

```bash [Terminal]
# Generates `layers/subscribe/nuxt.config.ts`
npx nuxt add-template layer subscribe
```
