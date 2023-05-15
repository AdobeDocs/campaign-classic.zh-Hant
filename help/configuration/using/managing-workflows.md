---
product: campaign
title: 管理工作流程
description: 管理工作流程
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 11%

---

# 管理工作流程{#managing-workflows}



依預設，您的新工作流程以預先設定的工作流程範本為基礎，並以收件者表格(nms:recipient)為基礎。 以便根據 **Nms_DefaultRcpSchema** 選項(請參閱 [配置介面](../../configuration/using/configuring-the-interface.md) 部分)，則必須建立新的工作流模板。

透過 **[!UICONTROL Resources > Templates > Workflow templates]** 節點。 在範本的屬性中，提供的維度會與外部收件者表格相符。

根據您最近建立的範本，您的新工作流程將依預設會為工作流程的全域鎖定目標和篩選維度選取個人化表格。

因此，工作流程中使用的所有活動都將使用您的自訂表格，而不需要任何額外的手動配置。

如需此工作流程的詳細資訊，請參閱[本小節](../../workflow/using/about-workflows.md)。

![](assets/cfg_external_table_workflow.png)
