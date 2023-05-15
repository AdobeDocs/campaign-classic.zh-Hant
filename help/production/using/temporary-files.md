---
product: campaign
title: 臨時檔案
description: 臨時檔案
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# 臨時檔案{#temporary-files}



當系統投入生產時，可能會顯示下列錯誤訊息（尤其是在傳送記錄中）:

*無法將檔案&#39;/tmp/tmp0000.tmp&#39;更名為/usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ；（errno=18，無效的跨裝置連結）(iRc=-52)*

原因如下：

Adobe Campaign會在 **/tmp**，然後重新命名，將其移至 **/usr/local/neolane/nl6/var**. 當兩個資料夾(**/tmp** 和 **/usr/local/neolane/nl6/var**，實際上是 **/var/nl6**)對應至不同裝置。 此 **df** 命令用於驗證。

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
