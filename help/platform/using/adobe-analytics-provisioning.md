---
solution: Campaign Classic
product: campaign
title: Adobe Analytics 連接器
description: 深入瞭解 Adobe Analytics 連接器 布建
feature: Overview
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 671e29425e8962ced833c10303b6edce7afda462
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 4%

---

# Adobe Analytics 連接器佈建 {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> 這些步驟只應由混合式和內部部署實作執行。
>
>若為托管實作，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 團隊。

Adobe Campaign Classic與Adobe Analytics驗證的整合支援AdobeIdentity Management服務(IMS):

* 如果您管理移轉的外部帳戶，您必須實作Adobe IMS並透過Adobe ID連線至Adobe Campaign。 透過Adobe ID IMS登入的使用者應為 **資料連接器** 帳戶，且擁有 **產品設定檔** 已提及。

* 若您正在實作新連接器，則可選擇實作Adobe IMS。 若無Adobe ID使用者，Adobe Campaign將使用技術使用者與Adobe Analytics同步。

為了讓這項整合發揮作用，您必須建立專供Analytics連接器使用的Adobe Analytics產品設定檔。 然後，您需要建立Adobe I/O專案。

## 建立Adobe Analytics產品設定檔 {#analytics-product-profile}

產品設定檔會決定使用者在您不同的Analytics元件上的存取層級。

如果您已有Analytics產品設定檔，仍應建立專用於Analytics連接器的新Adobe Analytics產品設定檔。 這可確保您的產品設定檔已針對這項整合設定正確的權限。

如需產品設定檔的詳細資訊，請參閱 [Admin Console檔案](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. 從 [Admin Console](https://adminconsole.adobe.com/)，選取您的Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. 按一下&#x200B;**[!UICONTROL New Profile]**。

   ![](assets/do-not-localize/triggers_2.png)

1. 新增 **[!UICONTROL Product profile name]**，建議您使用下列語法： `reserved_campaign_classic_<Company Name>`. 然後，按一下 **[!UICONTROL Next]**.

   此 **[!UICONTROL Product profile]** 應專用於Analytics Connector，以防止發生錯誤設定錯誤。

1. 開啟新建立的 **[!UICONTROL Product profile]** ，然後選取 **[!UICONTROL Permissions]** 標籤。

   ![](assets/do-not-localize/triggers_3.png)

1. 按一下「 」，設定不同的功能 **[!UICONTROL Edit]** 並選取要指派給您的 **[!UICONTROL Product profile]** 按一下加號(+)圖示即可。

   如需如何管理權限的詳細資訊，請參閱 [Admin Console檔案](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. 若 **[!UICONTROL Report Suites]** 功能，新增 **[!UICONTROL Report Suites]** 您需要稍後使用。

   如果您沒有任何報表套裝，可依下列項目建立 [這些步驟](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. 若 **[!UICONTROL Metrics]** 功能，新增 **[!UICONTROL Metrics]** 您以後需要配置。

   如有需要，您可以切換「自動包含」選項，該選項會將每個權限項目新增至包含的清單中，並自動新增權限項目。

   ![](assets/do-not-localize/triggers_13.png)

1. 若 **[!UICONTROL Dimensions]** 功能，新增 **[!UICONTROL Dimensions]** 您以後需要配置。

1. 若 **[!UICONTROL Report Suite Tools]** 功能，新增下列權限：

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. 若 **[!UICONTROL Analytics Tools]** 功能，新增下列權限：

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

您的產品設定檔現已設定完畢。 然後，您需要建立Adobe I/O專案。

## 建立Adobe I/O專案 {#create-adobe-io}

1. 存取Adobe I/O並登入為 **系統管理員** IMS組織的URL。

   如需管理員角色的詳細資訊，請參閱 [頁面](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. 按一下&#x200B;**[!UICONTROL Create a new project]**。

   ![](assets/do-not-localize/triggers_5.png)

1. 按一下 **[!UICONTROL Add to Project]** 選取 **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. 選取 [!DNL Adobe Analytics] 並按一下 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_7.png)

1. 選擇 **[!UICONTROL Service Account (JWT)]** 作為驗證類型，請按一下 **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_8.png)

1. 選取 **[!UICONTROL Option 1: Generate a Key-Pair]** 選項，然後按一下 **[!UICONTROL Generate a Key-Pair]**.

   然後會自動下載config.zip檔案。

   ![](assets/do-not-localize/triggers_9.png)

1. 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_10.png)

1. 選取 **[!UICONTROL Product profile]** 在前述步驟中建立，詳見 [節](#analytics-product-profile).

1. 然後，按一下 **[!UICONTROL Save Configured API]**.

   ![](assets/do-not-localize/triggers_11.png)

1. 從專案中選取 [!DNL Adobe Analytics] 並複製下列資訊 **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/triggers_12.png)

1. 使用以下命令將這些服務帳戶憑據貼到nlserver :

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

您現在可以開始使用Analytics連接器並追蹤客戶行為。
