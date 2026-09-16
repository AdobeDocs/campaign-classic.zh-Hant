---
product: campaign
title: 疑難排解
description: 疑難排解
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
TQID: https://experienceleague.adobe.com/4de9cxyepP-REa2OTWniBFWInphApeUM79sZuFGcynI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Adobe Analytics integration
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Adobe Experience Manager integration
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Adobe Experience Platform integration
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Adobe Target integration
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 3%
---
# 疑難排解{#troubleshooting}



如果發生錯誤，請確認下列元素已正確設定：

* **外部帳戶**

  在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中，確定已正確設定下列外部SFTP帳戶。 您的顧問應已在Adobe Experience Cloud中設定上述的SFTP伺服器。

  * **[!UICONTROL importSharedAudience]** ：專用於匯入對象的SFTP帳戶。
  * **[!UICONTROL exportSharedAudience]** ：專用於匯出對象的SFTP帳戶。

* **AMC資料來源**

  在&#x200B;**[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;中，檢查AMC資料來源是否已正確設定。

透過Experience Cloud Audience共用受眾或匯入受眾時，可能會遺失部分資料。 只有其ID （「訪客ID」或「宣告ID」）能夠與設定檔維度調解的記錄才會轉移。 Adobe Campaign無法辨識的區段中的ID不會匯入。
