---
title: 臨時檔案
seo-title: 臨時檔案
description: 臨時檔案
seo-description: null
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# 臨時檔案{#temporary-files}

如果系統投入生產時出現以下錯誤消息（尤其是在交付日誌中）:

**無法將檔案&#39;/tmp/tmp0000.tmp&#39;更名為/usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;（errno=18，無效的跨設備連結）(iRc=-52)**

原因如下：

Adobe Campaign會在 **/tmp下產生暫存檔**，然後重新命名檔案，將檔案移至 **/usr/local/neolane/nl6/var**。 當兩個資料夾(**/tmp** and **/usr/local/neolane/nl6/var**，實際上是到 ****/var/nl6的符號連結)對應到不同的設備時，就會發生此錯誤。 df **命令** ，用於驗證。

要解決此問題，必須在與目標相同的設備中生成臨時檔案。 例如，執行：

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

然後添加：

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

