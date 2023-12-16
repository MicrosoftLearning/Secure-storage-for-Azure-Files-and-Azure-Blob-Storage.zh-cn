---
lab:
  title: 练习 02b：为公司内部文档提供专用存储
  module: Guided Project - Azure Files and Azure Blobs
---


公司需要为其办公室和部门提供存储。 此内容为公司专属内容，未经同意不得共享。 如果发生区域性中断，此存储需要高可用性。 公司希望使用此存储来备份公共网站。 

## 体系结构关系图

![显示一个存储帐户和两个 Blob 容器的示意图](../Media/task-3.png)

## 技能任务
- 为公司专用文档创建存储帐户。
- 为存储帐户配置冗余。 
- 配置共享访问签名，以便合作伙伴对文件有受限的访问权限。 
- 备份公共网站存储。
- 实现生命周期管理，将内容移动到冷层。

## 练习说明

> **备注**：在按照这些说明操作之前，你必须已完成实验室 02a****，也就是为内部文档提供存储。

## 创建存储帐户并配置高可用性。

1. 为内部专用公司文档创建存储帐户。
    - 在门户中，搜索并选择“存储帐户”。  
    - 选择“+ 新建”。 
    - 选择在上一个实验室中创建的“资源组”****。   
    - 将“存储帐户名称”**** 设置为 `private`。 向名称添加标识符以确保名称是唯一的。 
    - 选择“查看”****，然后创建**** 存储帐户。 
    - 等待存储帐户部署完成，然后选择“转到资源”****。

1. 如果发生区域性中断，此存储需要高可用性。 不需要次要区域中的读取访问权限。 配置适当的冗余级别****。 

    - 在“存储帐户”的“数据管理”**** 部分中，选择“冗余”**** 边栏选项卡。 
    - 确保已选择“异地冗余存储(GRS)”****。
    - 刷新页面。 
    - 查看主要位置和次要位置信息。 
    - **保存**所做更改。

## 创建存储容器，上传文件，并限制对文件的访问。 

1. 为公司数据创建专用存储容器。 

    - 在“存储帐户”的“数据存储”**** 部分中，选择“容器”**** 边栏选项卡。 
    - 选择“+ 容器”。 
    - 确保容器“名称”**** 为 `private`。
    - 确保“公共访问级别”为“专用(非匿名访问)”********。
    - 如果有时间，查看“高级”**** 设置，但采用默认值。 
    - 选择**创建**。 

1.  要进行测试，上传一个文件到“专用”**** 容器。 文件类型无关紧要。 小型图像或文本文件是不错的选择。 测试以确保文件不可公开访问。 

    - 选择  容器。
    - 选择**上载**。
    - 浏览到文件**** 并选择文件。
    - 上传**** 文件。
    - 选择上传的文件。
    - 在“概述”选项卡上，复制 URL********。
    - 将 URL**** 粘贴到新的浏览器标签页中。 
    - 验证出现的结果：文件未显示，并收到错误。 

1. 外部合作伙伴要求至少在接下来的 24 小时内读取和写入文件。 配置和测试共享访问签名 (SAS)。 详细了解[共享访问签名](https://learn.microsoft.com/azure/storage/common/storage-sas-overview)。

    - 选择上传的 Blob 文件，并转到 “生成 SAS”选项卡****。 
    - 在“权限”**** 下拉列表中，确保合作伙伴仅有“读取”**** 权限。
    - 验证“开始和到期日期/时间 ”是否为接下来的 24 小时****。 
    - 选择“ **生成 SAS 令牌和 URL**”。
    - 将 Blob SAS URL**** 复制到新的浏览器标签页。
    - 验证是否可访问该文件。 如果上传的是图像文件，它将在浏览器中显示。 如果是其他类型的文件，则会下载它们。

## 配置存储访问层和内容复制。

1. 为节省成本，请在 30 天后将 Blob 从热层移动到冷层。 详细了解如何管理 [Azure Blob 存储生命周期](https://learn.microsoft.com/azure/storage/blobs/lifecycle-management-policy-configure?tabs=azure-portal)。

    - 返回到“存储帐户”****。
    - 在“概述”**** 部分中，请注意，“默认访问层”**** 已设置为“热”****。 
    - 在“数据管理”**** 部分中，选择“生命周期管理”**** 边栏选项卡。
    - 选择“添加规则”。 
    - 将“规则名称”**** 设置为 `movetocool`。
    - 将“规则范围”设置为“将规则应用于存储帐户中的所有 Blob”********。
    - 选择**下一步**。
    - 确保已选择“上次修改时间”****。
    - 将“是在(天前)”设置为 30********。
    - 在“预期结果”下拉列表中，选择“移动到冷存储层”********。
    - 如果有时间，请查看下拉列表中的其他生命周期选项。 
    - 添加规则****。
  
1. 公共网站文件需要备份到另一个存储帐户。详细了解[对象复制](https://learn.microsoft.com/azure/storage/blobs/object-replication-configure?tabs=portal)。

    - 在存储帐户中，新建**** 名为 `backup` 的容器。 使用默认值。 如果需要详细说明，请参阅实验室 02a。 
    - 导航到“publicwebsite”**** 存储帐户。 此存储帐户是在上一练习中创建的。 
        - 在“数据管理”**** 部分中，选择“对象复制”**** 边栏选项卡。 
        - 选择“创建复制规则”****。
        - 将“目标存储帐户”**** 设置为“专用”**** 存储帐户。
        - 将“源容器”设置为“公共”，并将“目标”容器设置为“备份”****************。
        - 创建复制规则****。 
    - （可选）如果有时间，将文件上传到“公共”**** 容器。 返回到“专用”**** 存储帐户，并刷新“备份”**** 容器。 几分钟后，公共网站文件将显示在备份文件夹中。 

>**备注**：如需进行额外练习，请完成[配置 Azure Blob 存储](https://learn.microsoft.com/training/modules/configure-blob-storage/)模块。 该模块具有交互式实验室模拟，可在其中进行更多创建 Blob 存储的练习。 
