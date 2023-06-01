---
product: campaign
title: 與 Windows 版 Web 伺服器整合
description: 與 Windows 版 Web 伺服器整合
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 4%

---

# 與 Windows 版 Web 伺服器整合{#integration-into-a-web-server-for-windows}



Adobe Campaign包含Apache Tomcat，可透過HTTP （和SOAP）作為應用程式伺服器的進入點。

您可以使用此整合式Tomcat伺服器來處理HTTP請求。

在此案例中：

* 預設接聽連線埠為8080。 若要變更，請參閱 [本節](../../installation/using/configure-tomcat.md).
* 然後，使用者端主控台會使用URL連線，例如 ```https:// `<computer>`:8080```.

不過，基於安全性與管理考量，建議使用專用網頁伺服器作為HTTP流量的主要入口點，因為執行Adobe Campaign的電腦會公開在網際網路上，而您想要開啟網路外部主控台的存取許可權。

網頁伺服器也可讓您使用HTTPs通訊協定來保證資料機密性。

同樣地，當您想要使用追蹤功能時，必須使用網頁伺服器，這項功能只能作為網頁伺服器擴充模組使用。

>[!NOTE]
>
>如果您未使用追蹤功能，可以執行標準Apache或IIS安裝，並重導至Campaign。 不需要追蹤Web伺服器擴充功能模組。

## 設定IIS Web伺服器 {#configuring-the-iis-web-server}

IIS Web伺服器的設定程式大多是圖形化的。 它涉及使用網站（已建立或暫止建立）來存取Adobe Campaign伺服器的資源：Java (.jsp)檔案、樣式表(.css、.xsl)、影像(.png)、用於重新導向的ISAPI DLL等。

以下小節詳細說明IIS 7中的設定。 IIS8的設定基本相同。

如果您的電腦尚未安裝Web IIS伺服器，您可以透過 **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** 功能表。

在IIS 7中，除了標準服務之外，您還需要安裝ISAPI擴充功能和ISAPI篩選器。

![](assets/s_ncs_install_iis7_isapi.png)

### 設定步驟 {#configuration-steps}

套用下列設定步驟：

1. 透過以下方式開啟IIS： **[!UICONTROL Control panel > Administrative tools > Services]** 功能表。
1. 根據網路引數（TCP連線連線埠、DNS主機、IP位址）建立及設定網站(例如Adobe Campaign)。

   ![](assets/s_ncs_install_iis7_add_site.png)

   您至少必須指定站台名稱以及虛擬目錄的存取路徑。 由於不使用Website目錄的存取路徑，因此您可以使用下列目錄。

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. A **VBS** script可讓您在我們剛建立的虛擬目錄上自動設定Adobe Campaign伺服器使用的資源。 若要啟動，請連按兩下 **iis_neolane_setup.vbs** 檔案位於 `[INSTALL]\conf` 資料夾，其中 `[INSTALL]` 是存取Adobe Campaign安裝資料夾的路徑。

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >若是Windows Server 2008/IIS7安裝，您必須以管理員身分登入，才能執行VBS指令碼或以管理員身分執行指令碼。

   按一下 **[!UICONTROL OK]** 如果Web伺服器是作為追蹤重新導向伺服器，否則請按一下 **[!UICONTROL Cancel]**.

   當已在網頁伺服器上設定多個網站時，會顯示一個中繼頁面，以指定安裝套用至哪個網站：輸入連結至網站的號碼，然後按一下 **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   應顯示確認訊息：

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. 在 **[!UICONTROL Content View]** 索引標籤中，確認網站已正確設定Adobe Campaign資源：

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   如果未顯示樹狀結構，請重新啟動IIS。

### 管理權限 {#managing-rights}

接下來，您必須為ISAPI DLL和Adobe Campaign安裝目錄中的資源設定安全性設定。

若要這麼做，請套用下列步驟：

1. 選取 **[!UICONTROL Features View]** 標籤並連按兩下 **驗證** 連結。

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. 在 **目錄安全性** 的標籤中，確定已啟用匿名存取。 如有需要，請按一下 **[!UICONTROL Edit]** 連結以變更設定。

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### 啟動Web伺服器並測試設定 {#launching-the-web-server-and-testing-the-configuration}

您現在必須測試設定是否正確。

要執行此操作，請套用下列程式：

1. 使用重新啟動IIS伺服器 **iisreset** 命令列。

1. 啟動Adobe Campaign服務，然後確認該服務正在執行。

1. 將下列URL插入網頁瀏覽器，以測試追蹤模組：

   ```
   https://<computer>/r/test
   ```

   瀏覽器應顯示下列回應：

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

若要測試重新導向模組是否存在，請執行以下命令列：

```
nlserver pdump
```

它必須傳回下列資訊：

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

您也可以確定ISAPI DLL已正確載入。

若要這麼做，請套用下列步驟：

1. 按一下「 」，編輯Adobe Campaign網站的ISAPI篩選器 **[!UICONTROL Driver mapping]** 圖示。
1. 檢查ISAPI篩選器的內容：

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## 其他設定 {#additional-configurations}

### 變更上傳檔案大小限制 {#changing-the-upload-file-size-limit}

設定IIS網頁伺服器時，上傳至伺服器的設定檔案會自動受到約28 MB的限制。

這可能會在Adobe Campaign中造成影響，尤其是當您想要上傳大於此限制的檔案時。

例如，如果您使用 **資料載入（檔案）** 在工作流程中輸入活動以匯入50 MB的檔案，錯誤會停止工作流程正確執行。

在此情況下，您必須增加此限制：

1. 透過以下方式開啟IIS： **[!UICONTROL Start > (Control panel) > Administration tools]** 功能表。
1. 在 **連線** 窗格，選取為Adobe安裝建立的網站，然後按兩下 **請求篩選** 於主窗格。
1. 在 **動作** 窗格，選取 **編輯功能設定** 才能編輯中的值 **授權內容大小上限（位元）** 欄位。

   例如，若要授權上傳50 MB的檔案，您必須指定大於「52428800」位元組的值。

>[!NOTE]
>
>如需有關此IIS選項的詳細資訊，請參閱 [正式檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

