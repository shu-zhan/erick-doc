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

### Langchain

- [官方文档](https://reference.langchain.com/python/langchain/overview)
- 对应的api可以去页面搜索

![image-20260708234359753](https://skillset.oss-cn-shanghai.aliyuncs.com/image-20260708234359753.png)

```bash
pip install langchain==1.3.11
```

#### ChatDeepSeek

- LangChain为一些大模型专门提供了对应的Model类

```bash
pip install langchain-deepseek==1.1.0

# 管理环境变量的包
pip install python-dotenv==1.2.2
```





### openai调用

```bash
pip install openai==2.44.0
```

