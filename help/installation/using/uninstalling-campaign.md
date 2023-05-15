---
product: campaign
title: 解除安裝 Campaign
description: 了解如何解除安裝Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 19%

---

# 解除安裝 Campaign{#uninstalling-campaign}



>[!CAUTION]
>
>這些程式會永久解除安裝Adobe Campaign。 所有資料都將丟失。

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows：**

請參閱 [頁面](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). 別忘了移除Campaign安裝資料夾。
