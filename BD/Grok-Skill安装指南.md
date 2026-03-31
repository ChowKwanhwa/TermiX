# Grok Skill 安装与使用指南

## 这是什么？

[xAI Grok Search](https://github.com/openclaw/skills/tree/main/skills/castanley/grok) 是一个 Claude Code 的 Skill，能够通过 xAI 的 Grok API 实时搜索 **X/Twitter** 和 **Web** 上的信息。

Grok 对 Twitter 数据有天然优势（xAI 是 X/Twitter 的关联公司），非常适合用来：

- 追踪 AI Agent、Crypto 赛道的最新项目动态
- 了解某个项目在 Twitter 上的社区讨论和情绪
- 发现新发布的项目、融资消息、Token 上线信息
- 监控竞品和潜在合作方的最新动向

## 安装步骤

### 1. 确保已安装 Claude Code

如果还没有，参考官方文档安装：https://docs.anthropic.com/en/docs/claude-code

### 2. 获取 xAI API Key

1. 访问 https://console.x.ai/
2. 注册/登录账号
3. 在 API Keys 页面创建一个新的 Key
4. 充值 Credits（$5 即可支撑大量搜索）

### 3. 配置环境变量

将 API Key 添加到 shell 配置文件中：

```bash
# 打开配置文件
nano ~/.zshrc

# 添加以下内容（替换为你的实际 Key）
export XAI_API_KEY="你的-xai-api-key"

# 保存后让配置生效
source ~/.zshrc
```

### 4. 安装 Skill

在项目目录下执行：

```bash
npx clawhub@latest install grok
```

安装成功后会看到：

```
✔ OK. Installed grok -> /你的项目路径/skills/grok
```

## 使用方式

安装完成后，在 Claude Code 对话中直接用自然语言提问即可。Claude 会自动调用 Grok Skill 进行搜索。

### 搜索 Twitter

> 用 grok 搜一下 Twitter 上最近讨论最多的 AI Agent 项目有哪些

> 搜一下 @virtuals_io 最近在 Twitter 上发了什么

> 用 grok 搜索 2026 年新出的 AI agent crypto 项目，限定今年 1 月以后的内容

### 搜索 Web

> 用 grok 搜一下最近 AI agent 赛道有哪些融资新闻

> 帮我搜索 MeshLedger 这个项目的官网信息

### 高级用法

Skill 支持以下过滤参数（Claude 会根据你的描述自动使用）：

| 功能 | 说明 |
|------|------|
| 日期过滤 | 限定搜索时间范围，如"只看 2026 年的" |
| 账号过滤 | 只看/排除特定 Twitter 账号，最多 10 个 |
| 域名过滤 | Web 搜索时限定/排除特定网站，最多 5 个 |
| 图片/视频理解 | 分析推文中的图片或视频内容 |

## 注意事项

- 搜索使用的是 reasoning 模型，单次查询可能需要 **30-60 秒**，请耐心等待
- 搜索结果基于 Twitter 讨论，投资机构、Token 状态等关键信息请做**二次验证**
- 避免短时间内大量并发请求，容易触发 Rate Limit
- API 调用会消耗 Credits，日常使用费用很低，但注意留意用量

## 相关链接

- Skill 源码：https://github.com/openclaw/skills/tree/main/skills/castanley/grok
- Skill 市场：https://clawhub.ai
- xAI API 控制台：https://console.x.ai
- xAI API 文档（Web Search）：https://docs.x.ai/developers/tools/web-search
- xAI API 文档（X Search）：https://docs.x.ai/developers/tools/x-search
