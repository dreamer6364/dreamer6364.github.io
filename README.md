# 我的笔记（Astro 极简站）

用 [Astro](https://astro.build) 搭的**本地优先** Markdown 笔记站，已发布到 https://dreamer6364.github.io/ 。


## 怎么写笔记

1. 打开 `src/content/posts/`
2. 新建一个 `.md` 文件（直接平铺，不用建子文件夹），按下面格式写：

```md
---
title: 文章标题
date: "2026-08-19"      ← 注意日期必须加英文引号
tags: ["标签1", "标签2"]
---

# 正文大标题

这里写内容，支持 Markdown：**加粗**、`代码`、列表、表格、代码块等。
```

3. 本地预览：在项目根目录运行 `npm run dev`，打开 http://localhost:4321/
4. 发布到线上（让别人也能看）：

```bash
git add -A
git commit -m "写了一条笔记"
git push
```

等一两分钟，GitHub Actions 会自动重新部署，线上 https://dreamer6364.github.io/ 就更新了。

## 目录结构

```
src/
  content.config.ts     # 笔记集合配置（title/date/tags）
  content/posts/        # ← 你写笔记的地方，每篇一个 .md
  layouts/BaseLayout.astro
  pages/
    index.astro         # 笔记列表（首页）
    blog/[...id].astro  # 文章详情
    tags/index.astro    # 标签云
    tags/[tag].astro    # 单个标签下的笔记
```

## 常用命令

| 命令 | 作用 |
| --- | --- |
| `npm run dev` | 本地预览（http://localhost:4321） |
| `npm run build` | 生成静态站点到 `dist/` |
| `git push` | 发布到线上 |

## 注意

- `date` 字段必须写成字符串 `"2026-08-19"`（带引号），否则构建报错。
- 笔记都是纯 `.md` 文本，永不锁定在某个软件里。
