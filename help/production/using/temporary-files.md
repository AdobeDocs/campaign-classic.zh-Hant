---
product: campaign
title: 臨時檔案
description: 臨時檔案
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# 臨時檔案{#temporary-files}



在系統投入生產時，可能會顯示以下錯誤消息（尤其是在傳遞日誌中）:

*無法將檔案「/tmp/tmp0000.tmp」更名為/usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ；（errno=18，無效的跨設備連結）(iRc=-52)*

原因如下：

Adobe Campaign生成臨時檔案 **/tmp**&#x200B;然後更名他們 **/usr/local/neolane/nl6/var**。 當兩個資料夾(**/tmp** 和 **/usr/local/neolane/nl6/var**&#x200B;實際上，它是 **/var/nl6**)對應不同的設備。 的 **東風** 命令用於驗證。

要糾正此問題，臨時檔案必須與目標位於同一設備中。

例如，執行以下操作：

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

然後添加：

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
