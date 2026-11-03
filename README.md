# xijiangzhu 的技术博客

基于 [Hugo](https://gohugo.io/) 和 [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 构建的个人技术博客，记录 Linux、数据库、容器、Kubernetes 及日常技术实践。

## 本地运行

安装 Hugo 后，在项目根目录执行：

```bash
hugo server -D
```

然后访问终端显示的本地地址。`-D` 会同时预览草稿文章。

## 构建

```bash
hugo --minify
```

生成的静态网站文件位于 `public/` 目录。该目录已加入 `.gitignore`。

## 主要功能

- PaperMod 响应式主题与浅色、深色模式
- 文章分类、标签、归档和站内搜索
- 文章目录、阅读时间和字数统计
- 基于标签及分类的相关文章推荐
- Giscus 评论、Busuanzi 访问统计和 RSS 订阅
- SEO 元数据及 Hugo 自动生成的站点地图

## 项目结构

```text
content/       页面、文章、分类和标签内容
layouts/       对主题模板的局部覆盖
assets/css/    自定义样式
static/        favicon、头像等静态资源
themes/        PaperMod 主题
hugo.yaml      Hugo 站点配置
```

新文章放在 `content/posts/` 下，使用 Markdown 编写，并在 Front Matter 中设置标题、日期、分类和标签。
