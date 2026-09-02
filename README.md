<p align="center">
  <img src="assets/logo.png" alt="XHS Sync Logo" width="100" />
</p>

<h1 align="center">XHS Sync · 小红书 → Obsidian</h1>

<p align="center">
  将小红书的<strong>收藏、点赞、帖子、搜索结果、订阅账号</strong>一键同步到 Obsidian<br/>
  图片/视频本地化 · AI 智能分类 · 热点分析日报 · 全程自动化<br/><br/>
  Sync Xiaohongshu (RedNote) bookmarks, likes, posts, searches and followed accounts to Obsidian — with media, AI tagging and hotspot reports.
</p>

<p align="center">
  <a href="https://github.com/unintended0x/xhs2obsidian/releases/latest">
    <img src="https://img.shields.io/github/v/release/unintended0x/xhs2obsidian?style=flat-square&color=ff2442" alt="Latest Release" />
  </a>
  <a href="https://github.com/unintended0x/xhs2obsidian/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/unintended0x/xhs2obsidian?style=flat-square" alt="License" />
  </a>
  <img src="https://img.shields.io/badge/Obsidian-Desktop%20Only-7c3aed?style=flat-square&logo=obsidian" alt="Desktop Only" />
  <img src="https://img.shields.io/badge/platform-macOS%20%7C%20Windows%20%7C%20Linux-blue?style=flat-square" alt="Platform" />
</p>

<p align="center">
  <a href="#中文说明">中文</a> · <a href="#english">English</a>
</p>

<p align="center">
  <img src="assets/screenshot-vault.png" alt="Obsidian Vault 效果预览" width="780" />
</p>

---

## 中文说明

### ✨ 功能一览

| 功能 | 说明 |
|------|------|
| 📚 **五类内容同步** | 收藏 · 点赞 · 个人帖子 · 关键词搜索 · 订阅账号 |
| 🖼️ **媒体本地化** | 图片和视频自动下载，离线永久可查 |
| 🤖 **AI智能分类** | 接入任意 OpenAI 兼容 API，自动归入自定义分类目录 |
| 💬 **评论抓取** | 可选同步主评论 + 子评论，设置抓取上限 |
| ⏱️ **定时自动同步** | 后台定时运行，新内容自动入库 |
| 🔄 **增量同步** | 记录已同步 ID，不重复拉取 |
| 📁 **专辑目录** | 收藏夹按专辑自动分子目录 |
| 📝 **结构化笔记** | frontmatter 记录 id、author、tags、likes、comments 等完整元数据 |

---

### 🗂️ Vault 文件结构

同步后在 Obsidian Vault 中自动生成：

```
RedNote/
├── Bookmarks/              # 收藏的笔记
│   ├── [专辑名]/           # 开启"同步专辑"后按专辑分组
│   └── 笔记标题.md
├── Posts/                  # 个人发布的帖子
├── Likes/                  # 点赞的帖子
├── Search/
│   └── [关键词]/           # 每个关键词独立目录
│       └── 笔记标题.md
├── Users/
│   └── [博主昵称]/
│       ├── _profile.md     # 博主主页档案
│       └── 笔记标题.md
├── Hotspots/
│   └── [分类名]/
│       ├── 笔记标题.md
│       └── 报告/
│           └── 2026-05-28.md   # AI 热点日报
└── Media/
    ├── 笔记标题/           # 每篇笔记独立媒体文件夹
    │   ├── 1.jpg
    │   └── video.mp4
    └── avatars/            # 评论头像
```

每篇笔记的 Markdown 示例：

```markdown
---
id: "6a92b65f000000002303cb65"
title: "感觉所有的博主，都该看看快手程一笑的分享"
author: "xxx"
type: "bookmarks"
url: "https://www.xiaohongshu.com/explore/6a92b65f000000002303cb65?xxxx..."
tags: ["博主", "自媒体", "2026光合大会", "创作", "经验"]
category: "xxx"
createdAt: "2026-08-29T10:37:19.000Z"
syncedAt: "2026-08-31 16:03:27"
likes: 1279
comments: 11
---

笔记正文…

![](../Media/感觉所有的博主，都该看看快手程一笑的分享/1.jpg)
```

---

### 🚀 安装

#### 方式一：从 Release 安装

1. 前往 [**Releases**](https://github.com/unintended0x/xhs2obsidian/releases/latest) 下载最新 `xhs2obsidian-x.x.x.zip`
2. 解压后将文件夹复制到 Vault 的 `.obsidian/plugins/` 目录
3. Obsidian → **设置 → 第三方插件** → 关闭「安全模式」→ 刷新列表 → 启用 **XHS Sync**

#### 方式二：BRAT 安装（自动更新）

1. 在 Obsidian 社区插件中安装并启用 **BRAT**（Beta Reviewer's Auto-update Tool）
2. 打开 BRAT → 选择 **Add Beta plugin**
3. 输入仓库地址：

   ```
   https://github.com/unintended0x/xhs2obsidian
   ```

4. 安装完成后，在 Obsidian **设置 → 第三方插件** 中启用 **XHS Sync**
5. BRAT 会跟随 GitHub Release 自动检测并更新到最新版本

> **注意：** 本插件依赖 Electron WebView，仅支持 Obsidian **桌面端**（macOS / Windows / Linux）。

---

### 📖 快速开始

#### 第一步：登录小红书

1. Obsidian → **设置 → XHS Sync**
2. 点击「**登录**」→ 在内置浏览器中完成扫码 / 手机号登录
3. 登录后点击「**登录完成，提取 Cookie**」
4. 状态栏显示「已登录：你的昵称」即成功

> Cookie 有效期约 30–90 天，过期后重新登录即可，不影响已同步笔记。

#### 第二步：选择同步内容

在设置中选择同步目标（收藏 / 点赞 / 个人帖子），或配置关键词搜索、账号订阅。

#### 第三步：开始同步

| 方式 | 操作 |
|------|------|
| 快速同步 | 点击左侧 Ribbon 栏云下载图标 |
| 命令面板 | `Cmd/Ctrl+P` → 搜索「同步收藏 / 同步点赞 / 关键词搜索…」|
| 自动同步 | 在设置中开启「定时自动同步」 |

同步进度以通知气泡实时显示，完成后提示新增条数。

---

### ⚙️ 主要配置项

#### 同步设置

| 设置项 | 默认值 | 说明 |
|--------|--------|------|
| 存储目录 | `RedNote` | Vault 内根目录名 |
| 同步内容 | 收藏 | Ribbon 图标触发的同步类型 |
| 每批数量 | 5 | 每次 API 请求条目数，建议 5–10 |
| 同步标签 | 开启 | 将小红书话题标签写入 frontmatter |
| 同步专辑 | 关闭 | 收藏夹按专辑分子目录 |
| 抓取评论 | 关闭 | 同步主评论及子评论 |
| 最大评论数 | 100 | 每帖主评论 + 子评论总上限 |
| 定时自动同步 | 关闭 | 后台按间隔自动同步 |
| 同步间隔 | 10 分钟 | 建议 ≥ 10 分钟 |

#### AI 分类

配置任意 OpenAI 兼容 API（OpenAI / Kimi / DeepSeek / OpenRouter 等）后，同步时自动将笔记归入自定义分类目录，并可开启 AI 打标（每篇生成 3–6 个语义标签）。

#### 关键词搜索

| 设置项 | 说明 |
|--------|------|
| 关键词列表 | 多关键词，每个独立目录，支持增量 |
| 排序方式 | 综合 / 最新 / 最多点赞 / 评论数 / 收藏数 |
| 笔记类型 | 不限 / 视频 / 图文 |
| 时间范围 | 不限 / 一天 / 一周 / 半年 |
| 定时自动搜索 | 按间隔自动执行，新增内容自动入库 |

#### 账号订阅

输入博主主页 URL 中 `/user/profile/` 后的 UID，每次拉取最新 30 条帖子，支持随机延迟避免触发限流。

#### 热点管理

按分类维护关键词列表（4–8 个/分类），一键触发：搜索最多点赞前 30 条 → AI 深度分析前 15 条爆款因素 → 生成结构化日报保存至 `Hotspots/[分类]/报告/YYYY-MM-DD.md`。

---

### ❓ 常见问题

**Q：同步时提示「请先登录」**  
Cookie 已过期，点击「重新登录」完成一次登录即可。

**Q：同步一段时间后报错停止**  
触发了小红书频率限制。将「每批数量」调小至 3–5，等待几分钟后重试。

**Q：图片或视频没有下载**  
小红书媒体链接有时效性，建议尽快同步。清除缓存后重新同步可重试失败项。

**Q：如何从头重新同步所有内容**  
设置 → 账号设置 → 点击「清除缓存」，下次同步将重新拉取全部内容。

**Q：定时同步被自动关闭了**  
遇到限流或 Cookie 失效时插件会自动关闭定时同步以保护账号，处理后在设置中重新开启。

---

## English

### ✨ Features

| Feature | Description |
|---------|-------------|
| 📚 **5 content types** | Bookmarks · Likes · Posts · Keyword search · Account subscriptions |
| 🖼️ **Local media** | Images and videos downloaded locally for offline access |
| 🤖 **AI classification** | Auto-categorize notes into custom folders via any OpenAI-compatible API |
| 🏷️ **AI tagging** | Generate 3–6 semantic tags per note, written to frontmatter |
| 🔥 **Hotspot reports** | Fetch top-liked content by category, AI-analyzes viral factors, saves daily report |
| 📰 **Account subscriptions** | Follow XHS creators by UID, sync latest posts automatically |
| 💬 **Comment sync** | Optionally sync top-level and sub-comments with configurable limits |
| ⏱️ **Auto sync** | Background timer-based sync, pauses on rate-limit or auth failure |
| 🔄 **Incremental sync** | Tracks synced IDs to avoid duplicates |
| 📝 **Structured notes** | Frontmatter with id, author, tags, aiTags, category, likes, comments |

### 🚀 Installation

#### Option 1: Download Release (Recommended)

1. Download the latest `xhs2obsidian-x.x.x.zip` from [**Releases**](https://github.com/unintended0x/xhs2obsidian/releases/latest)
2. Extract and copy the folder to your Vault's `.obsidian/plugins/` directory
3. Obsidian → **Settings → Community plugins** → Disable safe mode → Refresh → Enable **XHS Sync**

#### Option 2: Install via BRAT (Auto-update)

1. Install and enable **BRAT** (Beta Reviewer's Auto-update Tool) from Obsidian community plugins
2. Open BRAT → **Add Beta plugin**
3. Enter the repository URL:

   ```
   https://github.com/unintended0x/xhs2obsidian
   ```

4. Once installed, enable **XHS Sync** in Obsidian **Settings → Community plugins**
5. BRAT will automatically detect new GitHub Releases and keep the plugin up to date

> **Note:** This plugin requires Electron WebView and only works on Obsidian **desktop** (macOS / Windows / Linux).

### 📖 Quick Start

1. **Login** — Settings → XHS Sync → **Login** → complete login in the built-in browser → click **Extract Cookie**
2. **Configure** — Choose sync target, add keywords, or subscribe to accounts
3. **Sync** — Click the cloud icon in the ribbon, or use the command palette (`Cmd/Ctrl+P`)

### ⚙️ Configuration

| Setting | Default | Description |
|---------|---------|-------------|
| Root folder | `RedNote` | Storage directory in your vault |
| Sync target | Bookmarks | What to sync via ribbon icon |
| Batch size | 5 | Items per API request (5–10 recommended) |
| Sync tags | On | Write hashtags to frontmatter |
| Sync albums | Off | Organize bookmarks into album sub-folders |
| Fetch comments | Off | Sync comments and replies per note |
| Auto sync | Off | Background sync at a fixed interval |
| Sync interval | 10 min | Minimum 10 minutes recommended |
| AI classify | Off | Requires OpenAI-compatible API credentials |

### ❓ FAQ

**Q: "Please login first" error**  
Your cookie has expired. Click "Re-login" in settings to refresh.

**Q: Sync stops with a rate-limit error**  
Reduce batch size to 3–5 and wait a few minutes before retrying.

**Q: Images or videos are missing**  
XHS media URLs expire quickly. Sync soon after saving content. Clear cache to retry failed downloads.

---

## 🤝 Contributing

Issues and PRs are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting.

## ⚠️ Disclaimer

This plugin is not affiliated with or endorsed by Xiaohongshu (小红书). It accesses only your own personal data via the web interface. Use responsibly and in compliance with Xiaohongshu's Terms of Service.

## 📄 License

[MIT](LICENSE) © unintended0x
