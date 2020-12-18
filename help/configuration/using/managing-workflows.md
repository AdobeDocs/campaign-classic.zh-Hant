---
solution: Campaign Classic
product: campaign
title: 管理工作流程
description: 管理工作流程
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 11%

---


# 管理工作流程{#managing-workflows}

根據預設，您的新工作流程是以預先設定的工作流程範本為基礎，並以收件者表(nms:recipient)為基礎。 要根據&#x200B;**Nms_DefaultRcpSchema**&#x200B;選項中引用的收件者自動表（請參閱[配置介面](../../configuration/using/configuring-the-interface.md)部分），您必須建立新的工作流模板。

通過&#x200B;**[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;節點建立新模板。 在範本的屬性中，提供的維度與您的外部收件者表格相符。

將新工作流程建立在最近建立的範本上，您的個人化表格將依預設會針對工作流程的全域定位和篩選維度選取。

因此，您工作流程中使用的所有活動都將使用您的自訂表格，而不需額外的手動設定。

如需此工作流程的詳細資訊，請參閱[本小節](../../workflow/using/about-workflows.md)。

![](assets/cfg_external_table_workflow.png)

