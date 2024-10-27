---
description: 作者：Evanchen ,  Allen.
---

# 变更公告：图片上传被替换为文件上传

图片上传功能已被纳入至更加综合的[文件上传](file-upload.md)功能中，为了避免出现功能重复，我们决定对 Workflow 和 Chatflow 应用的“[附加功能](additional-features.md)”进行升级和调整：

* 移除 Chatflow 应用“功能”中的图片上传选项，取而代之的是新的“文件上传”功能。你可以在“文件上传”功能内选择图片文件类型。同时，应用对话框中的图片上传 icon 也被替换为文件上传 icon。

<figure><img src="../../.gitbook/assets/image (387).png" alt=""><figcaption></figcaption></figure>

* 将在未来**停用 Workflow 应用“功能”中的图片上传选项**以及移除 `sys.files` [变量](variables.md)，目前这两项功能已被标记为 `LEGACY`，建议应用开发者改用自定义文件变量为 Workflow 应用添加文件上传功能。

<figure><img src="../../.gitbook/assets/image (385).png" alt=""><figcaption></figcaption></figure>

### 为什么要替换“图片上传”功能？

Dify 此前仅支持上传图片文件。而在最新的版本中，已提供更加全面的文件上传能力，支持文档、图片、音视频文件或自定义文件格式，**图片上传能力已被更大的“文件上传”功能所包含。**应用开发者添加文件上传功能后，仅勾选“图片”类型文件即可开启图片上传能力。

为了避免功能重复所造成体验上的困扰，我们决定替换 Chatflow 应用内单独的图片上传功能，转而提供更加全面的文件上传能力；同时不再建议继续为 Workflow 应用开启图片上传功能。

### 更加全面的功能：文件上传

为了让应用具备更加强大的信息处理能力，本次更新我们新增了“文件上传”能力。相较于聊天文本，文档文件能够承载大量的信息，例如学术报告、法律合同。

* 文件上传功能允许将文件以 File variables 的形式在工作流应用中上传、解析、引用、和下载。
* 开发者现可轻松构建能理解和处理图片、音频、视频复杂工作的应用。

<figure><img src="../../.gitbook/assets/image (386).png" alt="" width="375"><figcaption></figcaption></figure>

因此不再建议使用单独的“图片上传”功能，而是改用更为综合全面的“文件上传”功能以增强应用体验。

### 你需要做什么？

#### **对于 Dify Cloud 用户：**

* **Chatflow 应用**

如果你已创建 Chatflow 应用并启用了“图片上传”功能，并在 LLM 节点中开启 Vision 功能，系统将自动完成功能切换，不会影响到应用的图片上传能力。如果需要更新并重新发布应用，需要在 LLM 节点中的 Vision 变量选择框指定文件变量后清除 checklist 中的 item，重新发布应用。

<figure><img src="../../.gitbook/assets/image (388).png" alt=""><figcaption></figcaption></figure>

如果你希望在 Chatflow 应用中添加“图片上传”功能，请在功能中开启“文件上传”，仅勾选“图片”类型。然后在 LLM 节点中启用 Vision 功能，并在其中填写 `sys.files` 变量。此时输入框将出现“回形针”的上传入口，详细说明请参考 [附加功能](additional-features.md)。

<figure><img src="../../.gitbook/assets/image (389).png" alt=""><figcaption></figcaption></figure>

* **Workflow 应用**

如果你已创建 Workflow 应用并启用了“图片上传”功能，并在 LLM 节点中开启 Vision 功能，此次变动当下不会产生任何影响但你需要做正式下线前完成手动迁移。

如果希望为 Workflow 应用开启“图片上传”功能，请在[开始](node/start.md)节点中添加文件变量。然后在后续的节点中引用该文件变量，不再继续使用 `sys.files` 变量。

#### 对于Dify 社区版或本地部署的企业版用户：

升级到 v0.10.0 版本后你将看到 “文件上传” 功能。

* **Chatflow 应用**

已启用“图片上传”功能的 Chatflow 应用将自动完成切换，无需变更。

如果你希望在 Chatflow 应用中添加“图片上传”功能，详细说明请参考[附加功能](additional-features.md)。

* Workflow 应用

已创建的 Workflow 应用不会产生任何影响，但是请在正式下线前完成手动迁移。

如果希望为 Workflow 应用开启“图片上传”功能，请在[开始](node/start.md)节点中添加文件变量。然后在后续的节点中引用该文件变量，不再继续使用 `sys.files` 变量。

### 常见问题

1. **这次更新会影响我现有的应用吗？**

* 已创建的 Chatflow 应用将自动迁移，图片上传功无感切换至文件上传功能。仍然会默认使用 sys.file 作为模型 vision 输入框的变量。应用使用页的图片上传入口会被替换为文件上传入口。
* 现有 Workflow 应用暂时不会受到影响。`sys.file` 和图片上传功能会被标记为 `Legacy` ，但仍然可以使用。被标记为 `Legacy` 的功能将在未来下线，届时需要手动更新应用。

2. **我需要立即更新我的应用吗？**

* 对于 Chatflow 应用,系统会自动迁移，无需手动更新。
* 对于 Workflow 应用，虽然不需要立即更新，但建议你尽早熟悉新的文件上传功能，为未来的迁移做准备。

3. **如何确保我的应用兼容新的文件上传功能？**

对于 Chatflow 应用:

* 检查 features 配置中的文件上传选项是否已开启。
* 确保使用带有视觉能力的 LLM，并打开 Vision 功能开关。
* 验证 `sys.files` 是否被正确选中作 Vision 框中的输入项。

对于 Workflow 应用:

* 在“开始节点”创建文件类型的变量。
* 在后续的节点中引用这个文件变量，而不是使用已被标记为 `Legacy` 的 `sys.files`。

### 我们期待您的反馈

作为 Dify 社区的重要成员，您的使用体验和反馈对我们至关重要。我们诚挚地邀请您：

1. 尝试新的文件上传功能，体验其便捷性和灵活性。
2. 通过以下渠道分享您的想法和建议：
   * [GitHub](https://github.com/langgenius/dify)
   * [Discord 频道](https://discord.gg/FngNHpbcY7)

您的每一条反馈都将帮助我们不断完善产品，为整个社区带来更好的体验。

