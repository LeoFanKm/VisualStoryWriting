# VisualWriter 快速启动模板

## 🚀 在新的 Claude Code 中直接复制这段话

```
你好 Claude！我想创建一个名为 VisualWriter 的项目。

【项目描述】
VisualWriter 是一个 AI 驱动的可视化故事创作工具，用户可以通过操作时间轴、角色关系图、空间位置图来辅助写作。它基于 Visual Story-Writing 项目改造而来。

【技术栈要求】
- 前端：React 18.2 + TypeScript 5.x + Tailwind CSS 3.x + Vite
- 后端：Cloudflare Workers（边缘计算）
- 数据库：Cloudflare D1（SQLite）+ KV（缓存）+ R2（文件存储）
- 认证：Clerk
- 支付：Stripe（后期集成）
- AI服务：Google Gemini 2.5 Flash（通过 OpenRouter）
- 托管：Cloudflare Pages

【我已准备的密钥】
请提示我输入以下密钥：
1. Clerk Publishable Key: pk_test_xxxxx
2. Clerk Secret Key: sk_test_xxxxx
3. OpenRouter API Key: sk-or-v1-xxxxx

【请帮我做的事】
1. 创建完整的项目脚手架
2. 配置所有环境变量
3. 创建数据库 Schema（用户表、项目表、历史记录表）
4. 实现用户认证（Clerk 集成）
5. 实现 AI 聊天接口（调用 Gemini）
6. 创建基础的前端界面（登录页、项目列表、编辑器）
7. 提供本地测试命令
8. 提供部署命令

【核心功能】
从简单开始，先实现：
1. 用户登录/注册
2. 创建新项目
3. 文本编辑器（基础版）
4. 调用 AI 提取故事元素（角色、地点、事件）
5. 简单的可视化展示（时间轴）
6. 自动保存

【开发流程】
请按照以下步骤指导我：
Step 1: 初始化项目结构
Step 2: 安装依赖
Step 3: 配置环境变量
Step 4: 创建数据库
Step 5: 实现后端 API
Step 6: 实现前端界面
Step 7: 本地测试
Step 8: 部署

每个步骤请给出具体的命令和代码，我会复制粘贴执行。

开始吧！
```

---

## 📋 Claude 会询问你的信息

当 Claude 问你密钥时，从你的 `keys.txt` 文件中复制粘贴：

### Clerk Publishable Key
```
pk_test_xxxxx（替换为你的）
```

### Clerk Secret Key
```
sk_test_xxxxx（替换为你的）
```

### OpenRouter API Key
```
sk-or-v1-xxxxx（替换为你的）
```

---

## ✅ 验证步骤

每完成一个步骤，Claude 会让你验证：

### Step 1 验证
```bash
ls -la
# 应该看到项目文件夹
```

### Step 2 验证
```bash
npm -v
# 应该显示版本号
```

### Step 3 验证
```bash
cat .env.local
# 应该看到配置的密钥
```

### Step 4 验证
```bash
wrangler d1 list
# 应该看到数据库列表
```

### Step 5-6 验证
```bash
# 终端1
cd backend && wrangler dev

# 终端2
cd frontend && npm run dev

# 浏览器访问 http://localhost:5173
# 应该看到登录页面
```

### Step 7-8 验证
```bash
# 部署后访问生成的网址
# 应该能正常使用
```

---

## 🔄 如果中途断开连接

保存 Claude 给你的所有命令到一个文件 `commands.txt`，然后在新对话中说：

```
我之前在创建 VisualWriter 项目，已经完成到第 X 步。
我的项目结构是：
[粘贴 ls -la 的结果]

现在我想继续第 X+1 步，请接着指导我。
```

---

## 💡 提示

- ✅ 每个命令执行完，等待成功提示再继续
- ✅ 遇到错误，复制完整错误信息给 Claude
- ✅ 不要跳过验证步骤
- ✅ 保存 Claude 给你的所有命令

---

**预计完成时间**: 2-3小时
**难度**: ⭐ 零基础可完成
