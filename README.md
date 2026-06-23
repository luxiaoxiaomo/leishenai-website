# 雷神个人网站

OPC 践行者 · AI Agent 实践者 · HR Tech 15年

## 技术栈

- 纯静态 HTML/CSS/JS，零后端
- 暖色纸质风格（参考 AhaDiff 设计语言）
- 响应式设计，移动端适配
- 数据驱动（JSON 文件管理项目、报道）

## 本地开发

```bash
cd personal-website
python -m http.server 8080
```

访问 http://localhost:8080

## 部署

Cloudflare Pages / GitHub Pages 均可直接部署，无需构建步骤。

## 目录结构

```
├── index.html          首页
├── about.html          关于
├── projects.html       AI项目
├── portfolio.html      作品集
├── news.html           新闻报道
├── speaking.html       讲课 & 联系
├── blog/
│   └── index.html      博客
├── data/
│   ├── projects.json   项目数据
│   ├── news.json       报道数据
│   └── posts.json      博客数据
├── assets/
│   └── img/            图片资源
├── css/
│   ├── vars.css        CSS 变量
│   ├── base.css        基础样式 + 组件
│   └── nav.css         导航栏
└── js/                 JavaScript（内联在各页面）
```
