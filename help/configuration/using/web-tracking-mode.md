---
product: campaign
title: 網路追蹤模式
description: 了解如何選取網頁追蹤模式
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 1%

---

# 網路追蹤模式{#web-tracking-mode}



Adobe Campaign可讓您選取網頁追蹤模式，定義應用程式中追蹤記錄的處理方式。

有三種可用的網頁追蹤模式： **&quot;工作階段追蹤&quot;**,**&quot;永久追蹤&quot;** 和 **&quot;匿名追蹤&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

每個模式都有特定特性。 「永久」網路追蹤模式包括「工作階段」網路追蹤模式的特性，而「匿名」模式包括「永久」和「工作階段」模式的特性。

>[!IMPORTANT]
>
>如果啟用「Leads」包，預設會啟用「匿名」Web跟蹤模式。 在所有其他情況下，預設會啟用「工作階段」網頁追蹤模式。
>
>您隨時都可以在執行個體部署精靈中變更預設模式。

請注意，如果您使用 **永久性網站** 或 **匿名** 追蹤模式時，您必須在追蹤表格(trackingLogXXX)中，將索引新增至「sourceID」欄(uuid230):

1. 識別永久追蹤所關注的追蹤表格。
1. 通過添加以下行來擴展與這些表匹配的架構：

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**永久** 和 **匿名** 網頁追蹤模式包含兩個選項： **強制傳送** 和 **上次傳送**.

此 **強制傳送** 選項可讓您在追蹤期間指定傳送的識別碼(@jobid)。

此 **上次傳送** 選項可讓您將目前的追蹤記錄連結至上次追蹤的傳送。

**工作階段網路追蹤的特性：**

此模式會為具有工作階段Cookie的使用者建立追蹤記錄。 這些是點按了Adobe Campaign所傳送電子郵件中URL的人，因此可讓我們追蹤下列資訊：

* 傳遞 ID
* 連絡人ID
* 傳遞記錄
* 永久cookie(uuid230)
* 追蹤URL
* 追蹤記錄的日期

使用此Web追蹤模式時，如果缺少部分資訊，應用程式中將不會建立任何追蹤記錄。

此模式在容量（trackingLog表中記錄數量有限）和計算（無調解）方面是經濟的。

**永久性網頁追蹤模式的特色：**

此網頁追蹤模式可讓您根據永久uuid230 Cookie的存在來建立追蹤記錄。 如果訪客關閉其工作階段，Adobe Campaign會使用永久Cookie，從先前的追蹤記錄中復原其相關資訊。 如果目前工作階段的uuid230與已儲存在追蹤表格中的uuid230具有相同值，Adobe Campaign會重新插入追蹤記錄。

這表示訪客必須先前在Adobe Campaign中識別（透過傳送），才能啟用uuid230值的調解。

依預設，先前追蹤記錄中的搜尋會在「trackingLog」表格中執行。 如果Leads包已啟用，則在搜索「trackingLog」表之前，Adobe Campaign將搜索「incomingLead」表以查找以前的跟蹤日誌記錄。

在日誌調解期間，此模式的計算成本很高。

**匿名Web追蹤模式的特性：**

此網頁追蹤模式可讓您擷取連結至Adobe Campaign中匿名瀏覽的追蹤記錄。 系統會自動為追蹤的URL上的每次點按建立追蹤記錄。 此記錄只有uuid230的值。 在行銷活動期間，會使用所有識別資訊自動建立追蹤記錄（請參閱工作階段追蹤）。 Adobe Campaign會自動搜尋先前記錄中「uuid230」值，該值等於此行銷活動追蹤記錄中的值。 如果找到相同的值，則會輸入所有先前的追蹤記錄，以及行銷活動追蹤記錄中的所有資訊。

這種模式在計算和容量方面成本最高。

>[!NOTE]
>
>若 **[!UICONTROL Leads]** 套件已安裝，您需要對活動表格執行相同操作(**crm:incomingLead**)

以下結構概述所有三種網頁追蹤模式的功能：

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**根據上次傳送的永久性網頁追蹤範例：**

佛羅倫薩會收到傳遞、開啟電子郵件、點擊連結、在零售網站上瀏覽，但不會進行任何購買。 第二天，佛羅倫薩回到零售網站，瀏覽並購買。 由於已啟用永久性網頁追蹤（上次傳送），其第二次造訪的所有記錄都會連結至前一天傳送給她的傳送。
