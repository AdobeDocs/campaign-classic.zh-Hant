---
product: campaign
title: 定義最終傳遞
description: 瞭解如何透過專屬的使用案例執行A/B測試
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
TQID: https://experienceleague.adobe.com/P0oI4PhLZB-iBFDrEJ2Qy7eIOPYWSWYu5s6j3yCN6j0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 119
ht-degree: 5%

---

# AB測試：定義最終傳遞 {#step-6--defining-the-final-delivery}

建立指令碼以選取A/B測試獲勝者後，您可以定義最終傳送的引數。

1. 將&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動連線至其餘&#x200B;**[!UICONTROL Delivery]**&#x200B;活動。
1. 開啟&#x200B;**[!UICONTROL Delivery]**&#x200B;活動。
1. 取消核取&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;選項以完成此活動的工作流程。
1. 將其他選項保留為其預設值。

   ![](assets/ab_test_final_delivery.png)

透過準備轉變中指定的傳遞（透過&#x200B;**[!UICONTROL Javascript Code]**&#x200B;活動定義），您就可以核准它並開始傳送，如下一個步驟所述。

您現在可以開始工作流程。 [了解更多資訊](a-b-testing-uc-start-workflow.md)。
