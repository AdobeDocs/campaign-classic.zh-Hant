---
product: campaign
title: 網路追蹤模式
description: 瞭解如何選取網頁追蹤模式
feature: Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# 網路追蹤模式{#web-tracking-mode}



Adobe Campaign可讓您選取網路追蹤模式，以定義在應用程式中處理追蹤記錄的方式。

有三種可用的網頁追蹤模式： **「工作階段追蹤」**，**「永久追蹤」** 和 **&quot;匿名追蹤&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

每個模式都有特定特性。 「永久」網路追蹤模式包含「工作階段」網路追蹤模式的特性，而「匿名」模式包含「永久」和「工作階段」模式的特性。

>[!IMPORTANT]
>
>如果已啟用「銷售機會」套件，預設會啟用「匿名」網頁追蹤模式。 在所有其他情況下，「工作階段」網頁追蹤模式都會預設為啟用。
>
>您隨時都可以在執行個體部署精靈中變更預設模式。

請注意，如果您使用 **永久網頁** 或 **匿名** 在追蹤模式中，您必須在追蹤表格(trackingLogXXX)的「sourceID」欄(uuid230)中新增索引：

1. 識別永久追蹤所關注的追蹤表格。
1. 新增下列行來擴充符合這些表格的綱要：

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**永久** 和 **匿名** 網頁追蹤模式包含兩個選項： **強制傳遞** 和 **上次傳遞**.

此 **強制傳遞** 選項可讓您在追蹤期間指定傳遞(@jobid)的識別碼。

此 **上次傳遞** 選項可讓您將目前追蹤記錄檔連結至上次追蹤的傳遞。

**工作階段Web追蹤的特徵：**

此模式會為擁有工作階段Cookie的人員建立追蹤記錄。 這些人在Adobe Campaign傳送的電子郵件中按一下URL，因此可讓我們追蹤下列資訊：

* 傳遞 ID
* 聯絡人ID
* 傳遞記錄
* 永久cookie (uuid230)
* 追蹤URL
* 追蹤記錄的日期

在此Web追蹤模式中，如果遺失部分資訊，則不會在應用程式中建立追蹤記錄。

此模式在數量（trackingLog表格中的記錄數量有限）和計算（無調解）方面比較經濟。

**永久網路追蹤模式的特性：**

此網路追蹤模式可讓您根據永久性uuid230 Cookie的存在來建立追蹤記錄。 如果訪客關閉其工作階段，Adobe Campaign會使用永久Cookie，從先前的追蹤記錄中復原有關訪客的資訊。 如果目前工作階段的uuid230與追蹤表格中已儲存的uuid230具有相同的值，Adobe Campaign會重新插入追蹤記錄。

這表示先前必須在Adobe Campaign中識別訪客（透過傳送），才能啟用對uuid230值的調解。

依預設，在「trackingLog」表格中執行先前追蹤記錄中的搜尋。 如果Leads套件已啟用，在搜尋「trackingLog」表格之前，Adobe Campaign會在「incomingLead」表格中搜尋先前的追蹤記錄記錄。

在記錄調解期間，此模式的計算成本很高。

**匿名網路追蹤模式的特性：**

此網路追蹤模式可讓您擷取連結至Adobe Campaign中匿名瀏覽的追蹤記錄。 每次點按追蹤的URL，系統都會自動建立追蹤記錄。 此記錄檔只有uuid230的值。 在行銷活動期間，會自動建立追蹤記錄，內含所有識別資訊（請參閱工作階段追蹤）。 Adobe Campaign會自動在先前的記錄中搜尋等於此行銷活動之追蹤記錄值的「uuid230」值。 如果找到相同的值，則會以行銷活動追蹤記錄中的所有資訊輸入所有先前的追蹤記錄。

此模式在計算與容量方面成本最高。

>[!NOTE]
>
>如果 **[!UICONTROL Leads]** 套件已安裝，您必須對活動表格執行相同操作(**crm：incomingLead**)

下列結構描述總結了所有三種網頁追蹤模式的功能：

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**根據上次傳遞的永久網路追蹤範例：**

Florence收到傳遞、開啟電子郵件、按一下連結、在零售網站上瀏覽但未進行任何購買。 第二天，佛羅倫薩回到零售網站，瀏覽並進行購買。 由於永久網路追蹤（上次傳遞）已啟用，她第二次瀏覽的所有記錄都會連結至前一天傳送給她的傳遞。
