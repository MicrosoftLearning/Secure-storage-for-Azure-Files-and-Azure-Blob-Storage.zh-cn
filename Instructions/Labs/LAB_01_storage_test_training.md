---
lab:
  title: 练习 1 - 为 IT 部门的测试和培训工作提供存储
  module: Guided Project - Azure Files and Azure Blobs
---

IT 部门需要为不同的存储方案创建原型并培训新人员。 内容不够重要，无法备份，如果数据被覆盖或删除，则无需还原。 需要可以轻松更改的简单配置。

## 体系结构关系图
![包含一个存储帐户的示意图](../Media/task-1.png)

## 技能任务
- 创建存储帐户。 
- 针对安全性和网络配置基本设置。 

## 练习说明

## 创建资源组和存储帐户。

1. 创建并部署资源组以保留所有项目资源。 了解有关 [资源组](https://learn.microsoft.com/azure/azure-resource-manager/management/manage-resource-groups-portal)的详细信息。
    - 在 Azure 门户中，搜索并选择 `Resource groups`。
    - 选择“+ 新建”。
    - 为资源组指定名称****。 例如，`storagerg`。
    - 选择区域****。 在整个项目中使用此区域。 
    - 选择“查看并创建”**** 以验证资源组。
    - 选择“创建”**** 以部署资源组。

1. 创建和部署存储帐户以支持测试和训练。 详细了解[存储帐户类型](https://learn.microsoft.com/azure/storage/common/storage-account-overview#types-of-storage-accounts)。
    - 在 Azure 门户中，搜索并选择 `Storage accounts`。 
    - 选择“+ 新建”。
    - 在“基本”选项卡上，选择所需资源组********。
    - 提供存储帐户名称****。 在 Azure 中，存储帐户名必须是唯一的。 
    - 将“性能”设置为“标准”********。 
    - 选择“查看”，然后选择“创建”。 
    - 等待存储帐户部署完成，然后单击“转到资源”****。  

## 在存储帐户中配置简单设置。

1. 此存储帐户中的数据不需要高可用性或持久性。 需要成本最低的存储解决方案。 详细了解[存储帐户冗余](https://learn.microsoft.com/azure/storage/common/storage-redundancy#locally-redundant-storage)。
    - 在存储帐户的“数据管理”**** 部分中，选择“冗余”**** 边栏选项卡。
    - 在“冗余”下拉列表中，选择“本地冗余存储(LRS)”********。 
    - 务必保存你的更改。 
    - 刷新页面并注意内容仅存在于主要位置。 

1. 存储帐户应仅接受来自安全连接的请求。 详细了解[如何要求从安全连接进行安全传输](https://learn.microsoft.com/azure/storage/common/storage-require-secure-transfer)
    - 在“设置”**** 部分选择“配置”**** 边栏选项卡。
    - 确保将“需要安全传输”**** 设置为“已启用”****。 

1. 开发人员希望存储帐户至少使用 TLS 版本 1.2。 详细了解[传输层安全 (TLS)](https://learn.microsoft.com//azure/storage/common/transport-layer-security-configure-minimum-version?tabs=portal)。
    - 在“设置”**** 部分选择“配置”**** 边栏选项卡。
    - 确保将“最低 TLS 版本”设置为“版本 1.2”********。  


1. 在再次需要使用存储之前，请禁用对存储帐户的请求。 详细了解[禁用共享密钥](https://learn.microsoft.com/azure/storage/common/shared-key-authorization-prevent?tabs=portal#disable-shared-key-authorization)。
    - 在“设置”**** 部分选择“配置”**** 边栏选项卡。
    - 确保将“允许存储帐户密钥访问”**** 设置为“已禁用”****。
    - 务必保存你的更改。 

1. 确保允许从所有网络公开访问存储帐户。  
    - 在“安全 + 网络”**** 部分中，选择“网络”**** 边栏选项卡。
    - 确保将“公用网络访问权限”**** 设置为“已从所有网络启用”****。
    - 务必保存你的更改。 

>**备注**：如需进行额外练习，请完成[创建 Azure 存储帐户](https://learn.microsoft.com/training/modules/create-azure-storage-account/)模块。 该模块有一个沙盒，可在其中练习创建存储帐户。

## 使用 Copilot 扩展学习

Copilot 可以协助你完成学习之旅。 Copilot 可以提供基本的技术信息、高级步骤、优点和缺点、故障排除帮助、用例、编码示例等。 要访问 Copilot，请打开 Edge 浏览器，然后选择 Copilot（右上角）。 花几分钟时间尝试这些提示。
+ 什么是 Azure 存储帐户？ 有哪些 Azure 存储帐户类型可用？
+ 创建比较 Azure 存储性能层的表。 重点介绍其关键功能和用例。 
+ 有哪些 Azure 存储冗余选项可用？ 应何时使用每个选项？

## 通过自定进度的培训了解详细信息

+ [介绍 Azure 存储服务](https://learn.microsoft.com/training/modules/describe-azure-storage-services/)。 在本模块中，你将比较 Azure 存储服务、描述存储层，以及描述冗余选项。
+ [创建 Azure 存储帐户](https://learn.microsoft.com/training/modules/create-azure-storage-account/)。 在本模块中，你将创建和配置存储帐户。 

## 关键结论

恭喜你完成本实验室的内容。 下面是本实验室的主要重点。 
+ Azure 存储帐户是一个容器，用于保存包括 Blob、文件、队列和表在内的所有 Azure 存储数据对象。
+ Azure 存储提供多种类型的存储帐户：标准和高级。 每种类型支持不同的功能，并且具有自己的定价模型。
+ Azure 存储会始终存储数据的多个副本，以保护它免受计划内和计划外事件的影响。
+ 冗余模型可以复制主要区域和次要区域中的数据。 
