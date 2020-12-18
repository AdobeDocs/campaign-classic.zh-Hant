---
solution: Campaign Classic
product: campaign
title: 疑難排解
description: 疑難排解
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---


# 疑難排解{#troubleshooting}

萬一發生錯誤，請確定下列元素已正確設定：

* **外部帳戶**

   在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中，請確定下列外部SFTP帳戶已正確設定。 您的顧問應已在Adobe Experience Cloud中設定上述SFTP伺服器。

   * **[!UICONTROL importSharedAudience]** :專用於匯入觀眾的SFTP帳戶。
   * **[!UICONTROL exportSharedAudience]** :專用於匯出觀眾的SFTP帳戶。

* **AMC資料來源**

   在&#x200B;**[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;中，檢查AMC資料源是否已正確設定。

透過「人員」核心服務共用觀眾或匯入觀眾時，可能會發生遺失部分資料的情況。 只會傳送ID（「訪客ID」或「Declared ID」）與描述檔維度可協調的記錄。 不會匯入Adobe Campaign未識別之「人員」核心服務區段的ID。
