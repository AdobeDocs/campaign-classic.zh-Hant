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



依預設，您的新工作流程會以預先設定的工作流程範本為基礎，並以收件者表格(nms：recipient)為基礎。 以便根據中參照的自訂收件者表格自動建立收件者 **Nms_DefaultRcpSchema** 選項(請參閱 [設定介面](../../configuration/using/configuring-the-interface.md) 區段)，您必須建立新的工作流程範本。

透過建立新範本 **[!UICONTROL Resources > Templates > Workflow templates]** 節點。 在範本的屬性中，提供的維度符合外部收件者表格。

透過將您的新工作流程建立在最近建立的範本上，系統會根據工作流程的全域目標定位和篩選維度，預設選取您的個人化表格。

因此，工作流程中使用的所有活動將使用您的自訂表格，而無需任何其他手動設定。

如需此工作流程的詳細資訊，請參閱[本小節](../../workflow/using/about-workflows.md)。

![](assets/cfg_external_table_workflow.png)
