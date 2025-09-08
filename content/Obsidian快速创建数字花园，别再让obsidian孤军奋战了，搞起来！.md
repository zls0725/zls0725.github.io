---
created: 2025-08-31T08:32
updated: 2025-09-06T13:28
title: Obsidian快速创建数字花园，别再让obsidian孤军奋战了，搞起来！
date: 2025-08-31T13:47:00
draft: false
description: 文章描述
tags:
categories:
slug:
🔗双链:
一句话总结:
---
### 使用 Hugo 制作 Obsidian 数字花园的详细步骤

数字花园是一种非线性知识展示方式，利用 Obsidian 的双链笔记（wikilinks，如 `[[链接]]`）和 Markdown 文件，通过 Hugo 生成静态网站，便于在线分享。以下是基于 2025 年 8 月 30 日当前生态的详细步骤，结合 Obsidian 和 Hugo 的最佳实践。
过程假设你有基本的命令行知识（如终端操作），并使用 Windows/macOS/Linux。核心工具：Obsidian（笔记管理）、Hugo（静态生成器）、Git（版本控制）、Vercel/Netlify（部署）。等等基礎知识你就可以做了，等等……是不是已经被吓跑了！
哈哈其实也没有那么难，真的很容易我也是个菜鸟零基础快速搭建。只要思路清晰还是很快的。跟着我一步一步操作就可以。

![Git一个神一般的的应用](https://images.hkhenry.com/2025-08-31-2025-08-31-09-42.avif)

**前提准备**：

- **安装 Obsidian**：下载 Obsidian（https://obsidian.md/），创建一个 Vault（知识库文件夹），存放你的笔记。笔记用 Markdown 格式，包含双链（如 `[[笔记标题]]`）。
- **安装 Git**：用于版本控制和部署（https://git-scm.com/）。
- **安装 Hugo**：下载最新版 Hugo（https://gohugo.io/installation/），例如 macOS 用 `brew install hugo`。（这是MAC）
- ![[2025-09-04-11-18.png]]
- 创建新项目

> [创建新项目]
> cd /Users/henry/Documents
> hugo new site my-new-hugo-site

cd my-new-hugo-site

当前目录下输入 `hugo server` 启动本地站点
![[2025-09-04-11-32.png]]

> [添加新主题]
> Hugo 默认是没有主题的，需要到 官网 去下载主题。我使用的主题是 Jimmy Cai 创作的 Stack 主题。接下来的部分内容会以此主题为例。

将主题下载完成后并解压至 themes 文件夹中，将 exampleSite 文件夹中的 content 和hugo.yaml 复制到主文件夹中，并删掉原来的 hugo.toml 和 Content/post/rich-content ，避免出现不兼容的错误。
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

- **Obsidian 插件**：安装 Obsidian Git（同步笔记到 GitHub）和 Dataview（可选，用于笔记查询）。国内用户可通过 Pkmer 社区（https://pkmer.cn/）获取插件。
- **选择主题**：推荐 Hugo 主题如 blowfish（简洁，支持双链）或 `Grdn`（专为 Obsidian 设计）。克隆主题到 Hugo 项目。
  -![[2025-09-05-13-12.png]]
  主题文件夹的名字叫什么就把文件名加入到配置文件保存
  ![[2025-09-05-13-13.png]]
  选择的额主题网站这就

**注意**：如果你的博客是三语言（中文、英文、日文），在 Hugo 配置中启用多语言支持（步骤 3）。整个过程大约需 1-2 天上手。

#### 步骤 1：准备 Obsidian 笔记

1. **组织笔记结构**：（有obsidian的可以忽略可以研究下两边文件夹怎么可以高效互通）

   - 在 Obsidian Vault 中创建一个文件夹结构，例如：

     ```
     my-vault/
     ├── notes/          # 所有笔记文件夹
     │   ├── note1.md    # 示例笔记：包含双链 [[note2]]
     │   ├── note2.md
     ├── assets/         # 图片、附件
     └── index.md        # 首页笔记（可选）
     ```
   - 为笔记添加 YAML front matter（Hugo 所需），例如在 note1.md 开头：

     ```yaml
     ---
     title: "笔记标题"
     date: 2025-08-30
     tags: ["知识管理", "Obsidian"]
     draft：false
     ---
     正文内容，链接到 [[note2]]。
     ```
   - 如果三语言，创建子文件夹如 `zh/`、`en/`、`ja/`，并在 front matter 添加 `language: zh`。
2. **处理 Obsidian 特有语法**：

   - 双链（`[[链接]]`）：Hugo 默认不支持，需要主题或脚本转换。使用 Enveloppe 插件（Obsidian 社区插件）将双链转为 Hugo 链接（如 `[链接](/notes/link)`）。
   - 嵌入（![]）：确保图片路径正确，存放在 `assets/`。
   - 测试渲染：在 Obsidian 中预览，确保笔记可读。
3. **同步笔记**：

   - 安装 Obsidian Git 插件，配置 GitHub 仓库（新建一个 repo，如 `my-digital-garden`）。
   - 提交笔记：插件自动 push 到 GitHub（或 Gitee 国内版）。

#### 步骤 2：设置 Hugo 项目

1. **初始化 Hugo 站点**：
2. ![](https://images.hkhenry.com/2025-08-31-2025-08-31-09-23.avif)

   - 在终端创建一个新文件夹（如 `my-hugo-garden`），运行：
     ```
     hugo new site my-hugo-garden
     cd my-hugo-garden
     ```
   - 这会生成基本结构：`content/`（放笔记）、`themes/`（放主题）、`config.toml`（配置文件）。
     ![https://themes.gohugo.io/themes](https://images.hkhenry.com/2025-08-31-2025-08-31-09-50.avif)
3. **添加主题**：

   - 克隆推荐主题：

     - 对于简单数字花园：`git submodule add https://github.com/janraasch/hugo-bearblog.git themes/hugo-bearblog`
     - 对于 Obsidian 专用：搜索 `Grdn` 主题
     - 下载下来放入网站文件夹「themes/」文件夹中
   - 在 `config.toml` 中启用主题：

     ```toml
     theme = "hugo-bearblog"  # 或 "grdn"
     ```

**本地预览**：

- 运行 hugo server 在 http://localhost:1313 预览网站。
- 如果包含草稿，运行 hugo server -D。
- 

2. **配置 Hugo**：

   - 编辑 `config.toml`：
     ```toml
     baseURL = "https://your-garden.vercel.app/"  # 你的域名
     languageCode = "en-us"  # 默认语言
     title = "我的数字花园"
     paginate = 10  # 分页大小

     [params]
       description = "我的 Obsidian 知识网络"
       showReadTime = false
       showToc = true  # 显示目录

     # 多语言支持（如果三语言）
     defaultContentLanguage = "zh"
     [languages]
       [languages.zh]
         title = "我的数字花园"
         weight = 1
       [languages.en]
         title = "My Digital Garden"
         weight = 2
       [languages.ja]
         title = "私のデジタルガーデン"
         weight = 3
     ```
   - 处理双链：如果主题不支持，添加自定义短代码（shortcode）到 `layouts/shortcodes/link.html`：
     ```html
     <a href="{{ .Get 0 | replaceRE "^/?" "/" | urlize }}">{{ .Get 1 | default (.Get 0) }}</a>
     ```

     在笔记中用 `{{< link "note2" >}}` 替代双链。
3. **导入 Obsidian 笔记到 Hugo**：

   - 复制 Obsidian 的 `notes/` 到 Hugo 的 `content/`。
   - 对于三语言：创建 `content/zh/`、`content/en/`、`content/ja/`，复制相应笔记。
   - 如果笔记多，使用 Python 脚本自动化转换（参考 ）：创建一个脚本处理双链和 front matter。
     示例脚本（Python）：
     ```python
     import os
     import re

     def convert_links(file_path):
         with open(file_path, 'r', encoding='utf-8') as f:
             content = f.read()
         # 转换 [[link]] 到 [link](/link)
         content = re.sub(r'\[\[(.+?)\]\]', r'[\1](/\1/)', content)
         with open(file_path, 'w', encoding='utf-8') as f:
             f.write(content)

     # 遍历笔记文件夹
     for root, dirs, files in os.walk('notes'):
         for file in files:
             if file.endswith('.md'):
                 convert_links(os.path.join(root, file))
     ```

     运行脚本后，复制到 `content/`。

#### 步骤 3：构建和预览网站

1. **生成站点**：

   - 运行 `hugo` 生成 `public/` 文件夹（静态 HTML）。
   - 如果三语言，确保 `config.toml` 配置正确，Hugo 会生成 `/zh/` 等子目录。
2. **本地预览**：

   - 运行 `hugo server -D`，浏览器访问 `http://localhost:1313/`。
   - 检查：双链是否转为链接？笔记是否显示？三语言切换是否正常（添加导航菜单到主题）？
   - 调整主题 CSS（`themes/hugo-bearblog/static/css/style.css`）以匹配 Obsidian 风格。
3. **优化数字花园特性**：

   - 添加知识图谱：用 JavaScript 插件（如 Graphviz）在主题中嵌入。
   - 搜索：集成 Lunr.js 或 Algolia 到 Hugo 主题。
4. 网页搭建

#### 步骤 4：部署网站

1. **版本控制**：
   - 初始化 Git：`git init`，添加文件 `git add .`，提交 `git commit -m "Initial commit"`。
   - 推送到 GitHub/Gitee：`git add`，`git push -u origin main`。

> [!代码块]
> git init
> git add .
> git commit -m "Initial commit"
> git remote add origin https://github.com/your-username/your-repo.git
> git push -u origin main

1. **选择部署平台**：
   - **Vercel**（推荐）：登录 Vercel（https://vercel.com/），导入 GitHub repo，选择 Hugo 框架，设置根目录为 `/`，构建命令 `hugo -D`。
     - 配置域名：添加 `your-garden.vercel.app` 或子路径 `/garden`。
     - 三语言：Vercel 自动处理路由如 `/zh/`。
   - **Netlify/GitHub Pages**：类似，拖拽 repo 或设置构建命令。
   - 国内用户：用 Gitee Pages 或阿里云 OSS 部署 `public/` 文件夹。
     [[Hugo 部署平台对比（Vercel vs Netlify vs GitHub Pages）]]

[[推荐Vercel部署]]

2. **自动化更新**：
   - Obsidian Git 插件自动 push 笔记。
   - Vercel 检测 Git 变更，自动构建。

#### 步骤 5：维护与扩展

1. **更新内容**：

   - 在 Obsidian 编辑笔记，push 到 Git，Hugo 重新构建。
   - 如果三语言，维护 `zh/en/ja` 文件夹。
2. **常见问题解决**：

   - 双链不工作：用 Enveloppe 插件或脚本转换。
   - 性能慢：Hugo 速度快，但笔记多时优化图片（用 WebP）。
   - SEO：添加 sitemap.xml 和 robots.txt 到 `config.toml`。
3. **扩展**：

   - 添加评论：集成 Disqus。
   - 多语言切换：主题中加语言按钮。
   - 知识图谱：用 Mermaid 或 Graphviz 短代码。

#### 步骤 6：测试与上线

- **测试**：本地预览后，部署到 Vercel，访问域名检查链接、语言切换、移动端响应。
- **上线**：自定义域名（Vercel 设置），监控访问量。
- **备份**：定期备份 Obsidian Vault 和 Git repo。

**注意事项**：

- **三语言**：确保笔记按语言文件夹组织，Hugo 会生成 `/zh/` 等路径。
- **挑战**：双链转换需脚本或插件，如果复杂，可用 Flowershow 替代 Quartz（见上个响应）。
- **成本**：免费（Hugo 开源，Vercel 免费层）。
- **国内优化**：用 Gitee 仓库，科学上网访问主题站。

这个方案将 Obsidian 笔记转为 Hugo 驱动的数字花园，适合知识分享。如果遇到问题（如主题安装），参考资源或社区。
