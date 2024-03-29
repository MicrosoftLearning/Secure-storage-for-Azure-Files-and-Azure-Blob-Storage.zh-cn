---
demo:
  title: 演示 02：创建和配置 Blob 存储
  module: Guided Project - Azure Files and Azure Blobs
---


## 演示 - 创建和配置 Blob 存储。

在本演示中，你将探索 Blob 存储。

## 查看 Blob 存储设置

1. [支持幻灯片] 在开始演示之前，请查看 Blob 存储的用途和组织。 我们的那些业务组将需要用到 Blob 存储？

1. 访问 **Azure 门户**。

1. 可以继续使用之前的存储帐户。 

1. 选择**概览**选项卡。

1. [支持幻灯片] 在“Blob 服务”**** 部分中，突出显示“默认访问层”**** 设置。 说明企业内容可以如何放置在热访问层中。 审核信息可以位于冷层中。 日志或季节性营销资料可以位于存档层中。 详细了解[Blob 存储的访问层](https://docs.microsoft.com/azure/storage/blobs/access-tiers-overview)。

1. [支持幻灯片] 在“Blob 服务”**** 部分中，突出显示“软删除”**** 设置。 这对公共网站很重要，可防止意外删除或覆盖某些内容。 学生将在实验室中练习软删除。 详细了解 [Blob 软删除](https://learn.microsoft.com/azure/storage/blobs/soft-delete-blob-overview)。

1. 在“Blob 服务”**** 部分中，指出“版本控制”**** 设置。 这可能对营销部门很重要。 可能需要跟踪产品资料。

## 创建 Blob 容器、上传文件并配置访问权限。

1. 在存储帐户中，找到“数据存储”**** 边栏选项卡。

1. 选择“容器”****，然后选择“+ 容器”****。

1. 为新容器提供名称****。
2. “公共”****。 这是公共网站的存储。

1. 将访问级别设置为“容器(对容器和 Blob 进行匿名读取访问)”****。 简要描述访问级别。 上一演示中详细介绍了这一点。 

1. 选择**创建**。

1. 等待容器部署完毕，然后继续在“公共”**** 容器中工作。

1. 上传 Blob****。 如果有时间，讨论这些选项。 

1. 选择“上传的文件”**** 并复制 URL****。

1. 打开新的浏览器标签页****，粘贴 URL 并确保上传的文件显示出来。

1. 返回到“公共”**** 容器，并将“访问级别”**** 更改为“专用(无匿名访问)”****。

1. 刷新 URL 选项卡**** 并确认对资源的访问权限现在设置为“拒绝”****。

## 配置生命周期管理。

1. [支持幻灯片] 首先讨论生命周期管理。 营销组的产品资料是季节性的。 例如，冬季服装和配饰系列。 此内容可以存档到下一季。 使用生命周期管理规则可以轻松完成内容存档。 详细了解 [Blob 生命周期管理策略](https://learn.microsoft.com/azure/storage/blobs/lifecycle-management-overview)。

1. 继续在存储帐户中工作。

1. 在“数据管理”**** 边栏选项卡中，选择“生命周期管理”****。

1. 在“详细信息”**** 选项卡上，将规则命名为“movetoarchive”****。

1. 讨论规则范围**** 以及如何使用筛选器限制 Blob****。 例如，仅移动特定容器中的内容。

1. 移动到“基本 Blob”**** 选项卡。

1. 讨论规则将如何根据数天前修改或创建的 Blob 自动移动 Blob。

1. 打开“然后”**** 下拉菜单并讨论这些选项。 尝试根据实验室方案提供示例。 例如，IT 部门可能需要在 30 天后删除 Blob，因为它是测试帐户。

## 配置对内容的有限访问权限。

1. 查看有限访问的用例。 例如，企业内容需要共享给第三方供应商或合作伙伴。 访问权限可能仅限于特定的时间范围和操作（读取、写入）。 详细了解[共享访问签名](https://learn.microsoft.com/azure/storage/common/storage-sas-overview)。

1. 继续使用存储帐户****。

1. 在“安全 + 网络”**** 边栏选项卡中，选择“共享访问签名”****。

1. 查看“允许的服务”**** 和“允许的资源类型”****。 说明 SAS 的范围可以限定为存储帐户、容器、文件或单个 Blob 文件。

1. 查看“允许的权限”****。

1. 选择“Blob 和容器”**** 和“读取”****。

1. 查看“开始”**** 和“到期日期/时间”**** 设置。

1. 选择“生成 SAS 和连接字符串”。

1. **保存**所做更改。 

1. 将“Blob 服务 SAS URL”**** 复制到新的浏览器标签页。

1. 讨论内容的显示方式，即使这是专用容器。

## 配置 Blob 对象复制。 

1. [支持幻灯片] 在继续演示之前，请查看 Blob 对象复制的用例。 例如，需要备份公共网站内容。 说明存储帐户可能位于不同的 Azure 区域，但这不是必需的。 详细了解[对象复制](https://learn.microsoft.com/azure/storage/blobs/object-replication-overview)。

1. 新**** 建存储帐户。

1. 在存储帐户中创建**** 一个名为“备份”**** 的容器****。

1. 返回到第一个存储帐户和“公共”**** 容器。 

1. 在“数据管理”**** 边栏选项卡中，选择“对象复制”****。

1. 选择“创建复制规则”****。

    - 目标存储帐户：第二个存储帐户

    - 源容器：公共****

    - 目标容器：备份****

1. 创建**** 规则。 说明复制源容器可能需要 5-10 分钟。 说明学生在完成实验室期间需要花点时间来执行此操作。 

> **备注：** 学生现在应能够完成 LAB_02a 和 LAB_02b。 

  
