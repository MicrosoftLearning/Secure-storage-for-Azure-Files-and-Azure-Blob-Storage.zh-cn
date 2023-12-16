---
demo:
  title: 演示 01：创建和配置存储帐户
  module: Guided Project - Azure Files and Azure Blobs
---
## 演示 - 创建和配置存储帐户 

在本演示中，我们将探索存储帐户。

1. [支持幻灯片] 在开始此演示之前，可能需要讨论存储的组织方式和考虑因素。 

1. 访问 **Azure 门户**。

1. 在“搜索”框中，键入“存储帐户”****。 开始键入时，会根据输入筛选该列表。

1. 选择“存储帐户”****。

1. 选择**创建**。

1. 说明 Azure 门户如何提供易于使用的向导界面。 提醒学生，标有红色星号的项是必填项。

1. 选择“订阅”****。

1. 选择“资源组”****。

1. 为存储帐户输入名称。 讨论存储帐户命名限制。

1. 选择存储帐户的区域。 查看学生应在实验室中使用的区域。 了解有关 [Azure 地域](https://azure.microsoft.com/explore/global-infrastructure/geographies/)的详细信息。

1. [支持幻灯片] 选择“标准”**** 性能。 详细了解[存储帐户的类型](https://learn.microsoft.com/azure/storage/common/storage-account-overview)。

1. [支持幻灯片] 选择“冗余”**** 作为“本地冗余”**** 存储。 详细了解 [Azure 存储冗余](https://docs.microsoft.com/azure/storage/common/storage-redundancy)。

1. 移动到“高级”**** 选项卡。在“安全”**** 部分中突出显示这些设置。 请注意，我们只介绍了少量内容，以帮助学生开始完成他们的第一个实验室。 

    - **需要为 REST API 操作使用安全传输**。 默认情况下，仅接受来自安全连接的存储帐户请求。 详细了解[安全传输](https://learn.microsoft.com/azure/storage/common/storage-require-secure-transfer)。

    - **启用存储帐户密钥访问权限**。 讨论此设置可如何禁用对存储帐户的访问。 例如，可以禁用对 IT 部门存储帐户的访问。 讨论保护密钥的重要性。 详细了解[管理存储帐户访问密钥](https://learn.microsoft.com/azure/storage/common/storage-account-keys-manage?tabs=azure-portal)。

    - **最低 TLS 版本**。 说明传输层服务的作用是保护网络通信安全。 TLS 是 SSL 的改进版本。 开发人员可能会询问可用的版本。 详细了解[传输层服务](https://learn.microsoft.com/azure/storage/common/transport-layer-security-configure-minimum-version)。

1. 说明在学生完成实验室的过程中，会对其他选项卡进行介绍。

1. 选择“查看”****，并确保没有验证错误。 讨论可能的验证错误。 

1. 选择“创建”**** 并在部署存储帐户时等待。 指出通知消息。

1. 演示如何转到资源****。 讨论访问资源的其他方法。

>**备注**：学生现在应该能够完成 LAB_01。
