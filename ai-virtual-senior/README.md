# AI 虚拟学长 · ai-virtual-senior

> 为 21 个专业各配置独立的 system prompt，用 DeepSeek API 提供 SSE 流式对话，解决"新生入学后问题没人问、学长学姐难找"的问题。

🔗 在线 Demo：https://12c0bda130b64a6aa6cd44bd7fcd38bf.bj8.agentos-app.net/ai-senior-chatbot.html

## 这个产品解决什么问题

高中生选专业时严重信息不对称——专业名称耳熟能详，但真实的学习内容、课程难度、就业方向全凭想象。这个产品构建"可感可视化大学专业体验馆"：**"想象 vs 现实"对比卡**让差距可感，**六维雷达图**让专业特征可视化，**AI 虚拟学长**让真实体验可对话。覆盖 21 个专业，每个有独立 AI 身份与知识库。

## 核心功能
- 21 个专业独立 system prompt：不同专业有各自的知识边界与回答风格
- SSE 流式对话：逐字流式输出，打字机效果提升感知速度，Markdown 渲染
- 每专业 5 个快捷问题引导冷启动，30 轮对话限制控制成本

## 为什么这样做（产品决策）

"专业独立 prompt"是关键产品决策：通用大模型回答容易泛泛而谈，只有按专业拆分 prompt 才能给出有专业感的答案。技术实现上放弃 Coze 平台（积分消耗过快），改为 DeepSeek API + 纯 HTML 单页应用，零后端依赖，打开即用。API Key base64 嵌入避免明文暴露，配合 30 轮对话限制控制成本。

## 技术架构
- 模型：DeepSeek API
- 对话协议：SSE 流式输出
- 前端：纯 HTML 单页应用，marked.js 渲染 Markdown
- 后端：Node.js 服务，管理 21 个专业 prompt 配置

## 如何运行

```bash
# 1. 安装依赖
npm install

# 2. 配置环境变量（复制 .env.example 为 .env 并填写）
cp .env.example .env

# 3. 启动开发服务
npm run dev
```

## 环境变量

```env
# 服务端口
PORT=3000

# DeepSeek API Key（请使用你自己的 Key，切勿提交真实值）
DEEPSEEK_API_KEY=sk-xxxxxxxxxxxxxxxx

# DeepSeek API 地址
DEEPSEEK_API_BASE=https://api.deepseek.com
```

## 待改进
- [ ] 补充 21 个专业 prompt 的脱敏示例
- [ ] 补充对话成本统计面板
- [ ] 补充完整业务代码

## License
MIT
