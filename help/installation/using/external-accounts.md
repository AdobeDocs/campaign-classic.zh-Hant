---
solution: Campaign Classic
product: campaign
title: 外部帳戶
description: 瞭解如何建立外部帳戶
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: bfe2e29ed904b6a04bab28455301437c63ab8118
workflow-type: tm+mt
source-wordcount: '1612'
ht-degree: 11%

---


# 外部帳戶{#external-accounts}

Adobe Campaign 隨附一組預先定義的外部帳戶。為了與外部系統建立連接，您可以建立新的外部帳戶。

技術流程（例如技術工作流程或宣傳工作流程）會使用外部帳戶。在工作流程中或與任何其他應用程式（Adobe Target、Experience Manager 等）進行資料交換時，您需要選取外部帳戶。

您可以設定下列外部帳戶類型：

* [傳送外部帳戶](#routing-external-account)
* [FTP外部帳戶](#ftp-external-account)
* [外部資料庫外部帳戶](#external-database-external-account)
* [Web Analytics外部帳戶](#web-analytics-external-account)
* [Facebook Connect外部帳戶](#facebook-connect-external-account)
* [執行實例外部帳戶](#execution-instance-external-account)
* [Adobe Experience Cloud外部帳戶](#adobe-experience-cloud-external-account)
* [SFTP 外部帳戶](#sftp-external-account)
* [Adobe Experience Manager 外部帳戶](#adobe-experience-manager-external-account)
* [Amazon簡易儲存服務(S3)外部帳戶](#amazon-simple-storage-service--s3--external-account)
* [Microsoft Dynamics CRM外部帳戶](#microsoft-dynamics-crm-external-account)
* [Salesforce CRM外部帳戶](#salesforce-crm-external-account)
* [Azure Blob 儲存外部帳戶](#azure-blob-external-account)

## 建立外部帳戶 {#creating-an-external-account}

若要建立新的外部帳戶，請遵循下列步驟。 詳細設定取決於外部帳戶的類型。

1. 在促銷活動&#x200B;**[!UICONTROL Explorer]**&#x200B;中，選擇&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

   ![](assets/ext_account_1.png)

1. 按一下 **[!UICONTROL New]** 按鈕。

   ![](assets/ext_account_2.png)

1. 輸入&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal Name]**。
1. 選擇要建立的外部帳戶&#x200B;**[!UICONTROL Type]**。
1. 根據所選的外部帳戶類型指定憑證，以設定帳戶的存取權。

   所需資訊通常由您所連接的伺服器提供者提供。

1. 選中&#x200B;**[!UICONTROL Enabled]**&#x200B;選項以激活連接。
1. 按一下 **[!UICONTROL Save]**。

外部帳戶會建立並新增至外部帳戶清單。

## 彈回郵件外部帳戶{#bounce-mails-external-account}

**Bouncemails**&#x200B;外部帳戶指定用於連接電子郵件服務的外部POP3帳戶。 有關此外部帳戶的詳細資訊，請參閱此[頁](../../workflow/using/inbound-emails.md)。

為POP3訪問配置的所有伺服器都可用於接收返回郵件。

![](assets/ext_account_6.png)

要配置&#x200B;**[!UICONTROL Bounce mails (defaultPopAccount)]**&#x200B;外部帳戶：

* **[!UICONTROL Server]**

   POP3伺服器的URL。

* **[!UICONTROL Port]**

   POP3連接埠號。 預設埠為110。

* **[!UICONTROL Account]**

   用戶名。

* **[!UICONTROL Password]**

   使用者帳戶密碼。

* **[!UICONTROL Encryption]**

   在&#x200B;**[!UICONTROL By default]**、**[!UICONTROL POP3 + STARTTLS]**、**[!UICONTROL POP3]**&#x200B;或&#x200B;**[!UICONTROL POP3S]**&#x200B;之間選擇的加密類型。

## 路由外部帳戶{#routing-external-account}

**[!UICONTROL Routing]**&#x200B;外部帳戶允許您根據所安裝的軟體包配置Adobe Campaign的每個可用通道。

![](assets/ext_account_7.png)

可以配置以下通道：

* [電子郵件](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [行動裝置（簡訊）](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [電話](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [直接郵件](../../delivery/using/about-direct-mail-channel.md)
* [代理商](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [iOS頻道](../../delivery/using/configuring-the-mobile-application.md)
* [Android頻道](../../delivery/using/configuring-the-mobile-application-android.md)

## FTP外部帳戶{#ftp-external-account}

FTP外部帳戶可讓您設定並測試對Adobe Campaign以外伺服器的存取。 若要設定與外部系統（例如用於檔案傳輸的FTP伺服器898）的連線，您可以建立自己的外部帳戶。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/file-transfer.md)。

若要這麼做，請在此外部帳戶中指定用來建立與FTP伺服器連線的位址和認證

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

   FTP伺服器的名稱。

* **[!UICONTROL Port]**

   FTP連接埠號。 預設埠為21。

* **[!UICONTROL Account]**

   用戶名。

* **[!UICONTROL Password]**

   使用者帳戶密碼。

* **[!UICONTROL Encryption]**

   在&#x200B;**[!UICONTROL None]**&#x200B;或&#x200B;**[!UICONTROL SSL]**&#x200B;之間選擇的加密類型。

要知道這些憑據的位置，請參閱此[頁](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials)。

## 外部資料庫外部帳戶{#external-database-external-account}

使用&#x200B;**External database**&#x200B;鍵入外部帳戶以連接到外部資料庫。 在[本節](../../installation/using/about-fda.md)中進一步瞭解Federated Data Access(FDA)選項。

與Campaign相容的外部資料庫列在[相容性矩陣](../../rn/using/compatibility-matrix.md)中

![](assets/ext_account_11.png)

外部帳戶配置設定取決於資料庫引擎。 以下各節提供更多資訊：

* 配置對[Azure synapse](../../installation/using/configure-fda-synapse.md)的訪問
* 配置對[Hadoop](../../installation/using/configure-fda-hadoop.md)的訪問
* 配置對[Oracle](../../installation/using/configure-fda-oracle.md)的訪問
* 配置對[Netezza](../../installation/using/configure-fda-netezza.md)的訪問
* 配置對[SAP HANA](../../installation/using/configure-fda-sap-hana.md)的訪問
* 配置對[Snowflake](../../installation/using/configure-fda-snowflake.md)的訪問
* 配置對[Sybase IQ](../../installation/using/configure-fda-sybase.md)的訪問
* 配置對[Teradata](../../installation/using/configure-fda-teradata.md)的訪問

## Web Analytics外部帳戶{#web-analytics-external-account}

**[!UICONTROL Web Analytics (Adobe Analytics - Data connector)]**&#x200B;外部帳戶允許您將資料以段的形式從Adobe Analytics轉發到Adobe Campaign。 相反地，它會將Adobe Campaign傳送的電子郵件促銷活動的指標和屬性傳送至Adobe Analytics-資料連接器。

![](assets/ext_account_10.png)

對於此外部帳戶，必須豐富追蹤URL的計算公式，並且必須核准兩個解決方案之間的連線。 如需關於此項目的詳細資訊，請參閱此[頁面](../../platform/using/adobe-analytics-data-connector.md#step-2--create-the-external-account-in-campaign)。

## Facebook連線外部帳戶{#facebook-connect-external-account}

**[!UICONTROL Facebook Connect]**&#x200B;外部帳戶可讓您在Facebook應用程式中顯示個人化內容，讓透過此社交網路取得潛在客戶變得更輕鬆。

對於每個Facebook應用程式，您必須建立&#x200B;**[!UICONTROL Facebook Connect]**&#x200B;類型的外部帳戶。 如需詳細資訊，請參閱[ page](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   **[!UICONTROL hosted by a partner]**&#x200B;或&#x200B;**[!UICONTROL hosted by this instance]**&#x200B;之間應用程式的代管模式。

* **[!UICONTROL Application ID]**

   您Facebook應用程式的應用程式ID。

* **[!UICONTROL Application secret]**

   您Facebook應用程式的應用程式密碼。

如果您選擇此例項模式代管，則「保全畫布URL」必須貼入Facebook上的&#x200B;**Facebook網頁遊戲(https)**&#x200B;欄位

要知道這些憑據的位置，請參閱此[頁](https://developers.facebook.com/docs/facebook-login/access-tokens)。

## 執行實例外部帳戶{#execution-instance-external-account}

如果您有劃分的架構，則需要指定連結至控制例項的執行例項，並加以連接。 事務性消息模板部署到執行實例

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   安裝執行實例的伺服器的URL。

* **[!UICONTROL Account]**

   帳戶名稱，它必須與在運算子資料夾中定義的「訊息中心代理」相符。

* **[!UICONTROL Password]**

   操作員資料夾中定義的帳戶密碼。

有關此配置的詳細資訊，請參閱此[頁](../../message-center/using/creating-a-shared-connection.md#control-instance)。

## Adobe Experience Cloud外部帳戶{#adobe-experience-cloud-external-account}

要使用Adobe ID連接到Adobe Campaign控制台，必須配置&#x200B;**[!UICONTROL Adobe Experience Cloud (MAC)]**&#x200B;外部帳戶。

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

   IMS伺服器的URL。 請確定舞台和生產執行個體都指向相同的IMS生產端點。

* **[!UICONTROL IMS scope]**

   此處定義的範圍必須是IMS所布建範圍的子集。

* **[!UICONTROL IMS client identifier]**

   IMS用戶端的ID。

* **[!UICONTROL IMS client secret]**

   IMS用戶端機密的憑證。

* **[!UICONTROL Callback server]**

   存取您的Adobe Campaign實例的URL。

* **[!UICONTROL IMS organization ID]**

   IMS組織的ID。 若要尋找您的組織ID，請參閱此[頁面](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html)（**哪裡可以找到我的IMS組織ID?**）。

* **[!UICONTROL Association mask]**

   語法，可讓Enterprise Dashboard中的設定名稱與Adobe Campaign的群組同步。

* **[!UICONTROL Server]**

   您的Adobe Experience Cloud實例的URL。

* **[!UICONTROL Tenant]**

   您的Adobe Experience Cloud租用戶名稱。

有關此配置的詳細資訊，請參閱此[頁](../../integrations/using/configuring-ims.md)。

## SFTP 外部帳戶 {#sftp-external-account}

SFTP外部帳戶可讓您設定並測試對Adobe Campaign以外伺服器的存取。 若要設定與外部系統（例如用於檔案傳輸的SFTP）的連線，您可以建立自己的外部帳戶。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/file-transfer.md)。

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   SFTP伺服器的URL。

* **[!UICONTROL Port]**

   FTP連接埠號。 預設埠為22。

* **[!UICONTROL Account]**

   用來連線至SFTP伺服器的帳戶名稱。

* **[!UICONTROL Password]**

   用於連接到SFTP伺服器的口令。

## Adobe Experience Manager 外部帳戶 {#adobe-experience-manager-external-account}

**[!UICONTROL AEM (AEM instance)]**&#x200B;外部帳戶可讓您直接在Adobe Experience Manager管理電子郵件傳送內容以及表格。

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   Adobe Experience Manager伺服器的URL。

* **[!UICONTROL Port]**

   用於連線至Adobe Experience Manager編寫例項的帳戶名稱。

* **[!UICONTROL Password]**

   用於連接到Adobe Experience Manager編寫實例的口令。

如需詳細資訊，請參閱本[區段](../../integrations/using/about-adobe-experience-manager.md)。

## Amazon簡單儲存服務(S3)外部帳戶{#amazon-simple-storage-service--s3--external-account}

Amazon簡單儲存服務(S3)連接器可用於將資料導入或導出到Adobe Campaign。 可在工作流活動中設定。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/file-transfer.md)。

![](assets/ext_account_3.png)

當您設定此新外部帳戶時，您必須提供下列詳細資訊：

* **[!UICONTROL AWS S3 Account Server]**

   伺服器的URL，應填入如下：

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL AWS access key ID]**

   要瞭解在何處查找您的AWS訪問密鑰ID，請參閱此[頁](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)。

* **[!UICONTROL Secret access key to AWS]**

   要瞭解在何處找到AWS的秘密訪問密鑰，請參閱此[頁](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/)。

* **[!UICONTROL AWS Region]**

   要瞭解有關AWS地區的更多資訊，請參閱此[頁](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)。

* 使用&#x200B;**[!UICONTROL Use server side encryption]**&#x200B;複選框可以以S3加密模式儲存檔案。

要瞭解在何處查找訪問密鑰ID和秘密訪問密鑰，請參閱Amazon網站服務[文檔](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys)。

## Microsoft Dynamics CRM外部帳戶{#microsoft-dynamics-crm-external-account}

**[!UICONTROL Microsoft Dynamics CRM]**&#x200B;外部帳戶允許您將Microsoft Dynamics資料導入和導出到Adobe Campaign。

在此[頁面](../../platform/using/crm-ms-dynamics.md)中進一步瞭解Campaign - Microsoft Dynamics CRM連接器。

>[!NOTE]
>
> **[!UICONTROL On-premise]** 而部 **[!UICONTROL Office 365]** 署類型現在已過時。[進一步瞭解](../../rn/using/deprecated-features.md)。

使用&#x200B;**[!UICONTROL Web API]**&#x200B;部署類型和&#x200B;**[!UICONTROL Password credentials]**&#x200B;驗證，您需要提供以下詳細資訊：

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   用來登入Microsoft CRM的帳戶。

* **[!UICONTROL Server]**

   Microsoft CRM伺服器的URL。

* **[!UICONTROL Client identifier]**

   可從&#x200B;**[!UICONTROL Update your code]**&#x200B;類別&#x200B;**[!UICONTROL Client ID]**&#x200B;欄位中的Microsoft Azure管理入口網站找到的用戶端ID。

* **[!UICONTROL CRM version]**

   **[!UICONTROL Dynamics CRM 2007]**、**[!UICONTROL Dynamics CRM 2015]**&#x200B;或&#x200B;**[!UICONTROL Dynamics CRM 2016]**&#x200B;之間的CRM版本。

使用&#x200B;**[!UICONTROL Web API]**&#x200B;部署類型和&#x200B;**[!UICONTROL Certificate]**&#x200B;驗證，您需要提供以下詳細資訊：

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   Microsoft CRM伺服器的URL。

* **[!UICONTROL Private Key (Base64 encoded)]**

   編碼為Base64的私密金鑰

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   可從&#x200B;**[!UICONTROL Update your code]**&#x200B;類別&#x200B;**[!UICONTROL Client ID]**&#x200B;欄位中的Microsoft Azure管理入口網站找到的用戶端ID。

* **[!UICONTROL CRM version]**

   **[!UICONTROL Dynamics CRM 2007]**、**[!UICONTROL Dynamics CRM 2015]**&#x200B;或&#x200B;**[!UICONTROL Dynamics CRM 2016]**&#x200B;之間的CRM版本。

有關此配置的詳細資訊，請參閱此[頁](../../platform/using/crm-connectors.md)。

## Salesforce CRM外部帳戶{#salesforce-crm-external-account}

**[!UICONTROL Salesforce CRM]**&#x200B;外部帳戶可讓您將Salesforce資料匯入並匯出至Adobe Campaign。

![](assets/ext_account_17.png)

若要設定Salesforce CRM外部帳戶以搭配Adobe Campaign使用，您必須提供下列詳細資訊：

* **[!UICONTROL Account]**

   用來登入Salesforce CRM的帳戶。

* **[!UICONTROL Password]**

   用於登入Salesforce CRM的密碼。

* **[!UICONTROL Client identifier]**

   若要知道在何處找到客戶識別碼，請參閱此[頁](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

* **[!UICONTROL Security token]**

   若要知道在何處找到安全令牌，請參閱此[頁](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

* **[!UICONTROL API version]**

   **[!UICONTROL Version 49]**、**[!UICONTROL Version 37]**、**[!UICONTROL Version 21]**&#x200B;或&#x200B;**[!UICONTROL Version 15]**&#x200B;之間的API版本。

對於此外部帳戶，您需要使用設定精靈來設定您的Salesforce CRM。

有關此配置的詳細資訊，請參閱此[頁](../../platform/using/crm-connectors.md)。

## Azure Blob儲存外部帳戶(#azure-blob-external-account)

**Azure Blob儲存**&#x200B;外部帳戶可用於使用&#x200B;**[!UICONTROL Transfer file]**&#x200B;工作流程活動將資料匯入或匯出至Adobe Campaign。 如需詳細資訊，請參閱本[區段](../../workflow/using/file-transfer.md)。

![](assets/ext_account_23.png)

要將&#x200B;**[!UICONTROL Azure external account]**&#x200B;配置為與Adobe Campaign合作，您需要提供以下詳細資訊：

* **[!UICONTROL Server]**

   您的Azure Blob儲存伺服器的URL。

* **[!UICONTROL Encryption]**

   在&#x200B;**[!UICONTROL None]**&#x200B;或&#x200B;**[!UICONTROL SSL]**&#x200B;之間選擇的加密類型。

* **[!UICONTROL Access key]**

   若要瞭解在何處找到&#x200B;**[!UICONTROL Access key]**，請參閱此[頁](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal)。
