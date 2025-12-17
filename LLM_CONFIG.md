# LLM API 配置指南

本项目支持所有兼容 OpenAI API 格式的 LLM 服务提供商。您可以通过环境变量配置不同的 API 供应商。

## 📋 配置方式

在项目根目录创建 `.env` 文件（或从 `.env.example` 复制），并设置以下环境变量：

```env
OPENAI_API_KEY=your_api_key_here
OPENAI_BASE_URL=your_api_base_url
LLM_MODEL=your_model_name
```

## 🔧 支持的 API 供应商

### 1. Moonshot AI (默认推荐)

**特点：** 国内访问速度快，支持中文，性价比高

**配置示例：**
```env
OPENAI_API_KEY=sk-your-moonshot-api-key
OPENAI_BASE_URL=https://api.moonshot.cn/v1
LLM_MODEL=moonshot-v1-8k
```

**可用模型：**
- `moonshot-v1-8k` - 8K 上下文（默认）
- `moonshot-v1-32k` - 32K 上下文
- `moonshot-v1-128k` - 128K 上下文
- `kimi-k2-0711-preview` - 预览版模型

**获取 API Key：**
- 访问：https://platform.moonshot.cn/
- 注册账号并获取 API Key

---

### 2. OpenAI

**特点：** 官方 API，模型质量高，但需要海外网络

**配置示例：**
```env
OPENAI_API_KEY=sk-your-openai-api-key
OPENAI_BASE_URL=https://api.openai.com/v1
LLM_MODEL=gpt-3.5-turbo
```

**可用模型：**
- `gpt-3.5-turbo` - 性价比高
- `gpt-4` - 高质量但价格较高
- `gpt-4-turbo-preview` - 最新预览版

**获取 API Key：**
- 访问：https://platform.openai.com/
- 注册账号并获取 API Key

---

### 3. 阿里云通义千问

**特点：** 阿里云服务，国内访问稳定

**配置示例：**
```env
OPENAI_API_KEY=your-dashscope-api-key
OPENAI_BASE_URL=https://dashscope.aliyuncs.com/compatible-mode/v1
LLM_MODEL=qwen-turbo
```

**可用模型：**
- `qwen-turbo` - 快速响应
- `qwen-plus` - 平衡性能
- `qwen-max` - 最强性能

**获取 API Key：**
- 访问：https://dashscope.console.aliyun.com/
- 开通服务并获取 API Key

---

### 4. 百度文心一言

**特点：** 百度 AI 服务，中文理解能力强

**配置示例：**
```env
OPENAI_API_KEY=your-baidu-api-key
OPENAI_BASE_URL=https://aip.baidubce.com/rpc/2.0/ai_custom/v1/wenxinworkshop/chat
LLM_MODEL=ernie-bot-turbo
```

**注意：** 百度 API 格式可能不完全兼容，需要额外适配

**获取 API Key：**
- 访问：https://cloud.baidu.com/product/wenxinworkshop
- 开通服务并获取 API Key

---

### 5. 智谱 AI (GLM)

**特点：** 清华大学团队，中文优化

**配置示例：**
```env
OPENAI_API_KEY=your-zhipu-api-key
OPENAI_BASE_URL=https://open.bigmodel.cn/api/paas/v4
LLM_MODEL=glm-4
```

**可用模型：**
- `glm-4` - 最新版本
- `glm-3-turbo` - 快速版本

**获取 API Key：**
- 访问：https://open.bigmodel.cn/
- 注册账号并获取 API Key

---

### 6. 其他兼容 OpenAI 格式的服务

本项目支持任何兼容 OpenAI API 格式的服务，包括：

- **DeepSeek** - https://api.deepseek.com/v1
- **零一万物** - https://api.01.ai/v1
- **MiniMax** - https://api.minimax.chat/v1
- **自建服务** - 使用 vLLM、Ollama 等搭建的本地服务

**配置方式：**
```env
OPENAI_API_KEY=your-api-key
OPENAI_BASE_URL=your-api-base-url
LLM_MODEL=your-model-name
```

---

## 🚀 快速开始

1. **选择 API 供应商**：根据您的需求选择合适的服务商

2. **获取 API Key**：访问对应服务商的官网注册并获取 API Key

3. **配置环境变量**：
   ```bash
   # 复制示例文件
   cp .env.example .env
   
   # 编辑 .env 文件，填入您的配置
   ```

4. **启动项目**：
   ```bash
   # Windows
   start.bat
   
   # Linux/macOS
   ./start.sh
   ```

## ⚠️ 注意事项

1. **API Key 安全**：
   - 不要将 `.env` 文件提交到 Git 仓库
   - 不要分享您的 API Key
   - 定期更换 API Key

2. **费用控制**：
   - 不同服务商的计费方式不同
   - 建议设置使用限额
   - 监控 API 调用量

3. **网络要求**：
   - 部分服务需要海外网络（如 OpenAI）
   - 国内服务商通常访问更快
   - 自建服务需要本地部署

4. **模型选择**：
   - 根据任务复杂度选择合适模型
   - 简单任务使用轻量模型节省成本
   - 复杂任务使用高性能模型提升质量

## 🔍 故障排除

### 问题1：API Key 无效
```
错误：Invalid API Key
解决：检查 .env 文件中的 OPENAI_API_KEY 是否正确
```

### 问题2：网络连接失败
```
错误：Connection timeout
解决：
- 检查网络连接
- 确认 API 地址是否正确
- 检查是否需要代理（海外服务）
```

### 问题3：模型不存在
```
错误：Model not found
解决：检查 LLM_MODEL 环境变量中的模型名称是否正确
```

### 问题4：API 格式不兼容
```
错误：API format error
解决：确认服务商是否完全兼容 OpenAI API 格式
```

## 📚 更多资源

- [OpenAI API 文档](https://platform.openai.com/docs)
- [Moonshot AI 文档](https://platform.moonshot.cn/docs)
- [通义千问文档](https://help.aliyun.com/zh/model-studio/)
- [智谱 AI 文档](https://open.bigmodel.cn/dev/api)

---

**💡 提示：** 如果您使用的是其他兼容 OpenAI 格式的服务，只需提供正确的 `OPENAI_BASE_URL` 和 `LLM_MODEL` 即可使用。

