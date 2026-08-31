---
title: 'nuxt cleanup'
description: '移除常见的 Nuxt 生成文件和缓存。'
links:
  - label: Source
    icon: i-simple-icons-github
    to: https://github.com/nuxt/cli/blob/3.x/packages/nuxi/src/commands/cleanup.ts
    size: xs
---

<!--cleanup-cmd-->
```bash [Terminal]
npx nuxt cleanup [ROOTDIR] [--cwd=<directory>]
```
<!--/cleanup-cmd-->

`cleanup` 命令会移除常见的 Nuxt 生成文件和缓存，包括：

- `.nuxt`
- `.output`
- `dist`
- `node_modules/.vite`
- `node_modules/.cache`

## 参数

<!--cleanup-args-->
| Argument      | Description                                    |
|---------------|------------------------------------------------|
| `ROOTDIR="."` | 指定工作目录（默认值：`.`） |
<!--/cleanup-args-->

## 选项

<!--cleanup-opts-->
| Option              | Default | Description                                                                      |
|---------------------|---------|----------------------------------------------------------------------------------|
| `--cwd=<directory>` |         | 指定工作目录，此选项的优先级高于 ROOTDIR（默认值：`.`） |
<!--/cleanup-opts-->
