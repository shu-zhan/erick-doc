# AI

- AI: 人工智能，Artificial Intelligence。 使机器能够像人类一样思考，学习和解决问题的技术

## 发展历史

![image-20260213003736554](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213003736554.png)

## NLP

- 深度学习的一个分支
- 自然语言处理：Natural Language Processing，其中的关键技术是 Transformer

## LLM

- 大模型：Large Language Models
- 比如： GPT, DeepSeek底层都是采用Transformer神经网络模型

![image-20260213004530673](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213004530673.png)

## Transformer

- 神经网络模型，最早是2017年由google团队的论文中提出来的

```bash
# 应用场景
1. machine translation     翻译
2. voice-to-text           语音生成文字
3. text-to-iamge           文字生成图片
4. 推理预测                 用在推理预测(自回归)
```

- 将生成的内容，再次带入到Transformer中进行处理：所以是一般是一个字一个字生成的

![image-20260213005315935](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213005315935.png)

## 大模型应用(Hybrid AI)

- 基于LLM的推理，分析，生成能力，结合传统编程能力，开发出的各种应用
- 二者进行结合(会话记忆)

### 大模型 vs 传统

![image-20260213015736166](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213015736166.png)

### 主流大模型

![image-20260213020026174](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213020026174.png)

 ### 大模型产品

![image-20260213020250466](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213020250466.png)

## AI应用开发架构

![image-20260213020443946](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213020443946.png)

### 纯Prompt问答

![](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213020546769.png)

### Function Calling

![image-20260213020856902](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213020856902.png)

### RAG

- Retrieval Augmented Generation: 给大模型外挂一个知识库，让大模型基于知识库内容做推理和回答

![image-20260213021307095](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213021307095.png)

### Fine-tuning

- 模型微调

# LLM部署

- 云部署/本地部署
- 开放API: 一些预先训练好的LLM的服务提供商，通过公共云来提供开放式的API

## OpenAI

- 目前全球最顶尖、影响力最大的 AI 公司之一。代表作是 ChatGPT 和 GPT 大模型。是整个 LLM 时代的开山鼻祖之一
- 几乎所有大模型 API 都在模仿 OpenAI 的格式

## 阿里云百炼

- 会有多种多样的LLM的模型：[模型广场](https://bailian.console.aliyun.com/cn-beijing/?spm=5176.29619931.J_SEsSjsNv72yRuRFS2VknO.2.607b10d7LFm4OF&tab=model#/model-market)

![image-20260213011410026](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213011410026.png)

### API KEY

- 用来调用LLM的对应的权限

![image-20260213011836055](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260213011836055.png)

### DeepSeek-V3.2

- [OpenAI](https://bailian.console.aliyun.com/cn-beijing/?spm=5176.29619931.J_SEsSjsNv72yRuRFS2VknO.2.607b10d7LFm4OF&tab=api#/api/?type=model&url=3016807)

```bash
# 代码解读
stream=true:     流式输出，回答是一个个蹦的，关闭后，一下子蹦出来
model：          对应的大模型的名字
baseUrl/api key
temperature：    采样温度，控制模型生成文本的多样性。越高，生成的文本更多样，反之，生成的文本更确定。0～2

# messages
System Message object （可选）
系统消息，用于设定大模型的角色、语气、任务目标或约束条件等。一般放在messages数组的第一位。

User Message object （必选）
用户消息，用于向模型传递问题、指令或上下文等。

# Prompt
- 提示词，我们在AI中问的问题
```

