# VisualWriter 傻瓜式开发指南

> 🎯 **目标**: 将 Visual Story-Writing 改造为全新的 VisualWriter 产品
>
> 📱 **不需要任何技术背景** - 只需复制粘贴命令即可！

---

## 📋 开始前的准备（必读）

### 你需要准备的东西

1. ✅ 一个新的 Claude Code 终端（打开网页版或桌面版）
2. ✅ 一个 GitHub 账号
3. ✅ 一张信用卡（用于注册服务，大部分有免费额度）
4. ✅ 30分钟的时间
5. ✅ 能上网的电脑

### 预计花费

| 服务 | 月费用 | 免费额度 | 说明 |
|------|--------|---------|------|
| Cloudflare | $0-5 | 每月100,000请求免费 | 托管平台 |
| Clerk | $0-25 | 10,000月活用户免费 | 用户登录 |
| OpenRouter | 按需 | 无 | AI服务 |
| Stripe | 2.9%交易费 | 无月费 | 支付功能 |
| **总计** | **$0-30** | **开发期可能为$0** | |

---

## 🚀 第一步：注册所有需要的服务

### 1.1 注册 GitHub（如果还没有）

**操作步骤**：
1. 打开浏览器，访问: https://github.com/signup
2. 输入邮箱、密码、用户名
3. 点击「Create account」
4. 验证邮箱

**验证成功**：能看到 GitHub 首页

---

### 1.2 注册 Cloudflare（托管平台）

**操作步骤**：
1. 访问: https://dash.cloudflare.com/sign-up
2. 输入邮箱和密码
3. 点击「Sign Up」
4. 验证邮箱

**验证成功**：能看到 Cloudflare 仪表板

---

### 1.3 注册 Clerk（用户登录系统）

**操作步骤**：
1. 访问: https://dashboard.clerk.com/sign-up
2. 选择「Continue with Google」或输入邮箱
3. 创建新应用
4. 应用名称输入: `VisualWriter`
5. 选择认证方式: 勾选 `Email` 和 `Google`
6. 点击「Create application」

**重要信息**（复制保存）：
```
Publishable Key: pk_test_xxxxxx（在仪表板首页能看到）
Secret Key: sk_test_xxxxxx（点击 API Keys 查看）
```

**验证成功**：能看到应用仪表板

---

### 1.4 注册 OpenRouter（AI服务）

**操作步骤**：
1. 访问: https://openrouter.ai/
2. 点击右上角「Sign In」
3. 选择「Continue with Google」
4. 点击「Keys」→「Create Key」
5. 输入名称: `VisualWriter`
6. 点击「Create」

**重要信息**（复制保存）：
```
API Key: sk-or-v1-xxxxxx
```

**充值**（可选，开发测试用$5即可）：
1. 点击「Credits」
2. 点击「Add Credits」
3. 输入金额: $5
4. 完成支付

**验证成功**：能看到 API Key

---

### 1.5 注册 Stripe（支付系统，暂时可跳过）

**操作步骤**：
1. 访问: https://dashboard.stripe.com/register
2. 输入邮箱、创建账户
3. 验证邮箱

**注意**：Stripe 需要企业信息，开发阶段可以使用测试模式，正式上线前再完善。

---

## 📝 第二步：保存所有密钥

**创建一个文本文件**（例如 `keys.txt`），保存以下信息：

```txt
=== VisualWriter 密钥信息 ===
创建日期: 2025-11-13

【Clerk】
Publishable Key: pk_test_xxxxx（替换为你的）
Secret Key: sk_test_xxxxx（替换为你的）

【OpenRouter】
API Key: sk-or-v1-xxxxx（替换为你的）

【GitHub】
用户名: your-username（替换为你的）
邮箱: your-email@example.com（替换为你的）

⚠️ 重要：此文件包含敏感信息，请勿分享或上传！
```

**保存位置**：桌面或文档文件夹，方便查找

---

## 🖥️ 第三步：在 Claude Code 中创建新项目

### 3.1 打开新的 Claude Code 终端

**操作方法**：
- 网页版: 打开新标签页，访问 Claude Code 网址
- 桌面版: 启动应用

**验证**：看到 Claude 的对话界面

---

### 3.2 复制粘贴以下内容给 Claude

```
你好！我想创建一个名为 VisualWriter 的新项目。

项目要求：
1. 基于现有的 Visual Story-Writing 项目改造
2. 使用 Cloudflare 全栈技术（Workers + Pages + D1）
3. 集成 Clerk 用户认证
4. 使用 Google Gemini 2.5 Flash 作为 AI 服务
5. 未来要集成 Stripe 支付

请帮我创建项目脚手架，包括：
- 前端 React 项目结构
- Cloudflare Workers 后端
- 数据库 Schema
- 环境变量配置

我已经准备好了以下密钥：
- Clerk Publishable Key: [从 keys.txt 复制粘贴]
- Clerk Secret Key: [从 keys.txt 复制粘贴]
- OpenRouter API Key: [从 keys.txt 复制粘贴]

请一步一步指导我操作。
```

**等待 Claude 回复**，然后按照他的指示操作。

---

## 📂 第四步：Claude 会帮你做什么

Claude 会帮你完成以下工作（你只需复制粘贴命令）：

### 4.1 创建项目文件夹
```bash
# Claude 会让你执行类似这样的命令
mkdir VisualWriter
cd VisualWriter
```

### 4.2 初始化前端项目
```bash
# 创建 React + Vite 项目
npm create vite@latest frontend -- --template react-ts
cd frontend
npm install
```

### 4.3 初始化后端项目
```bash
# 创建 Workers 项目
cd ..
mkdir backend
cd backend
npm init -y
npm install hono @cloudflare/workers-types
```

### 4.4 安装必要的依赖

**前端**：
```bash
cd frontend
npm install @clerk/clerk-react zustand @xyflow/react tailwindcss
```

**后端**：
```bash
cd backend
npm install @clerk/backend hono
```

---

## 🔧 第五步：配置环境变量

Claude 会创建配置文件，你只需填入密钥。

### 5.1 前端环境变量

**文件**: `frontend/.env.local`

```bash
# Claude 会创建这个文件，你只需替换密钥
VITE_CLERK_PUBLISHABLE_KEY=pk_test_xxxxx
VITE_API_BASE=http://localhost:8787
```

**操作**：
1. 打开 `frontend/.env.local` 文件
2. 将 `pk_test_xxxxx` 替换为你在 keys.txt 中保存的 Clerk Publishable Key
3. 保存文件（Ctrl+S 或 Cmd+S）

### 5.2 后端密钥配置

**操作**：
```bash
# 进入后端目录
cd backend

# 设置 Clerk Secret Key
wrangler secret put CLERK_SECRET_KEY
# 粘贴你的 sk_test_xxxxx 然后回车

# 设置 OpenRouter API Key
wrangler secret put OPENROUTER_API_KEY
# 粘贴你的 sk-or-v1-xxxxx 然后回车
```

**验证**：
```bash
wrangler secret list
# 应该看到两个密钥：CLERK_SECRET_KEY 和 OPENROUTER_API_KEY
```

---

## ✅ 第六步：测试项目是否能运行

### 6.1 启动后端

**打开第一个终端窗口**：
```bash
cd VisualWriter/backend
wrangler dev
```

**看到这个说明成功**：
```
⎔ Starting local server...
[wrangler] Ready on http://localhost:8787
```

**不要关闭这个窗口！**

---

### 6.2 启动前端

**打开第二个终端窗口**（新标签页）：
```bash
cd VisualWriter/frontend
npm run dev
```

**看到这个说明成功**：
```
  VITE v5.x.x  ready in xxx ms

  ➜  Local:   http://localhost:5173/
  ➜  press h to show help
```

---

### 6.3 在浏览器中打开

1. 打开浏览器
2. 访问: http://localhost:5173
3. 应该看到登录页面

**如果看到登录页面 = 成功！🎉**

---

## 🐛 遇到问题怎么办？

### 问题1: `command not found: npm`

**原因**: 没有安装 Node.js

**解决方法**：
1. 访问: https://nodejs.org
2. 下载并安装 LTS 版本
3. 重启终端
4. 输入 `node -v` 验证安装

---

### 问题2: `command not found: wrangler`

**解决方法**：
```bash
npm install -g wrangler
wrangler login
```

---

### 问题3: 页面显示 "Unauthorized"

**原因**: Clerk 密钥没有配置正确

**检查清单**：
1. 打开 `frontend/.env.local`
2. 确认 Clerk Publishable Key 正确
3. 重启前端服务（Ctrl+C 然后重新 `npm run dev`）

---

### 问题4: AI 功能报错

**原因**: OpenRouter API Key 没有配置或余额不足

**解决方法**：
1. 访问 https://openrouter.ai
2. 检查余额（至少 $1）
3. 重新配置密钥：
```bash
cd backend
wrangler secret put OPENROUTER_API_KEY
```

---

## 🎨 第七步：开始自定义你的产品

现在基础框架已经搭建好了，你可以让 Claude 帮你：

### 7.1 修改品牌名称

```
请帮我将所有 "Visual Story-Writing" 替换为 "VisualWriter"，包括：
- 页面标题
- Logo
- 欢迎消息
```

### 7.2 修改配色方案

```
请帮我修改配色方案，我想要：
- 主色调：#4F46E5（紫色）
- 辅助色：#10B981（绿色）
- 背景色：#F9FAFB（浅灰）
```

### 7.3 添加新功能

```
请帮我添加一个功能：用户可以导出故事为 PDF 文件
```

---

## 📤 第八步：部署到生产环境

当你准备好让别人使用时，让 Claude 帮你部署：

### 8.1 部署后端

```bash
cd backend
wrangler deploy
```

**成功后会看到**：
```
Published visual-writer-api
  https://visual-writer-api.your-subdomain.workers.dev
```

### 8.2 部署前端

```bash
cd frontend
npm run build
wrangler pages deploy dist --project-name visual-writer
```

**成功后会看到**：
```
✨ Success! Uploaded 45 files
🌎 https://visual-writer.pages.dev
```

### 8.3 配置自定义域名（可选）

```
我想使用自己的域名 app.visualwriter.com，请指导我配置
```

---

## 📊 第九步：监控和维护

### 9.1 查看使用情况

**Cloudflare Dashboard**：
1. 访问 https://dash.cloudflare.com
2. 点击「Workers & Pages」
3. 查看请求数、错误率

**Clerk Dashboard**：
1. 访问 https://dashboard.clerk.com
2. 查看用户注册数、活跃度

**OpenRouter Dashboard**：
1. 访问 https://openrouter.ai
2. 查看 AI 调用次数、费用

### 9.2 查看日志

```bash
# 查看后端实时日志
wrangler tail
```

---

## 🎓 第十步：学习和改进

### 推荐的学习资源

1. **Cloudflare Workers 教程**
   - 访问: https://developers.cloudflare.com/workers/get-started
   - 搜索: "Cloudflare Workers 中文教程"

2. **React 基础**
   - 访问: https://react.dev/learn
   - 看视频: B站搜索 "React 零基础"

3. **问 Claude**
   - 随时问："请解释一下这段代码是什么意思"
   - "如果我想添加 XXX 功能，应该怎么做？"

---

## 📋 常用命令速查表

复制这些命令，需要时直接使用：

```bash
# 启动开发环境
cd VisualWriter/backend && wrangler dev  # 终端1
cd VisualWriter/frontend && npm run dev  # 终端2

# 查看后端日志
cd backend && wrangler tail

# 部署到生产环境
cd backend && wrangler deploy
cd frontend && npm run build && wrangler pages deploy dist

# 更新依赖
cd frontend && npm update
cd backend && npm update

# 查看密钥配置
cd backend && wrangler secret list

# 修改密钥
cd backend && wrangler secret put CLERK_SECRET_KEY
cd backend && wrangler secret put OPENROUTER_API_KEY
```

---

## 🆘 紧急救援

**如果完全卡住了**，在 Claude Code 中输入：

```
救命！我遇到了以下错误：
[粘贴错误信息]

我在执行这个命令：
[粘贴你执行的命令]

我的项目结构：
[运行 ls -la 的结果]

请帮我解决！
```

---

## ✅ 成功检查清单

完成以下所有项目，说明你成功了：

- [ ] 所有服务账号注册完成
- [ ] 密钥保存在 keys.txt
- [ ] 项目在本地运行（http://localhost:5173 能打开）
- [ ] 能看到 Clerk 登录页面
- [ ] 能成功注册账号
- [ ] AI 功能正常工作
- [ ] 后端部署成功（有 .workers.dev 网址）
- [ ] 前端部署成功（有 .pages.dev 网址）
- [ ] 可以通过公网访问

---

## 🎉 恭喜你！

如果你完成了所有步骤，你已经成功：

1. ✅ 搭建了一个现代化的全栈应用
2. ✅ 集成了用户认证系统
3. ✅ 连接了 AI 服务
4. ✅ 部署到了全球 CDN

**这是一个完整的 SaaS 产品基础架构！**

---

## 📞 持续支持

记住：**Claude Code 就是你的技术顾问**

随时问：
- "我想添加 XXX 功能"
- "这个错误是什么意思"
- "如何优化性能"
- "如何添加新的 AI 模型"

Claude 会一步一步指导你！

---

**更新日期**: 2025-11-13
**难度等级**: ⭐ 零基础友好
**预计完成时间**: 2-4小时（第一次）
**后续改进**: 无限可能！
