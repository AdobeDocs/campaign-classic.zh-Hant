---
product: campaign
title: 臨時檔案
description: 臨時檔案
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 4%

---

# 臨時檔案{#temporary-files}



系統投入生產時，可能會顯示如下錯誤訊息（特別是在傳送記錄中）：

*無法將檔案&#39;/tmp/tmp0000.tmp&#39;重新命名為/usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ；（errno=18，無效的跨裝置連結） (iRc=-52)*

原因如下：

Adobe Campaign會在&#x200B;**/tmp**&#x200B;下產生暫存檔，然後重新命名以將它們移至&#x200B;**/usr/local/neolane/nl6/var**。 當兩個資料夾（**/tmp**&#x200B;和&#x200B;**/usr/local/neolane/nl6/var**，實際上是&#x200B;**/var/nl6**&#x200B;的符號連結）對應到不同的裝置時，就會發生此錯誤。 **df**&#x200B;命令用於驗證。

若要修正此問題，必須在與目的地相同的裝置上產生暫存檔案。

例如，執行下列動作：

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

然後新增：

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
