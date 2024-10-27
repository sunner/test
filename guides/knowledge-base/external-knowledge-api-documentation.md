---
description: 作者： Allen。 Dify Technical Writer。
---

# 外部知识库 API

## 端点

```
POST <your-endpoint>/retrieval
```

## 请求头

该 API 用于连接团队内独立维护的知识库，如需了解更多操作指引，请参考阅读 [连接外部知识库](https://docs.dify.ai/zh-hans/guides/knowledge-base/connect-external-knowledge-base)。你可以在 HTTP 请求头的 `Authorization` 字段中使用 `API-Key` 来验证权限。身份验证逻辑由您在检索 API 中定义，如下所示：

```
Authorization: Bearer {API_KEY}
```

## 请求体元素

请求接受以下 JSON 格式的数据。

| 属性 | 是否必需 | 类型 | 描述 | 示例值 |
|------|----------|------|------|--------|
| knowledge_id | 是 | 字符串 | 知识库唯一 ID | AAA-BBB-CCC |
| query | 是 | 字符串 | 用户的查询 | Dify 是什么？ |
| retrieval_setting | 是 | 对象 | 知识检索参数 | 见下文 |

`retrieval_setting` 属性是一个包含以下键的对象：

| 属性 | 是否必需 | 类型 | 描述 | 示例值 |
|------|----------|------|------|--------|
| top_k | 是 | 整数 | 检索结果的最大数量 | 5 |
| score_threshold | 是 | 浮点数 | 结果与查询相关性的分数限制，范围：0~1 | 0.5 |

## 请求语法

```json
POST <your-endpoint>/retrieval HTTP/1.1
-- 请求头
Content-Type: application/json
Authorization: Bearer your-api-key
-- 数据
{
    "knowledge_id": "your-knowledge-id",
    "query": "你的问题",
    "retrieval_setting":{
        "top_k": 2,
        "score_threshold": 0.5
    }
}
```

## 响应元素

如果操作成功，服务将返回 HTTP 200 响应。服务以 JSON 格式返回以下数据。

| 属性 | 是否必需 | 类型 | 描述 | 示例值 |
|------|----------|------|------|--------|
| records | 是 | 对象列表 | 从知识库查询的记录列表 | 见下文 |

`records` 属性是一个包含以下键的对象列表：

| 属性 | 是否必需 | 类型 | 描述 | 示例值 |
|------|----------|------|------|--------|
| content | 是 | 字符串 | 包含知识库中数据源的文本块 | Dify：GenAI 应用程序的创新引擎 |
| score | 是 | 浮点数 | 结果与查询的相关性分数，范围：0~1 | 0.5 |
| title | 是 | 字符串 | 文档标题 | Dify 简介 |
| metadata | 否 | json | 包含数据源中文档的元数据属性及其值 | 见示例 |

## 响应语法

```json
HTTP/1.1 200
Content-type: application/json
{
    "records": [{
                    "metadata": {
                            "path": "s3://dify/knowledge.txt",
                            "description": "dify 知识文档"
                    },
                    "score": 0.98,
                    "title": "knowledge.txt",
                    "content": "这是外部知识的文档。"
            },
            {
                    "metadata": {
                            "path": "s3://dify/introduce.txt",
                            "description": "dify 介绍"
                    },
                    "score": 0.66,
                    "title": "introduce.txt",
                    "content": "GenAI 应用程序的创新引擎"
            }
    ]
}
```

## 错误

如果操作失败，服务将返回以下错误信息（JSON 格式）：

| 属性 | 是否必需 | 类型 | 描述 | 示例值 |
|------|----------|------|------|--------|
| error_code | 是 | 整数 | 错误代码 | 1001 |
| error_msg | 是 | 字符串 | API 异常描述 | 无效的 Authorization 头格式。预期格式为 'Bearer <api-key>'。 |

`error_code` 属性有以下类型：

| 代码 | 描述 |
|------|------|
| 1001 | 无效的 Authorization 头格式 |
| 1002 | 授权失败 |
| 2001 | 知识库不存在 |

### HTTP 状态码

**AccessDeniedException**
由于缺少访问权限，请求被拒绝。请检查您的权限并重试。
HTTP 状态码：403

**InternalServerException**
发生内部服务器错误。请重试您的请求。
HTTP 状态码：500