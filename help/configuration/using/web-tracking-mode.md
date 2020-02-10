---
title: 網路追蹤模式
seo-title: 網路追蹤模式
description: 網路追蹤模式
seo-description: null
page-status-flag: never-activated
uuid: 51b889d3-28f8-480a-a614-10c8eb3128ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: efeef54b-925d-4654-8601-52a73539b41f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# 網路追蹤模式{#web-tracking-mode}

Adobe Campaign可讓您選擇網頁追蹤模式，以定義追蹤記錄在應用程式中的處理方式。

有三種可用的Web追蹤模式：「 **作業追蹤」**、**「永久追蹤」** 和「 **匿名追蹤」**。

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

每種模式都具有特定特性。 「永久」網頁追蹤模式包含「作業」網頁追蹤模式的特性，而「匿名」模式則包含「永久」和「作業」模式的特性。

>[!CAUTION]
>
>如果已啟用「Leads」套件，預設會啟用「匿名」網頁追蹤模式。 在所有其他情況下，預設會啟用「作業階段」網頁追蹤模式。
>
>您可以隨時在執行個體部署精靈中變更預設模式。

請注意，如果您使用 **永久Web** 或 **** 匿名追蹤模式，您必須在追蹤表格(trackingLogXXX)中的&quot;sourceID&quot;欄(uuid230)中新增索引：

1. 識別永久追蹤相關的追蹤表。
1. 通過添加以下行來擴展與這些表匹配的方案：

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**永久** 和匿 **名Web追蹤模式** ，包括兩個選項：強 **制傳送** , **最後傳送**。

「強 **制傳送** 」選項可讓您在追蹤期間指定傳送(@jobid)的識別碼。

「上 **次傳送** 」選項可讓您將目前的追蹤記錄連結至上次追蹤的傳送。

**工作階段Web追蹤的特性：**

此模式會為具有工作階段Cookie的使用者建立追蹤記錄。 這些人點選了Adobe Campaign所傳送電子郵件中的URL，因此可讓我們追蹤下列資訊：

* 傳送ID
* 連絡人ID
* 傳送記錄
* 永久Cookie(uuid230)
* 追蹤URL
* 追蹤記錄的日期

使用此網頁追蹤模式時，如果遺失部分資訊，應用程式中將不會建立追蹤記錄。

此模式在容量（trackingLog表中記錄的有限數目）和計算（無調節）方面非常經濟。

**永久Web追蹤模式的特性：**

此網頁追蹤模式可讓您根據永久uuid230 cookie的存在來建立追蹤記錄。 如果訪客關閉其工作階段，Adobe Campaign會使用永久Cookie，從先前的追蹤記錄中復原其相關資訊。 如果目前作業的uuid230與uuid230的值已儲存在追蹤表格中，Adobe Campaign會重新插入追蹤記錄檔。

這表示訪客必須先前在Adobe Campaign中識別（透過傳送），才能啟用uuid230值的協調。

依預設，在「trackingLog」表格中會執行先前追蹤記錄檔中的搜尋。 如果Leads套件已啟用，在搜尋「trackingLog」表格之前，Adobe Campaign會搜尋「incomingLead」表格以取得先前的追蹤記錄。

在日誌協調期間，此模式的計算成本很高。

**匿名Web追蹤模式的特性：**

此網頁追蹤模式可讓您擷取連結至Adobe Campaign中匿名瀏覽的追蹤記錄。 系統會針對每次點按追蹤的URL自動建立追蹤記錄。 此日誌只具有uuid230的值。 在行銷促銷活動期間，會自動建立追蹤記錄檔，並包含所有識別資訊（請參閱作業追蹤）。 Adobe Campaign會自動搜尋先前記錄檔中的「uuid230」值，該值等於此行銷促銷活動追蹤記錄檔中的值。 如果找到相同的值，則會輸入所有先前的追蹤記錄檔，並包含行銷促銷活動追蹤記錄檔的所有資訊。

在計算和容量方面，此模式成本最高。

>[!NOTE]
>
>如果安 **[!UICONTROL Leads]** 裝了包，則您需要對活動表執行相同操作(**crm:incomingLead**)

下列結構概述了所有三種Web追蹤模式的功能：

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**基於上次傳送的永久網頁追蹤範例：**

佛羅倫薩收到遞送、開啟電子郵件、點擊連結、在零售網站上瀏覽，但不進行任何購買。 第二天，佛羅倫薩回到零售網站，瀏覽並購買。 由於啟用永久網路追蹤（上次傳送），因此她第二次造訪的所有記錄檔都會連結至前一天傳送給她的傳送。
