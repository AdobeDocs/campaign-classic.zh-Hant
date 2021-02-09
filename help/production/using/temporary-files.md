---
solution: Campaign Classic
product: campaign
title: 臨時檔案
description: 臨時檔案
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---


# 臨時檔案{#temporary-files}

當系統投入生產時，可能會顯示以下錯誤訊息（尤其是在傳送記錄檔中）:

*無法將檔案&#39;/tmp/tmp0000.tmp&#39;更名為/usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;（errno=18，無效的跨設備連結）(iRc=-52)*

原因如下：

Adobe Campaign會在&#x200B;**/tmp**&#x200B;下產生暫存檔案，然後重新命名檔案，將檔案移至&#x200B;**/usr/local/neolane/nl6/var**。 當兩個資料夾（**/tmp**&#x200B;和&#x200B;**/usr/local/neolane/nl6/var**）對應於不同設備時，就會發生此錯誤。 ******df**&#x200B;命令用於驗證。

要解決此問題，必須在與目標相同的設備中生成臨時檔案。

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
