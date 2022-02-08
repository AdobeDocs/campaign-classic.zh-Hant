---
product: campaign
title: 網路追蹤模式
description: 瞭解如何選擇Web跟蹤模式
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---

# 網路追蹤模式{#web-tracking-mode}

![](../../assets/v7-only.svg)

Adobe Campaign允許您選擇Web跟蹤模式，該模式定義了跟蹤日誌在應用程式中的處理方式。

有三種可用的Web跟蹤模式： **&quot;會話跟蹤&quot;**。**&quot;永久跟蹤&quot;** 和 **&quot;匿名跟蹤&quot;**。

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

每種模式都有特定的特徵。 「永久」網路跟蹤模式包括「會話」網路跟蹤模式的特徵，而「匿名」模式包括「永久」和「會話」模式的特徵。

>[!IMPORTANT]
>
>如果啟用了「Leads」包，則預設啟用「匿名」Web跟蹤模式。 在所有其他情況下，預設情況下會啟用「會話」 Web跟蹤模式。
>
>可以隨時在實例部署嚮導中更改預設模式。

請注意，如果您使用 **永久網** 或 **匿名** 跟蹤模式，必須在跟蹤表(trackingLogXXX)中的「sourceID」列(uuid230)中添加索引：

1. 確定與永久跟蹤相關的跟蹤表。
1. 通過添加以下行來擴展與這些表匹配的方案：

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**永久** 和 **匿名** Web跟蹤模式包括兩個選項： **強制交付** 和 **上次交貨**。

的 **強制交付** 選項可在跟蹤期間指定交貨(@jobid)的標識符。

的 **上次交貨** 選項，您可以將當前跟蹤日誌連結到上次跟蹤的傳遞。

**會話Web跟蹤的特點：**

此模式為具有會話cookie的人員建立跟蹤日誌。 這些人點擊了Adobe Campaign發送的電子郵件中的URL，從而使我們能夠跟蹤以下資訊：

* 交貨ID
* 聯繫人ID
* 交貨日誌
* 永久cookie(uuid230)
* 跟蹤URL
* 跟蹤日誌的日期

使用此Web跟蹤模式時，如果缺少部分資訊，則不會在應用程式中建立跟蹤日誌。

此模式在體積（trackingLog表中記錄的有限數量）和計算（無協調）方面是經濟的。

**永久Web跟蹤模式的特點：**

此Web跟蹤模式允許您基於永久uid230 cookie的存在建立跟蹤日誌。 如果訪問者結束會話，Adobe Campaign會使用永久cookie從以前的跟蹤日誌中恢復有關他們的資訊。 Adobe Campaign如果當前會話的uuid230具有與跟蹤表中已儲存的uuid230相同的值，則重新插入跟蹤日誌。

這意味著訪問者需要先前在Adobe Campaign（通過傳遞）中識別，以啟用uuid230值的協調。

預設情況下，在「trackingLog」表中執行以前跟蹤日誌中的搜索。 如果啟用了Leads包，在搜索&quot;trackingLog&quot;表之前，Adobe Campaign將搜索&quot;incomingLead&quot;表以查找以前的跟蹤日誌記錄。

在日誌協調期間，此模式的計算成本很高。

**匿名Web跟蹤模式的特點：**

此Web跟蹤模式允許您檢索連結到Adobe Campaign匿名瀏覽的跟蹤日誌。 自動為每次按一下跟蹤的URL建立跟蹤日誌。 此日誌僅具有uuid230的值。 在市場營銷活動期間，系統會自動建立跟蹤日誌，其中包含所有標識資訊（請參閱會話跟蹤）。 Adobe Campaign將自動搜索以前的日誌，以查找與此市場營銷活動跟蹤日誌中的值相等的「uuid230」值。 如果找到相同的值，則輸入所有以前的跟蹤日誌以及來自市場營銷市場活動跟蹤日誌的所有資訊。

這種模式在計算量和體積上都是成本最高的。

>[!NOTE]
>
>如果 **[!UICONTROL Leads]** 包已安裝，您需要對活動表執行同樣操作(**crm：傳入線索**)

以下模式概括了所有三種Web跟蹤模式的功能：

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**基於上次傳遞的永久Web跟蹤示例：**

佛羅倫薩收到遞送，開啟電子郵件，按一下連結，瀏覽零售網站，但不進行任何購買。 第二天，佛羅倫薩回到零售網站，瀏覽並購買。 由於啟用了永久的Web跟蹤（上次傳送），因此她第二次訪問的所有日誌都將連結到前一天發送給她的傳送。
