---
title: 疑難排解
seo-title: 疑難排解
description: 疑難排解
seo-description: null
page-status-flag: never-activated
uuid: fb51ad18-221b-4058-b206-ca2ca045c507
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f3ff8c8e-22b0-4d61-9f26-11f5ca3bc0be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 疑難排解{#troubleshooting}

萬一發生錯誤，請確定下列元素已正確設定：

* **外部帳戶**

   在中 **[!UICONTROL Administration > Platform > External accounts]**，請確定下列外部SFTP帳戶已正確設定。 您的顧問應已在Adobe Experience cloud中設定上述SFTP伺服器。

   * **[!UICONTROL importSharedAudience]** :專用於匯入觀眾的SFTP帳戶。
   * **[!UICONTROL exportSharedAudience]** :專用於匯出觀眾的SFTP帳戶。

* **AMC資料來源**

   在中， **[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;檢查AMC資料源是否已正確設定。

透過「人員」核心服務共用觀眾或匯入觀眾時，可能會發生遺失部分資料的情況。 只會傳送ID（「訪客ID」或「Declared ID」）與描述檔維度可協調的記錄。 不會匯入Adobe Campaign未識別之「人員」核心服務區段的ID。
