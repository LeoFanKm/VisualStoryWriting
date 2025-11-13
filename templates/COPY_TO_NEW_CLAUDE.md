# 📋 复制粘贴清单 - 给新 Claude Code 的完整指令

> 🎯 直接复制下面的内容，粘贴到新的 Claude Code 终端
>
> ⚠️ 记得替换 `[你的XXX]` 部分！

---

## 🚀 第一次对话：初始化项目

```
你好！我需要你帮我创建一个名为 VisualWriter 的 AI 驱动可视化写作工具。

【项目背景】
这是基于开源项目 Visual Story-Writing（GitHub: damienmasson/VisualStoryWriting）的商业化改造。
原项目是研究原型，存在安全问题（API密钥浏览器暴露）和架构问题（无后端、无数据库）。

【技术栈（严格遵守）】
前端：
- React 18.2 + TypeScript 5.x
- Tailwind CSS 3.x（样式）
- Vite 4.5+（构建工具）
- 托管：Cloudflare Pages

后端：
- Cloudflare Workers（无服务器边缘计算）
- Runtime: V8 JavaScript
- 架构：事件驱动、单线程、无状态

数据存储：
- Cloudflare D1（SQLite，用户和项目数据）
- Cloudflare KV（缓存和配额管理）
- Cloudflare R2（文件存储，未来用）

第三方服务：
- Clerk（用户认证，我已有账号）
- OpenRouter（AI服务中转，调用 Google Gemini 2.5 Flash）
- Stripe（支付，后期集成）

【我的密钥信息】
Clerk Publishable Key: [你的 pk_test_xxxxx]
Clerk Secret Key: [你的 sk_test_xxxxx]
OpenRouter API Key: [你的 sk-or-v1-xxxxx]

【核心功能（MVP最小可行产品）】
1. 用户系统
   - 注册/登录（Clerk）
   - 用户配置页面
   - 每日免费配额：10次AI调用

2. 项目管理
   - 创建新项目
   - 项目列表展示
   - 自动保存（2秒防抖）
   - 历史版本（简单版）

3. 文本编辑
   - 基于 Slate.js 的富文本编辑器
   - 实时字数统计
   - Markdown 支持

4. AI 功能
   - 提取故事元素（角色、地点、事件）
   - 流式响应，实时显示
   - 建议模式（绿色=添加，灰色=删除）

5. 可视化（简化版）
   - 时间轴视图（横向滚动）
   - 角色关系图（React Flow）
   - 点击可视化元素，高亮对应文本

【数据库 Schema】
users 表：
- id (主键)
- clerk_user_id (唯一)
- email
- subscription_tier (free/pro/enterprise)
- daily_quota_used (整数)
- quota_reset_at (日期)
- created_at
- updated_at

projects 表：
- id (主键)
- user_id (外键 → users.id)
- title (项目名称)
- text_content (文本内容，JSON)
- entities (角色列表，JSON)
- locations (地点列表，JSON)
- actions (事件列表，JSON)
- created_at
- updated_at

project_history 表（简化版）：
- id
- project_id (外键 → projects.id)
- snapshot (完整状态，JSON)
- created_at

【请按以下步骤执行】

Step 1: 项目初始化
- 创建文件夹结构：visualwriter/frontend, visualwriter/backend
- 初始化 package.json
- 列出需要安装的依赖

Step 2: 后端实现
- 创建 wrangler.toml 配置
- 实现 /api/health（健康检查）
- 实现 /api/ai/chat（AI聊天，调用 Gemini）
- 实现 /api/projects（CRUD操作）
- 实现 Clerk 中间件验证
- 实现配额检查

Step 3: 数据库设置
- 创建 D1 数据库
- 生成 SQL 迁移脚本
- 执行迁移命令

Step 4: 前端实现
- 创建 React 项目结构
- 集成 Clerk 认证
- 创建登录/注册页面
- 创建项目列表页
- 创建编辑器页面（Slate）
- 创建简单的时间轴组件
- 实现 API 调用逻辑

Step 5: 本地测试
- 提供启动命令
- 提供测试检查清单

Step 6: 部署指南
- 后端部署命令
- 前端部署命令
- 环境变量配置

【代码规范】
- 所有文件使用 TypeScript（严格模式）
- 函数使用 JSDoc 注释
- 错误处理：try-catch + 用户友好消息
- API 响应格式：{ success: boolean, data?: any, error?: string }
- 命名规范：
  - 文件名：kebab-case (user-profile.tsx)
  - 组件名：PascalCase (UserProfile)
  - 函数名：camelCase (getUserProfile)
  - 常量：UPPER_SNAKE_CASE (API_BASE_URL)

【关键要求】
1. 安全第一：所有敏感信息（密钥）必须在服务端
2. 性能优化：使用 React.memo、useMemo、useCallback
3. 错误处理：每个 API 调用都要有 try-catch
4. 用户体验：加载状态、错误提示、成功反馈
5. 代码复用：创建通用组件和工具函数

【输出格式】
每个步骤请给出：
1. 文件路径
2. 完整代码（可直接复制）
3. 执行命令
4. 验证方法

现在开始 Step 1！
```

---

## 📝 后续对话

### 当 Claude 完成一个步骤后

```
Step X 完成，验证结果：
[粘贴你的验证输出]

继续 Step X+1！
```

### 遇到错误时

```
执行 [命令] 时遇到错误：
[粘贴完整错误信息]

我的环境：
- Node.js 版本：[运行 node -v]
- npm 版本：[运行 npm -v]
- 操作系统：[Windows/Mac/Linux]

请帮我解决！
```

### 需要修改功能时

```
我想修改 [功能名称]：
原来：[描述当前行为]
改为：[描述期望行为]

涉及的文件：[如果知道的话]

请给出修改方案！
```

---

## ✅ 验证检查清单

每完成一个步骤，勾选对应项：

### Step 1: 项目初始化
- [ ] `visualwriter` 文件夹已创建
- [ ] `frontend` 和 `backend` 子文件夹存在
- [ ] `package.json` 文件已创建

### Step 2: 后端实现
- [ ] `wrangler.toml` 配置正确
- [ ] API 文件都已创建
- [ ] `wrangler dev` 能启动
- [ ] 访问 http://localhost:8787/api/health 返回成功

### Step 3: 数据库设置
- [ ] D1 数据库已创建
- [ ] 迁移脚本执行成功
- [ ] `wrangler d1 execute` 能查询表结构

### Step 4: 前端实现
- [ ] React 项目能启动
- [ ] 访问 http://localhost:5173 显示登录页
- [ ] Clerk 登录功能正常
- [ ] 能创建新项目

### Step 5: 本地测试
- [ ] 能注册新用户
- [ ] 能创建和保存项目
- [ ] AI 功能正常
- [ ] 可视化显示正常

### Step 6: 部署
- [ ] 后端部署成功（有 .workers.dev 网址）
- [ ] 前端部署成功（有 .pages.dev 网址）
- [ ] 生产环境能正常访问

---

## 🎯 完成标志

当你能做到以下所有事情，说明成功了：

1. ✅ 在浏览器打开部署后的网址
2. ✅ 注册一个新账号
3. ✅ 创建一个新项目
4. ✅ 输入一段文字："小明在公园里遇到了小红，他们一起玩耍"
5. ✅ 点击 AI 分析按钮
6. ✅ 看到提取的角色（小明、小红）和地点（公园）
7. ✅ 时间轴显示事件
8. ✅ 刷新页面，数据还在

**如果以上全部成功 = 你的 MVP 完成了！🎉**

---

## 💡 提示

1. **不要着急** - 每个步骤都要验证成功再继续
2. **保存进度** - 把 Claude 给的所有代码保存到文件
3. **遇到问题正常** - 复制错误信息，让 Claude 帮你解决
4. **随时可以重来** - 如果搞砸了，删除文件夹重新开始

---

## 📞 需要帮助？

在 Claude Code 中随时问：

```
我卡在 XXX 步骤了，[描述问题]，请帮我！
```

Claude 会耐心指导你！

---

**更新日期**: 2025-11-13
**预计时间**: 2-4小时（第一次）
**难度**: ⭐ 复制粘贴即可
