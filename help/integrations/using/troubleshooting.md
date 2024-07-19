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
hidefromtoc: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '136'
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

透過「Experience Cloud對象」共用對象或匯入對象時，可能會遺失部分資料。 只有其ID （「訪客ID」或「宣告ID」）能夠與設定檔維度調解的記錄才會轉移。 Adobe Campaign無法辨識的區段中的ID不會匯入。
