# ComfyUI
[ComfyUI](https://www.comfy.org/) 是一个强大的、模块化的生成图形的平台。现在你可以在 Dify 中使用它， 传入图片的提示词， 并得到生成的图片。

## 1. 确保已能正常运行 ComfyUI 的工作流。  
请参考其[官方文档](https://docs.comfy.org/get_started/gettingstarted)，确保 ComfyUI 可以正常运行并生成图片。

## 2. 导出工作流的 API 文件。
<figure><img src="../../../.gitbook/assets/comfyui.png" alt=""><figcaption></figcaption></figure>
如图所示，在工具栏中选择 `Save(API Format)`，如果没有该选择，则需要在设置中开启 `Dev Mode`。

## 3. 在 Dify 中集成 ComfyUI  
在 `工具 > ComfyUI > 去认证` 中填写访问地址，如果您使用的 docker 部署的 Dify，这个地址一般是 `http://host.docker.internal:8188`。

## 4. 在 Dify 中使用 ComfyUI
打开其 `工作流` 工具，在 `WORKFLOW JSON` 中填入刚刚导出的 API 文件中的内容，就可以正常生成了。
