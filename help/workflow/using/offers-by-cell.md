---
product: campaign
title: 依儲存格列出的產品建議
description: 依儲存格列出的產品建議
feature: Workflows, Targeting Activity, Interaction
hide: true
exl-id: 72b17b48-093a-4eb9-a848-3c1570e49b61
TQID: 'https://experienceleague.adobe.com/ddCHWdqnyWjUtP3lcc3yIaUHffGkNCbnVKWiJVfhdjg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ff84ab2f-a7c2-4ced-a3c8-5113f4348d99
    internal-label: Targeting Activity
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 7%
---
# 依儲存格列出的產品建議{#offers-by-cell}



**[!UICONTROL Offers by cell]**&#x200B;活動可讓您將入站母體（例如從查詢）分配至數個區段，並指定要針對每個區段呈現的選件。

此活動只能與&#x200B;**互動**&#x200B;搭配使用。 如需詳細資訊，請參閱此[區段](../../interaction/using/about-outbound-channels.md)。

操作步驟：

1. 在指定目標母體後，新增&#x200B;**[!UICONTROL Offers by cell]**&#x200B;活動，然後開啟它。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;索引標籤中，選取您要顯示優惠方案的優惠方案空間。
1. 在&#x200B;**[!UICONTROL Cells]**&#x200B;索引標籤中，使用&#x200B;**[!UICONTROL Add]**&#x200B;按鈕指定不同的子集：

   * 使用可用的篩選和限制規則指定子集母體。
   * 接著，選取您要呈現給子集的選件。 可用的優惠方案是在上一步驟中選取的優惠方案空間上符合資格的優惠方案。

     ![](assets/int_offer_per_cell1.png)

1. 然後，設定與您所選管道對應的傳送活動。 請參閱[跨通道傳遞](cross-channel-deliveries.md)。
