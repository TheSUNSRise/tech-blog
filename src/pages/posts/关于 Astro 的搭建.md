---
layout: ../../layouts/post.astro
title: "关于 Astro 的搭建"
pubDate: 2024-12-08
description: "众所周知，搭了博客后的第一篇博客一定是写怎么搭博客！"
author: "S"
excerpt: 众所周知，搭了博客后的第一篇博客一定是写怎么搭博客！
image:
  src:
  alt:
tags: ["Astro", "折腾"]
---

这已经不是我搭的第一个博客了，有 [Rin], [memos] 等等... 用着都挺不错的，但是总是出于某些原因没有继续下去 ~~(太懒了🤣~~

但是总得继续折腾吧！

## 关于 Astro

前端框架 Astro 是一个使用 JavaScript 构建 Web 应用程序的工具。旨在简单的创建快速、可靠且易于维护的 Web 应用程序。最适合构建像博客、营销网站、电子商务网站这样的以内容驱动的网站的 Web 框架。

Astro 支持多种前端框架，包括 React、Vue 和 Svelte，可以帮助开发人员更轻松地使用这些框架来构建 Web 应用程序。并且支持多个平台 SSR 和静态部署。

我就部署在 [Cloudflare] 上面吧，我已经离不开**赛博菩萨**了😋

## 部署 Astro 至 Cloudflare Pages

Cloudflare Pages 是一个供前端开发人员协作和部署静态 (JAMstack) 或 SSR 网站的平台。

### 前提条件

开始之前，你需要：

- 一个 [Cloudflare] 账号。如果还没有，可以现在免费去 [Cloudflare] 官网注册一个。
- 你的源代码存储在 [GitHub] 或者 GitLab 仓库里。

### 使用 Git 部署

1. 将代码提交到 Git 仓库中。
2. 在 Cloudflare Pages 设置一个新项目。
3. 登录 Cloudflare 控制台并在选择 Workers 和 Pages > 概述。
4. 在概述页面中，选择 Pages 标签页，接着选择 连接导 Git 选项。
5. 选择你的账号和想部署的 Git 项目并点击开始设置。
6. 使用以下的构建设置：
   - 框架预设: `Astro`
   - 构建命令: `npm run build`
   - 构建输出目录: `dist`
7. 点击保存并部署按钮。

等待 Cloudflare 构建和部署完成。

#### 构建失败 问题解决

```sh title="Cloudflare 错误信息" showLineNumbers {5-7}
14:27:07 [build] 12 page(s) built in 3.02s
14:27:07 [build] Complete!
Finished
Note: No functions dir at /functions found. Skipping.
Validating asset output directory
Error: Output directory "dist" not found.
Failed: build output directory not found.
```

找了半天，发现代码打包配置里面有个 vercel 的配置。

```ts title="astro.config.mjs" showLineNumbers {2,5-10}
import { defineConfig } from "astro/config";
import vercelStatic from "@astrojs/vercel/static";

export default defineConfig({
  output: "static",
  adapter: vercelStatic({
    webAnalytics: {
      enabled: true,
    },
  }),
});
```

应该是作者用的 vercel 部署，我这里不需要这些配置，所以删除重新部署就好了。

部署完成:
![部署完成](/public/images/Cloudflare.png "部署完成")

#### 自定义域名

如果你有域名托管在 Cloudflare 上面，那自定义域名就比较简单了。

1. 在 Workers 和 Pages 中找到刚刚部署完成的应用程序。
2. 在详情页面中，选择 自定义域 标签页，接着点击 设置自定义域 选项。
3. 填入已经在 Cloudflare 中托管的域名，点击继续。
  ![自定义域1](/public/images/zdyy1.png "自定义域1")
4. 确认 DNS 记录值，点击 激活域 。Cloudflare 会帮我们自动解析 DNS.
  ![自定义域2](/public/images/zdyy2.png "自定义域2")
5. 添加成功，显示正在验证。
  ![自定义域3](/public/images/zdyy3.png "自定义域3")
6. 等待几分钟，访问域名就好了。

[Rin]: https://github.com/openRin/Rin
[memos]: https://github.com/usememos/memos
[GitHub]: https://github.com
[Cloudflare]: https://cloudflare.com
