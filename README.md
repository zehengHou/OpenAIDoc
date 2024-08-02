# OpenAI 相关笔记

## ScoutResearchKey:
- `sk-proj-HepBcJQQp5WG3vdQh7tjT3BlbkFJvT76mYDhbZzpunoTzCuk`
- 账户: `zhhou@telenavsoftware.com`

### ScoutMaps
- `sk-proj-VqbHsWas3tElsrlugaDAT3BlbkFJJUyNUzRa3tLCP3yUIEHN`

### 免费版配额有限
- `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`
- 提示: "You exceeded your current quota, please check your plan and billing details" 
- 充值之后也存在限制:
  - [限额设置](https://platform.openai.com/settings/organization/limits)
  - [速率限制指南](https://platform.openai.com/docs/guides/rate-limits)
  
## 1. 价格计算

- 参考链接: [OpenAI的API是如何计算费用的？](https://juejin.cn/post/7220974237141041208)
- 官方文档: [OpenAI Pricing](https://openai.com/api/pricing/)
  
### Tokens计算方式
- OpenAI API 通过请求和响应中的最终 Tokens 数量来计费。
- 不同模型收费标准不同。
- 例如：GPT-3.5-turbo 每 1000 Tokens 收费 $0.
  - 根据当前汇率，大约每1000个tokens收费1毛4分。
  - 1 Token ~= 4 个字符（英文）
  - 1,000 Tokens ~= 750 字

#### 价格示例（每1M Tokens）

| Model | Input Price | Batch API Input Price | Output Price | Batch API Output Price |
| --- | --- | --- | --- | --- |
| gpt-4 | $5.00 | $2.50 | $15.00 | $7.50 |
| gpt-3.5-turbo-0125 | $0.50 | $0.25 | $1.50 | $0.75 |
| gpt-3.5-turbo-instruct | $1.50 | $0.75 | $2.00 | $1.00 |

## 2. Azure OpenAI

- [Azure OpenAI: 如何创建资源](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/create-resource?pivots=web-portal)

## 3. API 使用速率限制

- [API使用限制设置](https://platform.openai.com/settings/organization/limits)
- [速率限制指南](https://platform.openai.com/docs/guides/rate-limits?context=tier-five)
  
### 速率限制原理：
- 每分钟请求数（RPM）
- 每分钟令牌数（TPM）
- 每日请求数（RPD）
- 速率限制是为了保护API免受滥用或误用，确保公平访问，管理基础设施的负载。

### 不同模型的速率限制

| Model | Tokens 限制 | 请求和其他限制 | 批量队列限制 |
| --- | --- | --- | --- |
| gpt-3.5-turbo | 40,000 TPM | 3 RPM | 200 RPD |
| gpt-3.5-turbo-instruct | 90,000 TPM | 3 RPM | 200 RPD |
  
- 速率限制是在组织级别和项目级别定义的。
- 不同模型系列共享速率限制。

## 4. Tokens 计算

- 参考链接: [Tokens 计算简介](https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them)
- 通过编程方式对文本进行Token化可以使用Tiktoken，一个专门用于OpenAI模型的快速BPE tokenizer。
- GitHub 地址: [Tiktoken](https://github.com/openai/tiktoken)

## 5. 使用政策

- [数据使用政策](https://openai.com/policies/usage-policies/)

### 数据使用和保留政策
- 自2023年3月1日起，OpenAI对数据使用和保留政策进行了调整。
- 默认情况下，OpenAI不会使用通过API提交的数据来训练模型。
- API数据最多保留30天，主要用于滥用和误用监控。

## Tools

### API 相关链接
- API key: [API-key 管理页面](https://platform.openai.com/api-keys)
- API key usage: [API-key 使用情况](https://platform.openai.com/usage)
  
### 知识查询
- [OpenAI帮助中心](https://help.openai.com/en/)

### 工具和资源
- GPT 比较工具: [GPT Comparison Tool](https://gpttools.com/comparisontool)
- 中文文档: [OpenAI 中文文档](https://openai.xiniushu.com/docs/quickstart)

### 调试工具
- [APIfox 调试工具](https://openai.apifox.cn/endpoint-123512277)

### OpenAI 工具合集
- [工具合集](https://xiniushu.com/#doc_tool)
  
### Tokens 计算工具
- [Tokenizer](https://platform.openai.com/tokenizer)

### 编程方式对文本进行token化
- 可以使用Tiktoken，一个专门用于OpenAI模型的快速BPE tokenizer。
- [GitHub 链接](https://github.com/openai/tiktoken)

### Prompt examples 示例
- [Examples](https://platform.openai.com/docs/examples)
  
## API 调试和错误码对比
- [错误码对比](https://platform.openai.com/docs/guides/error-codes/api-errors)
  
### Community libraries
- [OpenAI Libraries](https://platform.openai.com/docs/libraries/python-library)

### Dev board
- [Chat Playground](https://platform.openai.com/playground/chat?models=gpt-3.5-turbo-1106)

## AI 学习资源

- [d2l.ai](https://d2l.ai/): 了解人工智能工作原理的好资源。
- [Awesome ChatGPT Prompts](https://github.com/f/awesome-chatgpt-prompts)
- [FlowGPT](https://www.flowgpt.com/)
- [r/PromptDesign](https://www.reddit.com/r/PromptDesign/)
- [OpenAI Discord](https://discord.com/invite/openai)

## OpenAI 模型能力

1. **语音转文本**
   - Audio API 基于 Whisper v2 模型，提供了两个语音转文本端点：转录和翻译。
   - 支持的输入文件类型包括：mp3、mp4、mpeg、mpga、m4a、wav和webm。

2. **文本生成模型**
   - OpenAI的文本生成模型可以用于起草文档、编写计算机代码、回答问题、分析文本、翻译语言等多种应用。

### Fun
- [Fun 视频](https://www.youtube.com/watch?v=WpQ0TqS3_68&t=1208s)

### API Reference
- [API Reference](https://platform.openai.com/docs/api-reference/chat/create)

### Tools:

1. **调试工具**
   - [Clarified: 新注册的账户也不送了](https://community.openai.com/t/message-no-credit-grants-found-in-the-new-api-openai-accounts/712611)

2. **分批请求**

3. **BPE (Byte Pair Encoding)**
   - 一种常用于自然语言处理的分词算法。适用于与预训练的语言模型（如OpenAI的模型）无缝集成。

4. **Ktor HTTP Client**
   - Ktor HTTP 客户端是一个强大的工具，用于在 Kotlin 应用程序中进行 HTTP 请求。
   - 官网: [Ktor](https://ktor.io/)

5. **Prompt examples**
   - [Examples](https://platform.openai.com/docs/examples)
