# OpenAI 学习笔记

## 1. 账户信息

- **ScoutResearchKey**: `sk-proj-HepBcJQQp5WG3vdQh7tjT3BlbkFJvT76mYDhbZzpunoTzCuk`
- **账户**: `zhhou@telenavsoftware.com`
- **ScoutMaps**: `sk-proj-VqbHsWas3tElsrlugaDAT3BlbkFJJUyNUzRa3tLCP3yUIEHN`
- **API Key**: `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`

### 注意事项

- 免费版配额有限: `You exceeded your current quota, please check your plan and billing details`
- 充值后也存在限制: [查看限制详情](https://platform.openai.com/settings/organization/limits)

## 2. 价格计算

- [如何计算费用？](https://juejin.cn/post/7220974237141041208)
  - OpenAI API 通过请求和响应中最终的Tokens数量来计费（想了解Tokens是什么以及文本内容如何拆分成Token请通过左侧目录导航到附录查看）。
  - 不同的模型收费标准不同，以 `gpt-3.5-turbo` 为例，现在官网显示的费用是 `$0.002/1K tokens`，按照现在的汇率大概是每1000个token收费0.14元人民币。
  - 1K tokens 大约等于750个英文单词。
  - [查看价格详情](https://openai.com/api/pricing/)

### 模型和价格

- **gpt-4**
  - 输入: $5.00/1M tokens
  - 输出: $15.00/1M tokens
- **gpt-3.5-turbo-0125**
  - 输入: $0.50/1M tokens
  - 输出: $1.50/1M tokens
- **gpt-3.5-turbo-instruct**
  - 输入: $1.50/1M tokens
  - 输出: $2.00/1M tokens

## 3. Azure OpenAI 配合 Moderation

- [如何创建资源](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/create-resource?pivots=web-portal)

## 4. API 使用速率限制

- [速率限制详情](https://platform.openai.com/settings/organization/limits)
  - API 使用受到速率限制，包括每分钟的令牌数（TPM），每分钟或每天的请求数（RPM/RPD），以及其他特定模型的限制。

### 各模型速率限制

- **gpt-3.5-turbo**
  - 40,000 TPM
  - 3 RPM
  - 200 RPD
- **gpt-3.5-turbo-instruct**
  - 90,000 TPM
  - 3 RPM
  - 200 RPD

### 速率限制的意义

- 保护API免受滥用或误用。
- 确保公平访问。
- 管理基础设施的总体负载。

### 速率限制工作原理

- 限制通过五种方式衡量：RPM、RPD、TPM、TPD 和 IPM。
- 批量API队列限制是基于给定模型的输入令牌总数计算的。

## 5. Tokens

- [Tokens是什么及如何计算？](https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them)
- [Tokens计算工具](https://platform.openai.com/tokenizer)
- 可以通过编程方式对文本进行token化，使用 `Tiktoken`，这是一个专门用于OpenAI模型的快速BPE tokenizer。
- [Tiktoken GitHub](https://github.com/openai/tiktoken)

## 6. 使用政策

- 数据使用政策从2023年3月1日开始做出了两项更改：
  - 除非您明确决定与我们共享您的数据，否则OpenAI将不会使用通过我们的API提交的数据来训练或改进我们的模型。您可以选择选择加入以共享数据。
  - API数据保留用于滥用和误用监控目的，最长时间为30天，之后将被删除（除非法律另有规定）。
  - OpenAI为了滥用和误用监控目的保留API数据30天。少数经过授权的OpenAI员工以及受保密和安全义务约束的专业第三方承包商可以访问此数据，仅用于调查和验证涉嫌滥用行为。部署低误用可能性用例的企业客户可以请求根本不存储API数据，包括用于安全监控和预防。

### OpenAI的能力

1. **语音转文本**
   - Audio API基于我们最先进的开源大型v2 Whisper模型，提供了两个语音转文本端点：转录和翻译。
   - 它们可以用于将音频转录为音频中的语言或将音频翻译并转录为英语。
   - 文件上传目前限制为25 MB，支持的输入文件类型包括：mp3、mp4、mpeg、mpga、m4a、wav和webm。

2. **文本生成模型**
   - OpenAI的文本生成模型（通常称为生成预训练变压器或大型语言模型）已被训练来理解自然语言、代码和图像。模型根据输入提供文本输出。
   - 使用OpenAI的文本生成模型，您可以构建以下应用程序：
     - 起草文档
     - 编写计算机代码
     - 回答关于知识库的问题
     - 分析文本
     - 为软件提供自然语言接口
     - 辅导各种学科
     - 翻译语言
     - 为游戏模拟角色

## 7. 工具和调试

- [API Key 管理](https://platform.openai.com/api-keys)
- [API Key 使用](https://platform.openai.com/usage)
- [调试工具](https://openai.apifox.cn/endpoint-123512277)
- [Prompt 示例](https://platform.openai.com/docs/examples)
- [社区资源](https://platform.openai.com/docs/libraries/python-library)

### Tokens计算和示例

- [Token计算工具](https://platform.openai.com/tokenizer)
- [Tiktoken GitHub](https://github.com/openai/tiktoken)
- [Prompt 示例](https://platform.openai.com/docs/examples)

## 8. TODO

1. 分批请求
2. **BPE**（Byte Pair Encoding）是一种分词算法，常用于自然语言处理。它通过逐步合并出现频率最高的字符或字符对，将文本转化为子词单元。这个方法可以有效处理罕见词和未见词，提高模型的泛化能力。BPE分词器特别适合与预训练的语言模型，如OpenAI的模型，进行无缝集成。
3. **Ktor HTTP client**
   - Ktor HTTP客户端是一个强大的工具，用于在Kotlin应用程序中进行HTTP请求。它支持多种引擎，如CIO、Apache、OkHttp等，可以在不同的平台上使用。客户端允许配置请求、添加拦截器、处理响应等。其功能包括异步请求、表单提交、文件上传下载等。使用Ktor HTTP客户端可以轻松实现网络通信，满足复杂的应用需求。
   - 官网：[Ktor](https://ktor.io/)

## 9. 其他资源

- **Awesome ChatGPT Prompts**
- **FlowGPT**
- **r/PromptDesign** （以及类似的子版块）
- **OpenAI Discord**
- **OpenAI 工具合集**: [工具链接](https://xiniushu.com/#doc_tool)
- [Clarified](https://community.openai.com/t/message-no-credit-grants-found-in-the-new-api-openai-accounts/712611): 新注册的账户也不送了
