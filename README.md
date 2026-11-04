# xijiangzhu 的技术博客

这是一个使用 [Hugo](https://gohugo.io/) 生成的个人技术博客，采用 [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 主题。网站以静态文件形式发布，主要记录 Linux、数据库、容器、Kubernetes、网络和自动化相关的实践，也收录个人随笔。

线上地址：[https://blog.lenhon.com/](https://blog.lenhon.com/)

## 技术栈

- **静态站点生成器：** Hugo
- **主题：** PaperMod，主题文件位于 `themes/PaperMod/`
- **文章格式：** Markdown
- **站内搜索：** PaperMod 搜索页面及首页 JSON 输出
- **评论：** Giscus，使用 GitHub Discussions
- **访问统计：** Busuanzi
- **订阅：** Hugo RSS 输出

## 本地预览

先安装 Hugo，再在项目根目录运行：

```bash
hugo server 
```

开发服务器会显示本地访问地址，修改内容后浏览器会自动刷新。若要同时预览标记为草稿的文章：

```bash
hugo server -D
```

## 生成网站

```bash
hugo --minify
```

生成结果位于 `public/` 目录，可部署到支持静态网站的托管服务。`public/` 是构建产物，已加入 `.gitignore`，无需提交到源码仓库。

## 添加文章

在 `content/posts/` 下新建 Markdown 文件。可复制以下 Front Matter 并按需修改：

```yaml
---
title: "文章标题"
date: 2026-11-03T12:00:00+08:00
draft: false
description: "文章摘要，用于列表展示和搜索引擎摘要。"
categories:
  - Linux
tags:
  - 运维
  - 命令行
---

在这里开始撰写正文。

<!-- more -->

正文剩余内容……
```

说明：

- `draft: true` 的文章默认不会出现在正式构建结果中；本地可用 `hugo server -D` 预览。
- `description` 用于补充文章简介；省略时，Hugo 会根据正文生成摘要。
- `categories` 和 `tags` 支持多项。分类适合表示较大的主题，标签用于描述更具体的技术或工具。
- `<!-- more -->` 用于指定首页和文章列表中摘要的截断位置。
- 文章日期使用站点配置的 `DateFormat` 显示。

项目中的文章分类目录包括 `content/categories/`，标签目录为 `content/tags/`；具体文章存放在 `content/posts/`。

## 页面与资源

- 关于页面：`content/about/_index.md`
- 文章归档页面：`content/archives/_index.md`
- 文章列表说明：`content/posts/_index.md`
- 搜索页面：`content/search/_index.md`
- 站点配置：`hugo.yaml`
- 自定义样式：`assets/css/extended/`
- 自定义模板：`layouts/partials/`
- 静态资源：`static/`，包括网站图标和头像
- Hugo 文章模板：`archetypes/default.md`

自定义模板放在根目录的 `layouts/` 中，以覆盖或扩展主题对应模板。调整主题样式时，优先修改 `assets/css/extended/`，避免直接改动 `themes/PaperMod/`，这样更容易维护主题更新。

## 站点配置

常用配置集中在 `hugo.yaml`：

- `baseURL`、`title`、`languageCode`：站点地址、名称和语言
- `pagination.pagerSize`：文章列表每页数量
- `menu.main`：顶部导航菜单及排序
- `params.homeInfoParams`：首页简介
- `params.socialIcons`：首页 GitHub、邮箱和 RSS 图标
- `params.ShowToc`、`params.TocOpen`：文章目录显示与默认展开状态
- `params.ShowReadingTime`、`params.ShowWordCount`：阅读时间和字数信息
- `params.comments` 与 `params.giscus`：评论功能及 Giscus 配置
- `params.busuanzi.enable`：访问量统计开关
- `outputs.home`：首页生成 HTML、RSS 和 JSON，以支持站内搜索及 RSS 订阅

修改 Giscus 时，需要在 GitHub 仓库启用 Discussions，并确认 `repo`、`repoId`、`category` 和 `categoryId` 与 Giscus 配置一致。访问统计依赖 Busuanzi 的在线服务；本地预览数据与线上访问统计可能不同。

## 搜索引擎与发布

站点启用了 Hugo 的 `robots.txt` 生成。构建时 Hugo 会生成站点地图；发布后可将 `https://blog.lenhon.com/sitemap.xml` 提交给搜索引擎站长工具。

推送源码后，按仓库当前配置的托管或部署流程发布 `public/` 中的静态文件。不要把本地构建缓存、锁文件或 `public/` 构建结果作为源码提交。

## 许可证

博客文章及本站自定义代码的权利归作者所有；PaperMod 主题按其项目采用的 MIT 许可证发布。引用或转载内容时，请遵守对应内容的许可说明并注明来源。
