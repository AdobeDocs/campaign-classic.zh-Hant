---
product: campaign
title: 疑難排解
description: 疑難排解
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---

# 疑難排解{#troubleshooting}

發生錯誤時，請確定下列元素已正確設定：

* **外部帳戶**

   在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中，確認下列外部SFTP帳戶已正確設定。 上述SFTP伺服器應由您的顧問在Adobe Experience Cloud中設定。

   * **[!UICONTROL importSharedAudience]** :專用於匯入對象的SFTP帳戶。
   * **[!UICONTROL exportSharedAudience]** :專用於匯出受眾的SFTP帳戶。

* **AMC資料來源**

   在&#x200B;**[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;中，檢查AMC資料源是否設定正確。

透過「人物」核心服務共用受眾或匯入受眾時，可能會發生缺少某些資料的情況。 只有ID（「訪客ID」或「宣告ID」）能與設定檔維度調解的記錄能夠傳輸。 來自People核心服務區段且Adobe Campaign未辨識的ID不會匯入。
