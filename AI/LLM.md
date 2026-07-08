# 大模型调用

- python version = 3.13.12

## DeepSeek

- DeepSeek官网的DeepSeek模型

### 前置工作

- [官网Platform](https://platform.deepseek.com/usage)：首先完成个人用户认证，然后充值

![image-20260708231842853](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260708231842853.png)

- 创建对应的API KEY，创建好以后立刻保存

![image-20260708232031682](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260708232031682.png)

- [API文档](https://api-docs.deepseek.com/zh-cn/)

### openai调用

```bash
pip install openai==2.44.0

# 管理环境变量的包
pip install python-dotenv==1.2.2
```

```bash
# 对应的 .env文件
DEEPSEEK_API_KEY=sk-004a0a65074b7fa47b352
# open ai
DEEPSEEK_BASE_URL=https://api.deepseek.com
```

```python
import os

from dotenv import load_dotenv
from openai import OpenAI

# 读取 .env配置文件的信息，如果当前有类似的环境变量，则用 .env的对其进行覆盖
load_dotenv(override=True)

client = OpenAI(
    api_key=os.getenv("DEEPSEEK_API_KEY"),  # 传统风格
    base_url=os.environ.get('DEEPSEEK_BASE_URL')  # Pythonic 风格
)

# noinspection PyTypeChecker
response = client.chat.completions.create(
    model="deepseek-v4-pro",
    messages=[
        {"role": "system", "content": "你是一个专业的 AI 助手"},
        {"role": "user", "content": "你是谁？"}
    ],
    stream=False,
    reasoning_effort="high",
    extra_body={"thinking": {"type": "enabled"}}
)

print(response.choices[0].message.content)
```

### Langchain

- [官方文档](https://reference.langchain.com/python/langchain/overview)
- 对应的api可以去页面搜索

![image-20260708234359753](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260708234359753.png)

```bash
pip install langchain==1.3.11
```

#### ChatOpenAi

- Langchain出的，对于不同的模型都能兼容的

```python
import os

from dotenv import load_dotenv
from langchain_core.messages import SystemMessage, HumanMessage
from langchain_openai import ChatOpenAI

load_dotenv(override=True)

# noinspection PyTypeChecker
deep_seek_llm = ChatOpenAI(
    model="deepseek-v4-pro",
    api_key=os.environ.get("DEEPSEEK_API_KEY"),
    base_url=os.environ.get('DEEPSEEK_BASE_URL')
)

messages = [
    SystemMessage(content="你是一个专业的 AI 助手"),
    HumanMessage(content="你是谁？")
]

response = deep_seek_llm.invoke(messages)
print(response.content)
```

#### init_chat_model

- 函数工厂式的写法

```python
import os

from dotenv import load_dotenv
from langchain.chat_models import init_chat_model
from langchain_core.messages import SystemMessage, HumanMessage

load_dotenv(override=True)

deep_seek_llm = init_chat_model(
    model="deepseek-v4-pro",
    model_provider="openai",  # 使用open ai协议
    base_url=os.environ.get("DEEPSEEK_BASE_URL"),
    api_key=os.environ.get("DEEPSEEK_API_KEY"),

)

messages = [
    SystemMessage(content="你是一个专业的 AI 助手"),
    HumanMessage(content="你是谁？")
]

response = deep_seek_llm.invoke(messages)
print(response.content)
```

## 阿里云百炼

```bash
ALI_QWEN_API_KEY=sk-8dced6fc7a703df759b181ea5
ALI_QWEN_BASE_URL=https://ws-eh8ig9jj6hshvg4c.cn-beijing.maas.aliyuncs.com/compatible-mode/v1
```

### openai调用

```python
import os

from dotenv import load_dotenv
from openai import OpenAI

load_dotenv(override=True)

client = OpenAI(
    api_key=os.environ.get("ALI_QWEN_API_KEY"),
    base_url=os.environ.get('ALI_QWEN_BASE_URL')
)

# noinspection PyTypeChecker
response = client.chat.completions.create(
    model="qwen3.7-max", # 模型名字
    messages=[
        {"role": "system", "content": "你是一个专业的 AI 助手"},
        {"role": "user", "content": "你是谁？哪家公司的？"}
    ],
    stream=False,
    reasoning_effort="high",
    extra_body={"thinking": {"type": "enabled"}}
)

print(response.choices[0].message.content)
```

### Langchain

#### ChatOpenAi

```python
import os

from dotenv import load_dotenv
from langchain_core.messages import SystemMessage, HumanMessage
from langchain_openai import ChatOpenAI

load_dotenv(override=True)

# noinspection PyTypeChecker
deep_seek_llm = ChatOpenAI(
    model="qwen3.7-max",
    api_key=os.environ.get("ALI_QWEN_API_KEY"),
    base_url=os.environ.get('ALI_QWEN_BASE_URL')
)

messages = [
    SystemMessage(content="你是一个专业的 AI 助手"),
    HumanMessage(content="你是谁？哪家公司的")
]

response = deep_seek_llm.invoke(messages)
print(response.content)
```

#### init_chat_model

```python
import os

from dotenv import load_dotenv
from langchain.chat_models import init_chat_model
from langchain_core.messages import SystemMessage, HumanMessage

load_dotenv(override=True)

deep_seek_llm = init_chat_model(
    model="qwen3.7-max",
    model_provider="openai",  # 使用open ai协议
    base_url=os.environ.get("ALI_QWEN_BASE_URL"),
    api_key=os.environ.get("ALI_QWEN_API_KEY"),

)

messages = [
    SystemMessage(content="你是一个专业的 AI 助手"),
    HumanMessage(content="你是谁？")
]

response = deep_seek_llm.invoke(messages)
print(response.content)
```

