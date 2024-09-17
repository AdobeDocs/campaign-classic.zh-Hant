---
product: campaign
title: Adobe Analytics聯結器布建
description: 深入瞭解Adobe Analytics聯結器布建
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於v7內部部署和混合部署"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Adobe Analytics 連接器佈建 {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> 這些步驟應該只能由混合及內部部署實作來執行。
>
>針對託管和促銷活動Managed Services實作，請聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)團隊。

Adobe Campaign Classic與Adobe Analytics驗證之間的整合支援AdobeIdentity Management服務(IMS)：

* 如果您管理已移轉的外部帳戶，您必須實作Adobe IMS並透過Adobe ID連線至Adobe Campaign。

  請注意，透過Adobe ID IMS登入的使用者必須是Adobe Analytics中&#x200B;**Data Connector**&#x200B;帳戶的所有者，並且擁有以下[提及的&#x200B;**產品設定檔**&#x200B;的許可權](#analytics-product-profile)。

問題是資料聯結器的擁有者與登入Campaign並嘗試與Analytics整合的使用者不是使用者。

* 如果您正在實作新的聯結器，實作Adobe IMS為選用。 如果沒有Adobe ID使用者，Adobe Campaign將使用技術使用者來與Adobe Analytics同步。

為了讓此整合發揮作用，您必須建立Adobe Analytics產品設定檔，此設定檔將專門用於Analytics聯結器。 之後，您將需要建立開發人員控制檯專案。

>[!AVAILABILITY]
>
> Adobe已棄用服務帳戶(JWT)認證，Campaign與Adobe解決方案和應用程式的整合現在必須依賴OAuth伺服器對伺服器認證。 </br>
>
> * 如果您已實作與Campaign的傳入整合，您必須移轉您的技術帳戶，如[本檔案](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank)所詳述。 現有的[服務帳戶(JWT)認證](oauth-technical-account.md)將持續運作到2025年1月27日。</br>
>
> * 如果您已實作輸出整合(例如Campaign-Analytics整合或Experience Cloud Triggers整合)，則在2025年1月27日前都能正常運作。 不過，在該日期之前，您必須將您的Campaign環境升級至v7.4.1，並將您的技術帳戶移轉至OAuth。

## 建立Adobe Analytics產品設定檔 {#analytics-product-profile}

產品設定檔可決定使用者對不同Analytics元件的存取層級。

如果您已有Analytics產品設定檔，您仍應建立專用於Analytics聯結器的新Adobe Analytics產品設定檔。 這將確保您的產品設定檔已設定為此整合的正確許可權。

如需產品設定檔的詳細資訊，請參閱[Admin Console檔案](https://helpx.adobe.com/mt/enterprise/admin-guide.html)。

1. 從[Admin Console](https://adminconsole.adobe.com/)，選取您的Adobe Analytics **[!UICONTROL Product]**。

   ![](assets/do-not-localize/triggers_1.png)

1. 按一下&#x200B;**[!UICONTROL New Profile]**。

   ![](assets/do-not-localize/triggers_2.png)

1. 新增&#x200B;**[!UICONTROL Product profile name]**，我們建議使用下列語法： `reserved_campaign_classic_<Company Name>`。 然後，按一下&#x200B;**[!UICONTROL Next]**。

   此&#x200B;**[!UICONTROL Product profile]**&#x200B;應專用於Analytics Connector，以防止設定錯誤錯誤。

1. 開啟您新建立的&#x200B;**[!UICONTROL Product profile]**&#x200B;並選取&#x200B;**[!UICONTROL Permissions]**&#x200B;標籤。

   ![](assets/do-not-localize/triggers_3.png)

1. 按一下「**[!UICONTROL Edit]**」設定不同的功能，並按一下加號(+)圖示來選取要指派給您&#x200B;**[!UICONTROL Product profile]**&#x200B;的許可權。

   有關如何管理許可權的詳細資訊，請參閱[Admin Console檔案](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html)。

1. 針對&#x200B;**[!UICONTROL Report Suites]**&#x200B;功能，新增您稍後需要使用的&#x200B;**[!UICONTROL Report Suites]**。

   如果您沒有任何報表套裝，您可以依照[這些步驟](../../integrations/using/gs-aa.md)建立它。

   ![](assets/do-not-localize/triggers_4.png)

1. 針對&#x200B;**[!UICONTROL Metrics]**&#x200B;功能，新增您稍後需要設定的&#x200B;**[!UICONTROL Metrics]**。

   如有需要，您可以開啟「自動包含」選項，這會將每個許可權專案新增至包含的清單中，並自動新增許可權專案。

   ![](assets/do-not-localize/triggers_13.png)

1. 針對&#x200B;**[!UICONTROL Dimensions]**&#x200B;功能，新增未來設定所需的&#x200B;**[!UICONTROL Dimensions]**。

   確保所選的Dimension符合要在外部帳戶中設定的事件，並與Adobe Analytics中對應的eVar編號一致。

1. 針對&#x200B;**[!UICONTROL Report Suite Tools]**&#x200B;功能，新增下列許可權：

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. 針對&#x200B;**[!UICONTROL Analytics Tools]**&#x200B;功能，新增下列許可權：

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

您的產品設定檔現已設定完成。 然後，您需要建立OAuth專案。

## 建立Oauth專案 {#create-adobe-io}

若要繼續設定Adobe Analytics聯結器，請存取Adobe Developer主控台並建立您的OAuth伺服器對伺服器專案。

如需詳細檔案，請參閱[此頁面](oauth-technical-account.md#oauth-service)。

## 設定與使用 {#adobe-analytics-connector-usage}

在[Adobe Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}中瞭解如何使用Adobe Campaign和Adobe Analytics。