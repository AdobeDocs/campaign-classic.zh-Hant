---
solution: Campaign Classic
product: campaign
title: Adobe Analytics 連接器
description: 深入瞭解 Adobe Analytics 連接器 布建
feature: Overview
role: User, Admin
level: Beginner
source-git-commit: 5f596c14639e085edab9c08c2e3abba36e76acd3
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 4%

---

# Adobe Analytics Connector布建 {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> 這些步驟只應由混合式和內部部署實作執行。
>
>若為托管實作，請聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)團隊。

Adobe Campaign Classic與Adobe Analytics驗證的整合支援AdobeIdentity Management服務(IMS)。 您必須先實作Adobe IMS，並透過Adobe ID](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/connect-to-campaign/connecting-via-an-adobe-id/about-adobe-id.html?lang=en)連線至Campaign [，再開始實作Analytics Connector。

為了讓這項整合發揮作用，您必須建立專供Analytics連接器使用的Adobe Analytics產品設定檔。 然後，您需要建立Adobe I/O專案。

## 建立Adobe Analytics產品設定檔 {#analytics-product-profile}

產品設定檔會決定使用者在您不同的Analytics元件上的存取層級。

如果您已有Analytics產品設定檔，仍應建立專用於Analytics連接器的新Adobe Analytics產品設定檔。 這可確保您的產品設定檔已針對這項整合設定正確的權限。

如需產品設定檔的詳細資訊，請參閱[管理控制台檔案](https://helpx.adobe.com/mt/enterprise/admin-guide.html)。

1. 從[管理控制台](https://adminconsole.adobe.com/)中，選取您的Adobe Analytics **[!UICONTROL Product]**。

   ![](assets/do-not-localize/triggers_1.png)

1. 按一下&#x200B;**[!UICONTROL New Profile]**。

   ![](assets/do-not-localize/triggers_2.png)

1. 新增&#x200B;**[!UICONTROL Product profile name]**，建議使用下列語法：`reserved_campaign_classic_<Company Name>`。 然後，按一下&#x200B;**[!UICONTROL Next]**。

   此&#x200B;**[!UICONTROL Product profile]**&#x200B;應專用於Analytics連接器，以防止發生錯誤設定。

1. 開啟新建立的&#x200B;**[!UICONTROL Product profile]**&#x200B;並選擇&#x200B;**[!UICONTROL Permissions]**&#x200B;頁簽。

   ![](assets/do-not-localize/triggers_3.png)

1. 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;並按一下加號(+)圖示，以設定要指派給&#x200B;**[!UICONTROL Product profile]**&#x200B;的不同功能。

   如需如何管理權限的詳細資訊，請參閱[Admin Console檔案](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html)。

1. 對於&#x200B;**[!UICONTROL Report Suites]**&#x200B;功能，添加需要稍後使用的&#x200B;**[!UICONTROL Report Suites]**。

   如果您沒有任何報表套裝，可以依照[這些步驟](../../platform/using/adobe-analytics-connector.md#report-suite-analytics)建立。

   ![](assets/do-not-localize/triggers_4.png)

1. 對於&#x200B;**[!UICONTROL Metrics]**&#x200B;功能，添加您以後需要配置的&#x200B;**[!UICONTROL Metrics]**。

   如有需要，您可以切換「自動包含」選項，該選項會將每個權限項目新增至包含的清單中，並自動新增權限項目。

   ![](assets/do-not-localize/triggers_13.png)

1. 對於&#x200B;**[!UICONTROL Dimensions]**&#x200B;功能，添加您以後需要配置的&#x200B;**[!UICONTROL Dimensions]**。

1. 對於&#x200B;**[!UICONTROL Report Suite Tools]**&#x200B;功能，新增下列權限：

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. 對於&#x200B;**[!UICONTROL Analytics Tools]**&#x200B;功能，新增下列權限：

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

您的產品設定檔現已設定完畢。 然後，您需要建立Adobe I/O專案。

## 建立Adobe I/O專案 {#create-adobe-io}

1. 存取Adobe I/O並以IMS組織的&#x200B;**系統管理員**&#x200B;登入。

   有關管理員角色的詳細資訊，請參閱此[page](https://helpx.adobe.com/enterprise/using/admin-roles.html)。

1. 按一下&#x200B;**[!UICONTROL Create a new project]**。

   ![](assets/do-not-localize/triggers_5.png)

1. 按一下&#x200B;**[!UICONTROL Add to Project]**&#x200B;並選擇&#x200B;**[!UICONTROL API]**。

   ![](assets/do-not-localize/triggers_6.png)

1. 選取 [!DNL Adobe Analytics] 並按一下 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_7.png)

1. 選擇&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;作為身份驗證類型，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_8.png)

1. 選擇&#x200B;**[!UICONTROL Option 1: Generate a Key-Pair]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Generate a Key-Pair]**。

   然後會自動下載config.zip檔案。

   ![](assets/do-not-localize/triggers_9.png)

1. 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/do-not-localize/triggers_10.png)

1. 選擇在前面的步驟中建立的&#x200B;**[!UICONTROL Product profile]**，詳見此[節](#analytics-product-profile)。

1. 然後，按一下&#x200B;**[!UICONTROL Save Configured API]**。

   ![](assets/do-not-localize/triggers_11.png)

1. 從您的專案中，選取[!DNL Adobe Analytics]並複製&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;下的下列資訊：

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
