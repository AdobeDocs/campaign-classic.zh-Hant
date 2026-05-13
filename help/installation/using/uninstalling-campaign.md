---
product: campaign
title: 解除安裝Campaign
description: 瞭解如何解除安裝Campaign
feature: Installation
audience: installation
content-type: reference
hide: true
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
TQID: https://experienceleague.adobe.com/Dm4S9swh30hagUhayZHmaOS3Cjh1U-sWiG7crbI3Ciw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 36
ht-degree: 13%

---

# 解除安裝Campaign{#uninstalling-campaign}



>[!CAUTION]
>
>這些程式將會永久解除安裝Adobe Campaign。 所有資料都將遺失。

**RHEL：**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian：**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows：**

請參見此[頁面](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version)。 別忘了移除Campaign安裝資料夾。
