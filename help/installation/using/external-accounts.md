---
product: campaign
title: 外部帳戶
description: 了解如何建立外部帳戶
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1714'
ht-degree: 9%

---

# 外部帳戶{#external-accounts}



Adobe Campaign 隨附一組預先定義的外部帳戶。若要設定與外部系統的連線，您可以建立新的外部帳戶。

技術流程（例如技術工作流程或宣傳工作流程）會使用外部帳戶。例如，在工作流程中設定檔案傳輸，或與任何其他應用程式(Adobe Target、Experience Manager等)進行資料交換時，您需要選取外部帳戶。

## 建立外部帳戶 {#creating-an-external-account}

若要建立新外部帳戶，請遵循下列步驟。 詳細設定取決於外部帳戶的類型。

1. 從促銷活動 **[!UICONTROL Explorer]**，選取 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. 按一下 **[!UICONTROL New]** 按鈕。

   ![](assets/ext_account_2.png)

1. 輸入 **[!UICONTROL Label]** 和 **[!UICONTROL Internal Name]**.
1. 選取您的外部帳戶 **[!UICONTROL Type]** 您要建立的。
1. 根據所選外部帳戶類型指定憑證，以設定帳戶的存取權。

   所需資訊通常由您所連接的伺服器提供者提供。

1. 檢查 **[!UICONTROL Enabled]** 選項啟用連線。
1. 按一下&#x200B;**[!UICONTROL Save]**。

外部帳戶會建立並新增至外部帳戶清單。

## 促銷活動專用外部帳戶

### 退回郵件 {#bounce-mails-external-account}

此 **退回郵件** 外部帳戶指定用於連接到電子郵件服務的外部POP3帳戶。 有關此外部帳戶的詳細資訊，請參閱 [頁面](../../workflow/using/inbound-emails.md).

所有為POP3訪問配置的伺服器都可用於接收返回郵件。

![](assets/ext_account_6.png)

若要設定 **[!UICONTROL Bounce mails (defaultPopAccount)]** 外部帳戶：

* **[!UICONTROL Server]**

   POP3伺服器的URL。

* **[!UICONTROL Port]**

   POP3連接埠號。 預設埠為110。

* **[!UICONTROL Account]**

   使用者名稱。

* **[!UICONTROL Password]**

   用戶帳戶密碼。

* **[!UICONTROL Encryption]**

   選擇的加密類型 **[!UICONTROL By default]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** 或 **[!UICONTROL POP3S]**.

* **[!UICONTROL Function]**

   傳入電子郵件或SOAP路由器

>[!IMPORTANT]
>
>使用Microsoft OAuth 2.0設定POP3外部帳戶前，您必須先在Azure入口網站中註冊應用程式。 如需詳細資訊，請參閱[此頁面](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app)。

配置POP3外部，使用 **Microsoft OAuth 2.0**，檢查 **[!UICONTROL Microsoft OAuth 2.0]** 選項並填寫下列欄位：

* **[!UICONTROL Azure tenant]**

   在 **要點** Azure入口網站中應用程式概述的下拉式清單。

* **[!UICONTROL Azure Client ID]**

   在 **要點** Azure入口網站中應用程式概述的下拉式清單。

* **[!UICONTROL Azure Client secret]**

   可在 **用戶端密碼** 欄 **憑證與機密** Azure門戶中的應用程式菜單。

* **[!UICONTROL Azure Redirect URL]**

   可在 **驗證** Azure門戶中的應用程式菜單。 結尾應為下列語法 `nl/jsp/oauth.jsp`，例如 `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

輸入不同的憑證後，您可以按一下 **[!UICONTROL Setup the connection]** 完成外部帳戶配置。

### 路由{#routing-external-account}

此 **[!UICONTROL Routing]** 外部帳戶可讓您根據安裝的套件，設定Adobe Campaign中可用的每個管道。

![](assets/ext_account_7.png)

可設定下列通道：

* [電子郵件](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [行動裝置（簡訊）](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [電話](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [直接郵件](../../delivery/using/about-direct-mail-channel.md)
* [代理商](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Twitter](../../social/using/about-social-marketing.md)
* [iOS 管道](../../delivery/using/configuring-the-mobile-application.md)
* [Android 管道](../../delivery/using/configuring-the-mobile-application-android.md)

### 執行實例  {#execution-instance-external-account}

如果您有劃分架構，則需要指定連結至控制執行個體的執行執行個體，並加以連結。 交易式訊息範本部署至執行例項

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   安裝執行實例的伺服器的URL。

* **[!UICONTROL Account]**

   帳戶名稱，它必須符合運算子資料夾中定義的訊息中心代理。

* **[!UICONTROL Password]**

   運算子資料夾中定義的帳戶密碼。

有關此配置的詳細資訊，請參閱 [頁面](../../message-center/using/configuring-instances.md#control-instance).

## 訪問外部系統外部帳戶

### FTP {#ftp-external-account}

FTP外部帳戶可讓您設定及測試對Adobe Campaign以外之伺服器的存取。 若要設定與外部系統（例如用於檔案傳輸的FTP伺服器898）的連線，您可以建立自己的外部帳戶。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/file-transfer.md)。

若要這麼做，請在此外部帳戶中指定用來建立與FTP伺服器連線的位址和憑證

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

   FTP伺服器的名稱。

* **[!UICONTROL Port]**

   FTP連接埠號。 預設埠為21。

* **[!UICONTROL Account]**

   使用者名稱。

* **[!UICONTROL Password]**

   用戶帳戶密碼。

* **[!UICONTROL Encryption]**

   選擇的加密類型 **[!UICONTROL None]** 或 **[!UICONTROL SSL]**.

要了解在何處找到這些憑據，請參閱 [頁面](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

### SFTP {#sftp-external-account}

SFTP外部帳戶可讓您設定及測試對Adobe Campaign以外伺服器的存取。 若要設定與外部系統（例如用於檔案傳輸的SFTP）的連線，您可以建立自己的外部帳戶。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/file-transfer.md)。

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   SFTP伺服器的URL。

* **[!UICONTROL Port]**

   FTP連接埠號。 預設埠為22。

* **[!UICONTROL Account]**

   用來連線至SFTP伺服器的帳戶名稱。

* **[!UICONTROL Password]**

   用於連線至SFTP伺服器的密碼。

要在Windows上添加SSH密鑰：

1. 建立 **首頁** 環境變數，且值設為安裝目錄。

2. 將您的私密金鑰新增至 `/$HOME/.ssh/id_rsa` 檔案夾。

3. 重新啟動Adobe Campaign服務。

### 外部資料庫(FDA) {#external-database-external-account}

使用 **外部資料庫** 鍵入外部帳戶以連接到外部資料庫。 深入了解同盟資料存取(FDA)選項，位於 [本節](../../installation/using/about-fda.md).

在 [相容性矩陣](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

外部帳戶配置設定取決於資料庫引擎。 進一步了解以下章節：

* 設定存取權 [vertica analytics](../../installation/using/configure-fda-vertica.md)
* 設定存取權 [Snowflake](../../installation/using/configure-fda-snowflake.md)
* 設定存取權 [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* 設定存取權 [azure synapse](../../installation/using/configure-fda-synapse.md)
* 設定存取權 [Hadoop](../../installation/using/configure-fda-hadoop.md)
* 設定存取權 [Oracle](../../installation/using/configure-fda-oracle.md)
* 設定存取權 [Netezza](../../installation/using/configure-fda-netezza.md)
* 設定存取權 [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* 設定存取權 [Snowflake](../../installation/using/configure-fda-snowflake.md)
* 設定存取權 [sybase IQ](../../installation/using/configure-fda-sybase.md)
* 設定存取權 [Teradata](../../installation/using/configure-fda-teradata.md)


## Adobe解決方案整合外部帳戶

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

若要使用Adobe ID連線至Adobe Campaign主控台，您必須設定 **[!UICONTROL Adobe Experience Cloud (MAC)]** 外部帳戶。

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

   您的IMS伺服器URL。 請確定預備和生產執行個體都指向相同的IMS生產端點。

* **[!UICONTROL IMS scope]**

   此處定義的範圍必須是IMS布建範圍的子集。

* **[!UICONTROL IMS client identifier]**

   您的IMS用戶端ID。

* **[!UICONTROL IMS client secret]**

   IMS用戶端密碼的憑證。

* **[!UICONTROL Callback server]**

   存取Adobe Campaign例項的URL。

* **[!UICONTROL IMS organization ID]**

   組織ID。 若要尋找組織ID，請參閱 [本頁](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}。

* **[!UICONTROL Association mask]**

   允許將Enterprise Dashboard中的設定名稱同步至Adobe Campaign中群組的語法。

* **[!UICONTROL Server]**

   Adobe Experience Cloud例項的URL。

* **[!UICONTROL Tenant]**

   您的Adobe Experience Cloud租用戶名稱。

有關此配置的詳細資訊，請參閱 [本頁](../../integrations/using/configuring-ims.md).

## 網站分析 {#web-analytics-external-account}

此 **[!UICONTROL Web Analytics]** 外部帳戶可讓您以區段形式將資料從Adobe Analytics轉送至Adobe Campaign。 相反地，它會將Adobe Campaign傳送之電子郵件促銷活動的指標和屬性傳送至Adobe Analytics連接器。

![](assets/ext_account_10.png)

對於此外部帳戶，必須擴充追蹤URL的計算公式，且必須核准兩個解決方案之間的連線。 如需關於此項目的詳細資訊，請參閱此[頁面](../../platform/using/adobe-analytics-connector.md#external-account-classic)。

### Adobe Experience Manager {#adobe-experience-manager-external-account}

此 **[!UICONTROL AEM (AEM instance)]** 外部帳戶可讓您直接在Adobe Experience Manager中管理電子郵件傳送的內容以及表單。

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   Adobe Experience Manager伺服器的URL。

* **[!UICONTROL Port]**

   用來連線至Adobe Experience Manager編寫執行個體的帳戶名稱。

* **[!UICONTROL Password]**

   用來連線至Adobe Experience Manager製作執行個體的密碼。

如需詳細資訊，請參閱本[區段](../../integrations/using/about-adobe-experience-manager.md)。

## CRM連接器外部帳戶

### Microsoft Dynamics CRM {#microsoft-dynamics-crm-external-account}

>[!NOTE]
>
> **[!UICONTROL On-premise]** 和 **[!UICONTROL Office 365]** 部署類型現已過時。 [了解更多](../../rn/using/deprecated-features.md)。

此 **[!UICONTROL Microsoft Dynamics CRM]** 外部帳戶可讓您將Microsoft Dynamics資料匯入和匯出至Adobe Campaign。

深入了解Campaign - Microsoft Dynamics CRM連接器，請參閱 [頁面](../../platform/using/crm-ms-dynamics.md).

使用 **[!UICONTROL Web API]** 部署類型和 **[!UICONTROL Password credentials]** 驗證時，您需要提供下列詳細資料：

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   用來登入Microsoft CRM的帳戶。

* **[!UICONTROL Server]**

   Microsoft CRM伺服器的URL。

   尋找您的Microsoft CRM **[!UICONTROL Server URL]**，請存取您的Microsoft Dynamics CRM帳戶，然後按一下 **Dynamics 365** 並選取您的應用程式。 然後，您就可以 **[!UICONTROL Server URL]** 在瀏覽器的位址列中，例如 `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client identifier]**

   用戶端ID，可從以下位置的Microsoft Azure管理入口網站找到： **[!UICONTROL Update your code]** 類別， **[!UICONTROL Client ID]** 欄位。

* **[!UICONTROL CRM version]**

   選擇 **[!UICONTROL Dynamics CRM 365]** CRM版本。

使用 **[!UICONTROL Web API]** 部署類型和 **[!UICONTROL Certificate]** 驗證時，您需要提供下列詳細資料：

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   Microsoft CRM伺服器的URL。

   尋找您的Microsoft CRM **[!UICONTROL Server URL]**，請存取您的Microsoft Dynamics CRM帳戶，然後按一下 **Dynamics 365** 並選取您的應用程式。 然後，您就可以 **[!UICONTROL Server URL]** 在瀏覽器的位址列中，例如 `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Private Key (Base64 encoded)]**

   請注意，私密金鑰需要編碼為Base64。

   要執行此操作，可以使用Base64編碼器的幫助或使用命令行 `base64 -w0 private.key` Linux版。

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   用戶端ID，可從以下位置的Microsoft Azure管理入口網站找到： **[!UICONTROL Update your code]** 類別， **[!UICONTROL Client ID]** 欄位。

* **[!UICONTROL CRM version]**

   CRM版本，介於 **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** 或 **[!UICONTROL Dynamics CRM 2016]**.

有關此配置的詳細資訊，請參閱 [頁面](../../platform/using/crm-connectors.md).

### Salesforce.com CRM  {#salesforce-crm-external-account}

此 **[!UICONTROL Salesforce CRM]** 外部帳戶可讓您將Salesforce資料匯入和匯出至Adobe Campaign。

![](assets/ext_account_17.png)

若要設定Salesforce CRM外部帳戶以搭配Adobe Campaign運作，您需要提供下列詳細資訊：

* **[!UICONTROL Account]**

   用於登入Salesforce CRM的帳戶。

* **[!UICONTROL Password]**

   用於登入Salesforce CRM的密碼。

* **[!UICONTROL Client identifier]**

   若要了解在何處尋找用戶端識別碼，請參閱 [頁面](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

   若要了解在何處尋找您的安全代號，請參閱 [頁面](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

   選取API的版本。

對於此外部帳戶，您需要使用配置嚮導配置Salesforce CRM。

有關此配置的詳細資訊，請參閱 [頁面](../../platform/using/crm-connectors.md).

## 傳輸資料外部帳戶

### Amazon Simple Storage Service(S3) {#amazon-simple-storage-service--s3--external-account}

Amazon Simple Storage Service(S3)連接器可用來匯入或匯出資料至Adobe Campaign。 可在工作流程活動中設定。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/file-transfer.md)。

![](assets/ext_account_3.png)

當您設定此新外部帳戶時，您必須提供下列詳細資訊：

* **[!UICONTROL AWS S3 Account Server]**

   伺服器的URL，應填入如下：

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL AWS access key ID]**

   若要了解在何處尋找您的AWS存取金鑰ID，請參閱 [頁面](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

* **[!UICONTROL Secret access key to AWS]**

   若要了解在何處尋找您的AWS秘密存取金鑰，請參閱此 [頁面](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

   若要深入了解AWS地區，請參閱 [頁面](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* 此 **[!UICONTROL Use server side encryption]** 核取方塊可讓您以S3加密模式儲存檔案。

若要了解在何處尋找存取金鑰ID和秘密存取金鑰，請參閱Amazon網站服務 [檔案](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

### Azure Blob 儲存體 {#azure-blob-external-account}

此 **Azure Blob儲存** 外部帳戶可用來匯入或匯出資料至Adobe Campaign，使用 **[!UICONTROL Transfer file]** 工作流程活動。 如需詳細資訊，請參閱本[區段](../../workflow/using/file-transfer.md)。

![](assets/ext_account_23.png)

若要設定 **[!UICONTROL Azure external account]** 若要與Adobe Campaign搭配使用，您必須提供下列詳細資訊：

* **[!UICONTROL Server]**

   Azure Blob儲存伺服器的URL。

* **[!UICONTROL Encryption]**

   選擇的加密類型 **[!UICONTROL None]** 或 **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

   知道在哪裡找到 **[!UICONTROL Access key]**，請參閱 [頁面](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
