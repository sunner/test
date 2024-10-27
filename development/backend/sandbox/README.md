# DifySandbox

### 介绍
`DifySandbox`是一个轻量、快速、安全的代码运行环境，支持多种编程语言，包括`Python`、`Nodejs`等，用户在`Dify Workflow`中使用到的如`Code`节点、`Template Transform`节点、`LLM`节点的Jinja2语法、`Tool`节点的`Code Interpreter`等都基于DifySandbox运行，它确保了`Dify`可以运行用户代码的前提下整个系统的安全性。

### 特性
- **多语言支持**：`DifySandbox`基于`Seccomp`，这是一个系统层级的解决方案，从而确保了可以支持多种编程语言，目前支持了`Python`与`Nodejs`。
- **系统安全**：使用白名单策略，只允许运行特定的系统调用，从而确保不会出现意外的绕过。
- **文件系统隔离**：用户代码将运行在一个独立的隔离的文件系统中。
- **网络隔离**:
    - **DockerCompose**：独立网络Sandbox网络，并使用代理容器进行网络访问，确保内网系统的安全，同时提供了灵活的代理配置方案。
    - **K8s**：直接使用`Exgress`配置网络隔离策略即可。

### 项目地址
你可以直接访问[DifySandbox](https://github.com/langgenius/dify-sandbox)获取项目源码，并遵循项目文档进行部署和使用。

### 贡献
你可以参考[贡献指南](contribution.md)来参与到`DifySandbox`的开发中。
