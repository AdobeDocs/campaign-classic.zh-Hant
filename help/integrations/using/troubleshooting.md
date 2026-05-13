---
product: campaign
title: 疑難排解
description: 疑難排解
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
TQID: https://experienceleague.adobe.com/4de9cxyepP-REa2OTWniBFWInphApeUM79sZuFGcynI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875f
  - id: a8512b64-d668-4084-b4f0-34baa899e306
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 136
ht-degree: 3%

---

# 疑難排解{#troubleshooting}



如果發生錯誤，請確認下列元素已正確設定：

* **外部帳戶**

  在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中，確定已正確設定下列外部SFTP帳戶。 您的顧問應已在Adobe Experience Cloud中設定提及的SFTP伺服器。

   * **[!UICONTROL importSharedAudience]** ：專用於匯入對象的SFTP帳戶。
   * **[!UICONTROL exportSharedAudience]** ：專用於匯出對象的SFTP帳戶。

* **AMC資料來源**

  在&#x200B;**[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;中，檢查AMC資料來源是否已正確設定。

透過Experience Cloud Audience共用對象或匯入對象時，可能會遺失部分資料。 只有其ID （「訪客ID」或「宣告ID」）能夠與設定檔維度調解的記錄才會轉移。 Adobe Campaign無法辨識的區段中的ID不會匯入。
