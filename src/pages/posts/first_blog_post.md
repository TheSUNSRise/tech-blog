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

等待 Cloudflare 构建和部署完成

##### H5 For example

Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur vero esse non molestias eos excepturi, inventore atque cupiditate. Sed voluptatem quas omnis culpa, et odit.

###### H6 For example

Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur vero esse non molestias eos excepturi, inventore atque cupiditate. Sed voluptatem quas omnis culpa, et odit.

## Emphasis

Emphasis, aka italics, with _asterisks_ or _underscores_.

Strong emphasis, aka bold, with **asterisks** or **underscores**.

Strikethrough uses two tildes. ~~Scratch this.~~

## Blockquotes

> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can _put_ **Markdown** into a blockquote.

## Horizontal separator

This is a horizontal separator:

---

Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur vero esse non molestias eos excepturi, inventore atque cupiditate. Sed voluptatem quas omnis culpa, et odit.

---

## List types

### Ordered list

1. List item 1
2. List item 2
   1. Nested list item A
   2. Nested list item B
3. List item 3

### Unordered list

- List item
- List item
  - Nested list item
  - Nested list item
    - Double nested list item
    - Double nested list item
- List item

### Mixed list

1. First ordered list item
2. Another item
   - Unordered sub-list.
3. Actual numbers don't matter, just that it's a number
   1. Ordered sub-list
4. And another item.

## Links

[Inline-style link](https://www.google.com)

[Inline-style link with title](https://www.google.com "Google's Homepage")

[Reference-style link][arbitrary case-insensitive reference text]

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com

## Images

Images included in _\_posts_ folder are lazy loaded.

Inline-style:
![alt text](/src/images/random.jpeg "Logo Title Text 1")

## Table

| Tables        |      Are      | Cool |
| ------------- | :-----------: | ---: |
| col 3 is      | right-aligned | 1600 |
| col 2 is      |   centered    |   12 |
| zebra stripes |   are neat    |    1 |

| Markdown | Less      | Pretty     |
| -------- | --------- | ---------- |
| _Still_  | `renders` | **nicely** |
| 1        | 2         | 3          |

## Syntax highlight

```ts title="astro.config.mjs" showLineNumbers {1-2,5-6}
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

Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur vero esse non molestias eos excepturi, inventore atque cupiditate. Sed voluptatem quas omnis culpa, et odit.
Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur vero esse non molestias eos excepturi, inventore atque cupiditate. Sed voluptatem quas omnis culpa, et odit.
Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur vero esse non molestias eos excepturi, inventore atque cupiditate. Sed voluptatem quas omnis culpa, et odit.

```python showLineNumbers
s = "Python syntax highlighting"
print s
```

[Rin]: https://github.com/openRin/Rin
[memos]: https://github.com/usememos/memos
[GitHub]: https://github.com
[Cloudflare]: https://cloudflare.com
