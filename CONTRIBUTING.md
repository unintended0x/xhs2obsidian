# Contributing to XHS Sync

感谢你对本项目的兴趣！ / Thanks for your interest in contributing!

## 开发环境 / Development Setup

```bash
git clone https://github.com/unintended0x/xhs2obsidian.git
cd xhs2obsidian
npm install
npm run dev
```

`npm run dev` 会启动监听模式，修改源码后自动重新编译到 `main.js`。

将 `main.js`、`manifest.json`、`styles.css` 复制到你的 Obsidian Vault：

```
<Your Vault>/.obsidian/plugins/xhs2obsidian/
```

## 项目结构 / Project Structure

```
src/
├── main.ts          # 插件入口 / Plugin entry point
├── types.ts         # TypeScript 类型定义 / Type definitions
├── xhs-api.ts       # 小红书 API 客户端 / XHS API client
├── sync-engine.ts   # 同步核心逻辑 / Core sync logic
├── vault-writer.ts  # Obsidian Vault 写入 / Vault file writer
├── sign-manager.ts  # 请求签名管理 / Request signing
├── signing.ts       # 签名算法实现 / Signing algorithm
├── login-modal.ts   # 登录弹窗 / Login modal
├── ai-classifier.ts # AI 分类 / AI classification
└── logger.ts        # 日志 / Logger
```

## 提交 PR / Submitting a PR

1. Fork 本仓库
2. 创建功能分支：`git checkout -b feature/your-feature`
3. 提交变更：`git commit -m 'feat: add some feature'`
4. 推送分支：`git push origin feature/your-feature`
5. 发起 Pull Request

## 反馈问题 / Reporting Issues

- 🐛 **Bug 报告** → [Bug Report](.github/ISSUE_TEMPLATE/bug_report.md)
- 💡 **功能建议** → [Feature Request](.github/ISSUE_TEMPLATE/feature_request.md)
- 🔑 **签名算法失效** → 请附上 Obsidian 开发者控制台的错误截图
