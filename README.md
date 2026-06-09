# 牟磊的 GitHub Pages 简历站

这是一个基于 Jekyll 的个人简历主页，内容根据 `牟磊-嵌入式软件工程师.pdf` 整理生成。

## 本地预览

如果本机已经安装 Ruby 与 Bundler：

```bash
bundle install
bundle exec jekyll serve
```

然后访问 `http://127.0.0.1:4000`。

## GitHub Pages 部署

1. 将本目录提交到 GitHub 仓库。
2. 在仓库 `Settings -> Pages` 中选择部署分支。
3. GitHub Pages 会按 `_config.yml` 与 `Gemfile` 自动构建 Jekyll 站点。
