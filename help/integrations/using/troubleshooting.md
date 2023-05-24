---
product: campaign
title: 疑難排解
description: 疑難排解
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---

# 疑難排解{#troubleshooting}



如果發生錯誤，請確認下列元素已正確設定：

* **外部帳戶**

   在 **[!UICONTROL Administration > Platform > External accounts]**，確定已正確設定下列外部SFTP帳戶。 您的顧問應已在Adobe Experience Cloud中設定提及的SFTP伺服器。

   * **[!UICONTROL importSharedAudience]** ：專用於匯入對象的SFTP帳戶。
   * **[!UICONTROL exportSharedAudience]** ：專用於匯出受眾的SFTP帳戶。

* **AMC資料來源**

   在 **[!UICONTROL Administration > Platform > AMC Data sources]**，檢查AMC資料來源是否設定正確。

透過「人員」核心服務共用對象或匯入對象時，可能會遺失部分資料。 只有其ID （「訪客ID」或「宣告ID」）能夠與設定檔維度調解的記錄才會轉移。 Adobe Campaign無法辨識的People核心服務區段ID不會匯入。
