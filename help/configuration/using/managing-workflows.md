---
title: 管理工作流程
seo-title: 管理工作流程
description: 管理工作流程
seo-description: null
page-status-flag: never-activated
uuid: 8b6320c0-1aae-4acd-a698-03f9bebd916d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ee724240-c337-489d-a21b-5f3aec1f247a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 管理工作流程{#managing-workflows}

根據預設，您的新工作流程是以預先設定的工作流程範本為基礎，並以收件者表(nms:recipient)為基礎。 要根據 **Nms_DefaultRcpSchema選項中引用的收件人的自定義表自動使用這些檔案(請參** 閱配置介面部分 [](../../configuration/using/configuring-the-interface.md) )，必須建立新的工作流模板。

通過節點建立新模 **[!UICONTROL Resources > Templates > Workflow templates]** 板。 在範本的屬性中，提供的維度與您的外部收件者表格相符。

將新工作流程建立在最近建立的範本上，您的個人化表格將依預設會針對工作流程的全域定位和篩選維度選取。

因此，您工作流程中使用的所有活動都將使用您的自訂表格，而不需額外的手動設定。

如需此工作流程的詳細資訊，請參閱[本小節](../../workflow/using/about-workflows.md)。

![](assets/cfg_external_table_workflow.png)

