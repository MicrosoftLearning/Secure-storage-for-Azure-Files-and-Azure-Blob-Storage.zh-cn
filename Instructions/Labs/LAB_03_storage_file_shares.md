---
lab:
  title: 练习 03：为公司办公室提供共享文件存储
  module: Guided Project - Azure Files and Azure Blobs
---


公司的办公室分散在不同的地理位置。  这些办事处需要一种共享文件和传播信息的方式。 例如，财务部门需要确认用于审计和合规性的成本信息。 这种文件共享应易于访问和加载，且不会延迟。 某些内容只能从选定的企业虚拟网络访问。


## 体系结构关系图

![包含存储帐户、文件共享和目录的示意图](../Media/task-4.png)

## 技能任务
- 为文件共享创建专门的存储帐户。 
- 配置文件共享和目录。  
- 配置快照并练习如何还原文件。 
- 限制对特定虚拟网络和子网的访问。 

## 练习说明

>**备注**：要完成此实验室，你将需要有 Azure 订阅[](https://azure.microsoft.com/free/)。

## 为 Azure 文件存储创建和配置存储帐户。 

1. 为财务部门的共享文件创建存储帐户。  详细了解 [Azure 文件存储部署](https://learn.microsoft.com/azure/storage/files/storage-files-planning#management-concepts)的存储帐户。

    - 在门户中，搜索并选择 `Storage accounts`。
    - 选择“+ 新建”。
    - 对于“资源组”****，选择“新建”****。 为资源组指定一个名称****，然后选择“确定”**** 以保存更改。 
    - 提供存储帐户名称****。 确保名称满足命名要求。 
    - 将“性能”**** 设置为“高级”****。
    - 将“高级帐户类型”**** 设置为“文件共享”****。
    - 将“冗余”**** 设置为“区域冗余存储”****。
    - 选择“查看”****，然后创建**** 存储帐户。
    - 等待资源部署完毕。
    - 选择“转到资源”。 

## 使用目录创建和配置文件共享。

1. 为公司办公室创建文件共享。 详细了解 [Azure 文件层](https://learn.microsoft.com/azure/storage/files/storage-files-planning#storage-tiers)。

    - 在“存储帐户”的“数据存储”**** 部分中，选择“文件共享”**** 边栏选项卡。 
    - 选择“+ 文件共享”**** 并提供“名称”****。
    - 查看其他选项，但采用默认值。
    - 选择“创建”

1. 将目录添加到财务部门的文件共享。 上传文件供将来调试。 

    - 选择文件共享，然后选择“+ 添加目录”****。 
    - 为新目录 `finance` 命名。
    - 选择“浏览”****，然后选择“财务”**** 目录。
    - 请注意，可以添加目录**** 以进一步组织文件共享。
    - 上传**** 选择的文件。 

## 配置和测试快照。

1. 与 Blob 存储类似，需要防止意外删除文件。 你决定使用快照。 详细了解[文件快照](https://learn.microsoft.com/azure/storage/files/storage-snapshots-files)。
    
    - 选择文件共享。
    - 在“操作”**** 部分中，选择“快照”**** 边栏选项卡。 
    - 选择“+ 添加快照”****。 注释是可选的。 选择“确定”****。
    - 选择快照并验证文件目录和上传的文件是否包含在内。
  
1. 练习使用快照还原文件。
    - 返回到“文件共享”****。
    - 浏览**** 到文件目录。 
    - 找到已上传的文件，然后在“属性”**** 窗格中选择“删除”****。 选择“是”确认删除。**** 
    - 选择“快照”**** 边栏选项卡，然后选择快照。 
    - 浏览到想要还原的文件，
    - 选择文件，然后选择“还原”****。
    - 提供已还原文件的名称****。 
    - 验证文件目录中是否有已还原的文件。  

## 将存储访问限制配置为仅限选定的虚拟网络。

1. 本部分中的此任务需要具有子网的虚拟网络。 在生产环境中，这些资源已创建。
    - 搜索并选择“虚拟网络”。****
        - 选择**创建**。 选择资源组。 为虚拟网络指定名称****。
        - 为其他参数采用默认值，选择“查看 + 创建”****，然后选择“创建”****。
        - 等待资源部署完毕。
        - 选择“转到资源”。 
    - 在“设置”**** 部分中，选择“子网”**** 边栏选项卡。
        - 选择默认子网。
        - 在“服务终结点”**** 部分的“服务”**** 下拉列表中，选择“Microsoft.Storage”****。
        - 请勿进行任何其他更改。    
        - 务必保存你的更改。 
   
1. 只能从刚刚创建的虚拟网络访问此存储帐户。 了解有关使用[专用存储终结点](https://learn.microsoft.com/azure/storage/common/storage-private-endpoints)的详细信息。

    - 返回到“文件存储帐户”****。 
    - 在“安全 + 网络”**** 部分中，选择“网络”**** 边栏选项卡。
        - 将“公共网络访问”更改为“从选定的虚拟网络和 IP 地址启用”********。
        - 在“虚拟网络”**** 部分，选择“添加现有虚拟网络”****。
        - 选择你的虚拟网络和子网，然后选择“添加”****。
        - 务必保存你的更改。 
    - 选择“存储浏览器”并导航到文件共享****。 
    - 验证消息无权执行此操作**。 你未从虚拟网络进行连接。 


>**备注**：有关其他练习，请完成“配置 Azure 存储安全”[](https://learn.microsoft.com/training/modules/configure-storage-security/)模块。 该模块具有交互式实验室模拟，可在其中进行更多创建安全存储的练习。 

## 使用 Copilot 扩展学习

Copilot 可以协助你完成学习之旅。 Copilot 可以提供基本的技术信息、高级步骤、优点和缺点、故障排除帮助、用例、编码示例等。 要访问 Copilot，请打开 Edge 浏览器，然后选择 Copilot（右上角）。 花几分钟时间尝试这些提示。
+ 什么是 Azure 文件存储，它与 Azure Blob 存储有何不同？ 我如何决定使用哪一个？
+ 保护 Azure 文件内容安全的不同方法有哪些？

## 通过自定进度的培训了解详细信息

+ [配置 Azure 文件存储和 Azure 文件同步](https://learn.microsoft.com/en-us/training/modules/configure-azure-files-file-sync/)。在本模块介绍如何配置 Azure 文件共享和文件共享快照。

## 关键结论

恭喜你完成本实验室的内容。 下面是本实验室的主要重点。 
+ Azure 文件存储在云中提供完全托管的文件共享，这些共享项可通过行业标准的服务器消息块 (SMB) 协议、网络文件系统 (NFS) 协议和 Azure 文件存储 REST API 进行访问。
+ Azure 文件提供了获取 SMB 和 NFS 文件共享的快照的功能。 共享快照可以捕获在某个时间点的共享状态。 共享快照只提供文件级保护。
+ 可以配置存储帐户终结点，以便直接访问 Azure 文件共享。 用于限制对存储帐户进行网络访问的终结点。

