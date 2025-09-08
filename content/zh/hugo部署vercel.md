---
created: 2025-09-03T21:05
updated: 2025-09-06T13:28
title: 感恩复盘-000
date: 2025-09-07T18:05:00-07:00
draft: false
categories:
  - 技术
  - 博客
tags:
  - gratitude-diary
description: 文章的简短描述，用于 SEO 和社交媒体分享
slug:
featuredImage: 网页图片封面
author: 香港Henry
keywords:
weight: 文章的排序权重（值越小越靠前），用于置顶或自定义排序。
aliases:
  - 旧 URL 的别名，用于重定向（当文章 URL 变更时）。
hidden: false 表示在文章页中显示封面图
一句话总结: 重点
---
# 文章标题

这里是正文内容，支持 Markdown 语法...

## 子标题

- 列表项 1
- 列表项 2

![图片描述](2025-09-03-关键词.avif)

#### **精简、结构化、视觉化、实践导向**https://brume.top/p/build-your-personal-blog-with-hugo/

### 3. **如何确认 Vercel 部署成功并查看网址**

要确认你的 Hugo 网站是否通过 Vercel 部署成功并找到访问网址，请按照以下步骤：

- **登录 Vercel 仪表板**：
  1. 打开 Vercel 官网（vercel.com），登录你的账户。
  2. 找到与你的 GitHub 仓库关联的 Vercel 项目（通常以项目名或仓库名命名）。
- **检查部署状态**：
  1. 点击项目，进入 **Deployments**（部署）选项卡。
  2. 查看最新的部署记录：
     - 如果状态为 **Ready** 或 **Deployed**（绿色），表示部署成功。
     - 如果状态为 **Error**（红色），点击查看日志，检查错误原因（例如 Hugo 配置文件错误或缺少文件）。
- **查找网站网址**：
  1. 在项目页面顶部或 **Domains**（域名）部分，Vercel 会列出你的网站 URL，通常是：
     - 默认 URL：https://your-project-name.vercel.app。
     - 如果配置了自定义域名，会显示你的域名（例如 https://yourdomain.com）。
  2. 复制该 URL，在浏览器中打开，确认网站是否正常加载。
- **验证 Hugo 构建**：
  - 确保你的 GitHub 仓库包含 Hugo 的源文件（包括 config.toml 或 config.yaml 和 content 文件夹等）。
  - 在 Vercel 的项目设置中，确认 **Framework Preset** 设置为 **Hugo**，并且构建命令和输出目录正确（默认构建命令为 hugo --gc --minify，输出目录为 public）。
