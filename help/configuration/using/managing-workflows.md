---
product: campaign
title: 管理工作流程
description: 管理工作流程
feature: Workflows, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
TQID: 'https://experienceleague.adobe.com/dpHtLw4PYGg35t-ihmw9LGUSbjgeNloUhGXp9KPJaRU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 11%
---
# 管理工作流程{#managing-workflows}



依預設，您的新工作流程是以預先設定的工作流程範本為基礎，並以收件者表格(nms:recipient)為基礎。 若要讓收件者自動以&#x200B;**Nms_DefaultRcpSchema**&#x200B;選項中參考的收件者自訂表格為基礎（請參閱[設定介面](../../configuration/using/configuring-the-interface.md)區段），您必須建立新的工作流程範本。

透過&#x200B;**[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;節點建立新範本。 在範本的屬性中，提供的維度符合外部收件者表格。

透過將您的新工作流程建立在最近建立的範本上，依照預設，將會針對工作流程的全域目標定位和篩選維度選取您的個人化表格。

因此，工作流程中使用的所有活動都會使用自訂表格，不需要任何其他手動設定。

如需此工作流程的詳細資訊，請參閱[本小節](../../workflow/using/about-workflows.md)。

![](assets/cfg_external_table_workflow.png)
