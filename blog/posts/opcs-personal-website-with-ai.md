# 一个 OPC 践行者的个人网站：从 0 到上线，AI 全程协作

## 缘起

作为 OPC（One Person Company）践行者，我一直在用 AI Agent 团队做项目。但有个问题：别人想了解我，找不到一个入口。

公众号文章是碎片化的，飞书文档是内部协作的，朋友圈是临时的。我需要一个**完整的、始终在线的、自己可控的个人网站**。

于是，我和 Claude 坐下来，从一句话需求到网站上线，全程 AI 协作。

---

## 一句话需求

> 我要做一个个人网站，我有域名，参考 AhaDiff 的风格，包含个人简介、作品集、AI 项目展示、博客、讲课内容。

就这一句。没有原型图，没有设计稿，没有需求文档。

---

## AI 协作全流程

### 第一步：生成 PRD

我用 [乔木 AI PRD](https://github.com/joeseesun/qiaomu-ai-prd) 技能，一句话生成了完整的 11 章 PRD，包括：

- 产品定位：个人品牌静态网站
- 6 个核心页面
- 数据模型（JSON 驱动）
- 技术架构（纯静态 HTML/CSS/JS）
- 性能指标
- 开发优先级（P0/P1/P2）

### 第二步：确定设计风格

Claude 抓取了参考网站 AhaDiff 的实际 CSS 变量，提取出完整的暖色纸质风格：

```css
--paper: #FAF8F2;       /* 温暖纸白 */
--ink: #1C1B18;         /* 墨色文字 */
--accent: #D27050;      /* 暖橙强调 */
--hair: #E6E3D8;        /* 细线分隔 */
--font-serif: 'Newsreader', 'Noto Serif SC', Georgia, serif;
```

不是常见的深色极客风，而是有质感的纸质书卷气。这才是我想要的。

### 第三步：读取记忆，填充真实内容

Claude 读取了我之前存在 Claude Code 记忆系统里的项目信息：

- AI 原生组织五层治理栈
- 知识治理系统（知识原子元模型 + 10 层 Harness）
- 数据治理 Agent OS
- 问查办一体化 HR AI Agent
- 微信群聊归档助手
- HR AI 龙虾实战营

这些都是真实项目，不是编的。AI 从记忆里提取，比我自己整理还快。

### 第四步：编码，按优先级推进

P0（1-2 天）：
- CSS 变量系统 + 基础样式
- 导航组件（桌面 + 移动端）
- 首页 Hero + 精选项目
- AI 项目页（JSON 驱动渲染）
- 讲课页 + 公众号 + 联系我弹窗

P1（3-5 天）：
- 关于页（时间线组件）
- 博客列表页
- 作品集页
- 新闻报道模块
- 首页新闻卡片

技术选型：**零框架，纯静态**。没有 React、没有 Vue、没有构建工具。双击 HTML 就能打开，push 到 GitHub 就能部署。

### 第五步：抓取真实新闻

中国新闻网有一篇关于 OPC 创业的报道，但页面是客户端渲染，普通抓取拿不到内容。Claude 通过 CDP（Chrome DevTools Protocol）直接操控浏览器，成功提取了文章标题和正文：

> **AI技术赋能 浙江杭州"OPC"创业悄然兴起**
> ——中国新闻网 2026-05-31

这篇报道直接作为"媒体报道"模块展示在网站上。

### 第六步：一键部署

```bash
# 创建 Cloudflare Pages 项目
npx wrangler pages project create leishenai-website

# 部署
npx wrangler pages deploy . --project-name=leishenai-website
```

18 个文件，2 秒上传，部署完成。

绑定自定义域名 `leishenai.ccwu.cc`，在 Cloudflare Dashboard 点两下就行。

---

## 最终架构

```
personal-website/
├── index.html          首页
├── about.html          关于
├── projects.html       AI 项目
├── portfolio.html      作品集
├── news.html           新闻报道
├── speaking.html       讲课 & 联系
├── blog/index.html     博客
├── data/
│   ├── projects.json   项目数据
│   ├── news.json       报道数据
│   └── posts.json      博客数据
├── assets/img/         图片资源
├── css/                样式文件
└── CNAME               自定义域名
```

内容更新只需改 JSON 文件，不用碰代码。

---

## 几个关键决策

| 决策 | 选择 | 原因 |
|------|------|------|
| 框架 | 无 | 个人网站不需要，双击就能看 |
| 部署 | Cloudflare Pages | 免费、快、自带 CDN |
| 内容管理 | JSON 文件 | AI 可以直接改，比 CMS 轻 |
| 设计风格 | 暖色纸质 | 参考了 AhaDiff，不是千篇一律的深色极客风 |
| 联系方式 | 弹窗微信二维码 | 避免公网暴露个人微信 |

---

## OPC 模式的实际验证

这个项目本身就是 OPC 模式的一个缩影：

- **我做决策**：风格方向、内容取舍、域名选择
- **AI 做执行**：PRD 生成、CSS 编码、页面开发、新闻抓取、部署
- **我审核**：每个阶段看效果，调整方向

从"我想做个网站"到"网站上线"，全程大约 3 小时。如果我自己从零写，至少需要 2-3 天。

这不是 AI 替代人，是 AI 放大人。一个人 + AI Agent 团队，产出效率接近一个小型工作室。

---

## 后续计划

- [ ] 补充博客文章（从公众号精选）
- [ ] 添加更多新闻报道
- [ ] 添加 OG 标签（社交分享预览）
- [ ] 深色/浅色模式切换
- [ ] 博客搜索功能
- [ ] Google Analytics 埋点

---

**网站地址**：[leishenai.ccwu.cc](https://leishenai.ccwu.cc)

**GitHub**：[github.com/luxiaoxiaomo/leishenai-website](https://github.com/luxiaoxiaomo/leishenai-website)

如果你也是 OPC 践行者，欢迎交流。
