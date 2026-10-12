---
product: campaign
title: 建立測試環境
description: 建立測試環境
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 49ac279b-bc67-4311-b0a4-0e23f2a99c52
TQID: 'https://experienceleague.adobe.com/-V-tBgJnQ-1-W7MfUEqXQ5Zzd8GN32XT-9dWVsRa6FI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
    internal-label: Offer Management
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
source-git-commit: 323ff901668895588a6e9587fa2a8b7804cf2fb4
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%
---
# 建立測試環境{#creating-a-test-environment}



若要建立測試環境（沙箱模式），請套用下列步驟：

>[!IMPORTANT]
>
>僅將此環境建立方法用於測試環境。 在所有其他情況下，請使用目標對應助理。 如需詳細資訊，請參閱[建立優惠方案環境](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/offers/interaction-settings/interaction-env#create-an-offer-environment){target="_blank"} （Campaign v8檔案）。

1. 啟動Adobe Campaign Explorer並前往執行個體根目錄。
1. 按一下滑鼠右鍵，然後使用下拉式功能表新增&#x200B;**[!UICONTROL Generic folder]**。

   ![](assets/offer_env_creation_001.png)

1. 接著，移至您剛建立的資料夾，並使用右鍵功能表新增&#x200B;**[!UICONTROL Offer environment]**。

   ![](assets/offer_env_creation_001bis.png)

1. 套用相同的程式來建立環境子資料夾和元素。
1. 測試完成後，如果您希望在生產環境中使用環境，請在設計環境中複製選件和空間。 （按一下滑鼠右鍵>「**[!UICONTROL Actions]**」>「**[!UICONTROL Deploy]**」）。

   ![](assets/migration_interaction_5.png)
