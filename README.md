# OpenSkills-Weixin

AI 编码助手技能集，通过 6551 平台 API 提供加密货币新闻、社交媒体和交易操作功能。

## 可用技能

### 新闻与社交媒体

| 技能 | 描述 |
|-------|-------------|
| `opennews` | 加密货币新闻搜索、AI 评级、交易信号和实时更新 |
| `opentwitter` | Twitter/X 数据，包括用户资料、推文搜索和 KOL 追踪 |

**总计**: 2 个技能

## 前置要求

所有技能都需要来自 6551 平台的 API 令牌。

### API 令牌设置

在项目根目录创建或编辑 `.env` 文件以覆盖默认 API 凭据。在执行操作前加载它。

```bash
OPEN_TOKEN=your_token_here
```

获取你的 API 令牌: https://6551.io/mcp

**安全警告**: 永远不要将 `.env` 提交到 git（将其添加到 `.gitignore`），也不要在日志、截图或聊天消息中暴露凭据。

### 配置文件（备选方案）

你也可以将令牌存储在配置文件中:

**macOS/Linux:**
```bash
mkdir -p ~/.config/openskills
echo '{"token": "your-token-here"}' > ~/.config/openskills/credentials.json
```

**Windows:**
```powershell
mkdir $env:APPDATA\openskills
echo '{"token": "your-token-here"}' > $env:APPDATA\openskills\credentials.json
```

**优先级:** `.env` 文件优先于配置文件。

所有请求都需要 Bearer 令牌认证:

```bash
Authorization: Bearer $OPEN_TOKEN
```

## 安装

### 推荐方式

```bash
npx skills add 6551Team/openskills-weixin
```

适用于 Claude Code、Cursor、Codex CLI 和 OpenCode。自动检测你的环境并相应安装。

## 技能工作流

这些技能在典型的加密货币工作流中协同工作:

### 新闻驱动交易
`opennews` → 分析市场数据 → 执行交易决策

1. 从新闻中发现交易信号
2. 检查当前代币价格
3. 基于信息做出交易决策

### 社交情绪分析
`opentwitter` → `opennews` → 市场验证 → 交易决策

1. 搜索 Twitter 提及和 KOL 活动
2. 与新闻信号交叉参考
3. 验证价格走势
4. 执行明智的交易

## API 基础 URL

所有技能使用基础 URL: `https://ai.6551.io`

## 响应格式

所有 API 响应遵循此格式:

```json
{
  "code": 200,
  "message": "success",
  "data": {
    // 响应数据
  },
  "usage": 1
}
```

## 错误处理

```json
{
  "code": 400,
  "message": "error message",
  "error": "detailed error information"
}
```

## 速率限制

- 速率限制适用于所有端点
- 每个请求消耗配额单位（通常每个请求 1 单位）
- 在 https://6551.io/mcp 监控你的使用情况

## 许可证

MIT

## 支持

如有问题和功能请求，请访问: https://6551.io/support
