# SuNote

SuNote 是一個用來記錄前端開發、JavaScript、AI Agent 與自動化工具學習歷程的個人筆記網站。

[線上瀏覽](https://su-note.vercel.app/) · [GitHub Repository](https://github.com/Tissuu/SuNote)

## 專案特色

- 使用 Markdown／MDX 撰寫及管理文章
- 透過標籤分類學習內容
- 支援深色與淺色模式
- 響應式設計，適合不同尺寸的裝置
- 提供文章導覽與 RSS 訂閱
- 使用 Astro 產生靜態網站，兼顧載入速度與 SEO

## 學習內容

本站主要記錄：

- 前端開發與 JavaScript
- 程式語法與實作筆記
- Artificial Intelligence 與 AI Agent
- n8n 等自動化工具
- 每日學習過程與心得

## 使用技術

- [Astro](https://astro.build/)
- [TypeScript](https://www.typescriptlang.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Astro Content Collections](https://docs.astro.build/en/guides/content-collections/)
- [MDX](https://mdxjs.com/)
- [Vercel Analytics](https://vercel.com/analytics)

## 本機執行

```bash
git clone https://github.com/Tissuu/SuNote.git
cd SuNote
npm install
npm run dev
```

啟動後開啟 [http://localhost:4321](http://localhost:4321)。

## 開發指令

| 指令 | 用途 |
| --- | --- |
| `npm run dev` | 啟動本機開發伺服器 |
| `npm run build` | 建置正式環境版本 |
| `npm run preview` | 預覽建置結果 |

## 新增文章

在 `src/content/posts/` 建立 `.md` 或 `.mdx` 檔案，並加入文章資訊：

```md
---
title: 文章標題
date: 2026-06-11
excerpt: 文章摘要
image: /images/example.jpg
tags: [JavaScript, Astro]
---

文章內容寫在這裡。
```

文章圖片可放在 `public/images/`，並使用 `/images/檔案名稱` 引用。

## 部署

本專案部署於 Vercel：

https://su-note.vercel.app/

---

Built with Astro, TypeScript, and Tailwind CSS.

Original design based on [Brook 2](https://templatedeck.com/templates/brook2) by [TemplateDeck](https://templatedeck.com/).
