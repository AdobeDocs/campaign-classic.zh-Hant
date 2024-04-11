---
product: campaign
title: 管理工作流程
description: 管理工作流程
feature: Workflows, Configuration
role: Data Engineer, Developer
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 10%

---

# 管理工作流程{#managing-workflows}



依預設，您的新工作流程以預先設定的工作流程範本為基礎，並以收件者表格(nms：recipient)為基礎。 以便這些收件者能自動根據中參照的自訂收件者表格 **Nms_DefaultRcpSchema** 選項(請參閱 [設定介面](../../configuration/using/configuring-the-interface.md) 區段)，您必須建立新的工作流程範本。

透過建立新範本 **[!UICONTROL Resources > Templates > Workflow templates]** 節點。 在範本的屬性中，提供的維度符合外部收件者表格。

透過將您的新工作流程建立在最近建立的範本上，依照預設，將會針對工作流程的全域目標定位和篩選維度選取您的個人化表格。

因此，工作流程中使用的所有活動都會使用自訂表格，不需要任何其他手動設定。

如需此工作流程的詳細資訊，請參閱[本小節](../../workflow/using/about-workflows.md)。

![](assets/cfg_external_table_workflow.png)
