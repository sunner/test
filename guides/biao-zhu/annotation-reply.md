# 标注回复

标注回复功能通过人工编辑标注为应用提供了可定制的高质量问答回复能力。

适用情景：

* **特定领域的定制化回答：** 在企业、政府等客服或知识库问答情景时，对于某些特定问题，服务提供方希望确保系统以明确的结果来回答问题，因此需要对在特定问题上定制化输出结果。比如定制某些问题的“标准答案”或某些问题“不可回答”。
* **POC 或 DEMO 产品快速调优：** 在快速搭建原型产品，通过标注回复实现的定制化回答可以高效提升问答结果的生成预期，提升客户满意度。

标注回复功能相当于提供了另一套检索增强系统，可以跳过 LLM 的生成环节，规避 RAG 的生成幻觉问题。

### 使用流程

1. 在开启标注回复功能之后，你可以对 LLM 对话回复内容进行标注，你可以将 LLM 回复的高质量答案直接添加为一条标注，也可以根据自己的需求编辑一条高质量答案，这些编辑的标注内容会被持久化保存；
2. 当用户再次提问相似的问题时，会将问题向量化并查询中与之相似的标注问题；
3. 如果找到匹配项，则直接返回标注中与问题相对应的答案，不再传递至 LLM 或 RAG 过程进行回复；
4. 如果没有找到匹配项，则问题继续常规流程（传递至 LLM 或 RAG）；
5. 关闭标注回复功能后，系统将一直不再继续从标注内匹配回复。

<figure><img src="../../.gitbook/assets/image (181).png" alt="" width="563"><figcaption><p>标注回复流程</p></figcaption></figure>

### 提示词编排中开启标注回复

进入“应用构建->添加功能”开启标注回复开关：

<figure><img src="../../.gitbook/assets/image (124).png" alt=""><figcaption><p>提示词编排中开启标注回复</p></figcaption></figure>

开启时需要先设置标注回复的参数，可设置参数包括：Score 阈值 和 Embedding 模型

**Score 阈值**：用于设置标注回复的匹配相似度阈值，只有高于阈值分数的标注会被召回。

**Embedding 模型**：用于对标注文本进行向量化，切换模型时会重新生成嵌入。

点击保存并启用时，该设置会立即生效，系统将对所有已保存的标注利用 Embedding 模型生成嵌入保存。

<figure><img src="../../.gitbook/assets/image (126).png" alt=""><figcaption><p>标注回复参数设置</p></figcaption></figure>

### 在会话调试页添加标注

你可以在调试与预览页面直接在模型回复信息上添加或编辑标注。

<figure><img src="../../.gitbook/assets/image (128).png" alt=""><figcaption><p>添加标注回复</p></figcaption></figure>

编辑成你需要的高质量回复并保存。

<figure><img src="../../.gitbook/assets/image (129).png" alt=""><figcaption><p>编辑标注回复</p></figcaption></figure>

再次输入同样的用户问题，系统将使用已保存的标注直接回复用户问题。

<figure><img src="../../.gitbook/assets/image (130).png" alt=""><figcaption><p>通过已保存的标注回复用户问题</p></figcaption></figure>

### 日志与标注中开启标注回复

进入“应用构建->日志与标注->标注”开启标注回复开关：

<figure><img src="../../.gitbook/assets/image (118).png" alt=""><figcaption><p>日志与标注中开启标注回复</p></figcaption></figure>

### 在标注后台设置标注回复参数

标注回复可设置的参数包括：Score 阈值 和 Embedding 模型

**Score 阈值**：用于设置标注回复的匹配相似度阈值，只有高于阈值分数的标注会被召回。

**Embedding 模型**：用于对标注文本进行向量化，切换模型时会重新生成嵌入。

<figure><img src="../../.gitbook/assets/image (119).png" alt=""><figcaption><p>设置标注回复参数</p></figcaption></figure>

### 批量导入标注问答对

在批量导入功能内，你可以下载标注导入模板，按模版格式编辑标注问答对，编辑好后在此批量导入。

<figure><img src="../../.gitbook/assets/image (120).png" alt=""><figcaption><p>批量导入标注问答对</p></figcaption></figure>

### 批量导出标注问答对

通过标注批量导出功能，你可以一次性导出系统内已保存的所有标注问答对。

<figure><img src="../../.gitbook/assets/image (121).png" alt=""><figcaption><p>批量导出标注问答对</p></figcaption></figure>

### 查看标注回复命中历史

在标注命中历史功能内，你可以查看所有命中该条标注的编辑历史、命中的用户问题、回复答案、命中来源、匹配相似分数、命中时间等信息，你可以根据这些系统信息持续改进你的标注内容。

<figure><img src="../../.gitbook/assets/image (123).png" alt=""><figcaption><p>查看标注回复命中历史</p></figcaption></figure>
