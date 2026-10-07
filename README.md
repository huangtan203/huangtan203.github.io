# 嵌入式 · RISC-V 学习笔记

基于 Hugo + PaperMod 的个人静态博客，通过 GitHub Actions 自动部署到 GitHub Pages。主题已内置在仓库中，无需联网拉取子模块。

## 本地写作

```bash
hugo server -D              # 本地预览 http://localhost:1313（含草稿）
hugo new content posts/新文章.md
```

文章头部 front matter 中 `draft: false` 才会被发布。

## 发布到 GitHub Pages（一次性配置）

1. 在 GitHub 新建**公开**仓库，名字必须为 `<你的用户名>.github.io`
2. 推送代码：

```bash
git remote add origin https://github.com/<你的用户名>/<你的用户名>.github.io.git
git add .
git commit -m "init: hugo + papermod blog"
git push -u origin main
```

3. 仓库 Settings → Pages → Build and deployment → Source 选择 **GitHub Actions**
4. 等 Actions 执行完成，访问 `https://<你的用户名>.github.io`

## 发布前必须替换的占位符

| 文件 | 占位符 | 说明 |
|---|---|---|
| hugo.yaml | `<你的GitHub用户名>`（2 处） | baseURL、菜单 GitHub 链接 |
| hugo.yaml | `<你的名字>` | params.author |
| README.md | `<你的用户名>` | 本文件的推送示例 |

## 绑定自己的域名（可选）

1. 购买域名（约 ¥50/年）
2. DNS 添加 CNAME 记录指向 `<你的用户名>.github.io`
3. 仓库 Settings → Pages → Custom domain 填入域名并开启 Enforce HTTPS
4. 把 hugo.yaml 的 baseURL 改成 `https://你的域名/`

## 目录结构

```text
content/posts/     文章（Markdown）
themes/PaperMod/   主题（已内置，更新主题时重新下载覆盖此目录）
.github/           GitHub Actions 自动部署配置
```
