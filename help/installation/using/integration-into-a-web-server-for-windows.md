---
title: 與Windows版Web伺服器整合
seo-title: 與Windows版Web伺服器整合
description: 與Windows版Web伺服器整合
seo-description: null
page-status-flag: never-activated
uuid: a5042221-44fe-46a6-9322-288b108396e2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: a4f2ae0e-e631-4ab6-934e-8298e4ce6f2c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: abddb3cdfcee9e41cab2e7e662d5bfd5d53d6f7e

---


# 與Windows版Web伺服器整合{#integration-into-a-web-server-for-windows}

Adobe Campaign包含Apache Tomcat，可透過HTTP（和SOAP）在應用程式伺服器中當做入口點。

您可以使用此整合的Tomcat伺服器來服務HTTP請求。

在本例中：

* 預設監聽埠為8080。 要更改它，請參 [閱Configuring Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat)。
* 然後，用戶端主控台會使用 [https:// `<computer>`:8080等URL連線](https://machine:8080)。

不過，出於安全性和管理原因，我們建議使用專用的Web伺服器作為HTTP流量的主要入口點，因為執行Adobe Campaign的電腦在網際網路上公開，而且您想要在網路外開啟主控台的存取權。

Web伺服器也可讓您使用HTTP通訊協定來保證資料的機密性。

同樣地，當您想要使用追蹤功能時，必須使用Web伺服器，此功能僅能做為Web伺服器擴充模組使用。

>[!NOTE]
>
>如果您不使用追蹤功能，則可執行Apache或IIS的標準安裝，並重新導向至促銷活動。 不需要追蹤Web伺服器擴充模組。

## 配置IIS web伺服器 {#configuring-the-iis-web-server}

IIS web伺服器的配置過程大多是圖形化的。 它涉及使用網站（已建立或待建立）來存取Adobe Campaign伺服器的資源：Java(.jsp)檔案、樣式表(.css、.xsl)、影像(.png)、用於重新導向的ISAPI DLL等。

IIS 7中的以下章節詳細配置。 IIS8的組態基本相同。

如果您的電腦上尚未安裝Web IIS伺服器，則可以通過菜單進行安 **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** 裝。

在IIS 7中，除了標準服務外，您還需要安裝ISAPI擴充功能和ISAPI篩選器。

![](assets/s_ncs_install_iis7_isapi.png)

### 配置步驟 {#configuration-steps}

套用下列設定步驟：

1. 通過菜單開啟IIS **[!UICONTROL Control panel > Administrative tools > Services]** 。
1. 根據網路參數（TCP連線埠、DNS主機、IP位址），建立並設定網站（例如Adobe Campaign）。

   ![](assets/s_ncs_install_iis7_add_site.png)

   您至少必須指定站點的名稱和到虛擬目錄的訪問路徑。 由於不使用用於訪問「網站」目錄的路徑，因此您可以使用以下目錄。

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. VBS **** 指令碼可讓您在我們剛建立的虛擬目錄上自動設定Adobe Campaign伺服器使用的資源。 若要啟動它，請連按兩下資料 **夾中的iis_neolane_setup.vbs** 檔案，其中 `[INSTALL]\tomcat-7\conf``[INSTALL]` 是存取Adobe Campaign安裝資料夾的路徑。

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >在安裝Windows伺服器2008/IIS7時，您必須以管理員身份登錄才能運行VBS指令碼或以管理員身份執行指令碼。

   如果 **[!UICONTROL OK]** Web伺服器是用作追蹤重新導向伺服器，請按一下，否則請按一下 **[!UICONTROL Cancel]**。

   當網站伺服器上已設定多個網站時，會顯示一個中介頁面，以指定安裝套用至哪個網站：輸入連結至網站的編號，然後按一下 **[!UICONTROL OK]**。

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   應顯示確認消息：

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. 在標籤 **[!UICONTROL Content View]** 中，請確定網站已正確設定Adobe Campaign資源：

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   如果未顯示樹，請重新啟動IIS。

### 管理權限 {#managing-rights}

您接著必須設定ISAPI DLL和Adobe Campaign安裝目錄中資源的安全性設定。

若要這麼做，請套用下列步驟：

1. 選擇該 **[!UICONTROL Features View]** 頁籤，然後按兩下「 **Authentication** （驗證）」連結。

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. 在網站 **的「目錄安全** 」標籤中，請確定已啟用匿名存取。 如有必要，請按一 **[!UICONTROL Edit]** 下連結以變更設定。

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### 啟動Web伺服器並測試配置 {#launching-the-web-server-and-testing-the-configuration}

您現在必須測試此設定是否正確。

若要這麼做，請套用下列程式：

1. 使用iisreset命令行重新啟動 **IIS** 伺服器。
1. 將下列URL插入網頁瀏覽器，以測試追蹤模組：

   ```
   https://<computer>/r/test
   ```

   瀏覽器應顯示下列回應：

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

要測試重定向模組是否存在，請運行以下命令行：

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

1. 按一下圖示，編輯Adobe Campaign網站的ISAPI篩 **[!UICONTROL Driver mapping]** 選。
1. 檢查ISAPI篩選器的內容：

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## 其他配置 {#additional-configurations}

### 變更上傳檔案大小限制 {#changing-the-upload-file-size-limit}

配置IIS web伺服器時，將自動為上載到伺服器的設定檔案設定大約28 MB的限制。

這可能會對Adobe Campaign產生影響，尤其是如果您想要上傳超過此限制的檔案。

例如，如果您在工作流中使用「 **Data loading(file)** type」(資料載入(file)類型)活動來匯入50 MB的檔案，則錯誤會導致工作流程無法正確執行。

在這種情況下，您必須提高此限制：

1. 通過菜單開啟IIS **[!UICONTROL Start > (Control panel) > Administration tools]** 。
1. 在「連 **線** 」窗格中，選取為您的Adobe安裝所建立的網站，然後按兩下主窗格中 **的「請求篩選** 」。
1. 在「動 **作** 」窗格中，選取「編 **輯功能設定」** ，以便能夠編輯「最大授權內容大小（位元組）」欄 **位中的值** 。

   例如，若要授權上傳50 MB的檔案，您必須指定超過&quot;52428800&quot;位元組的值。

>[!NOTE]
>
>有關此IIS選項的更多資訊，請參閱官方文檔的「How To」 [部分](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)。

### 配置http錯誤消息顯示 {#configuring-http-error-message-display}

如果您使用6.1版IIS伺服器，由於訊息中顯示不想要的HTML程式碼，所產生的錯誤訊息可能難以讀取。

若要修正此問題並正確顯示錯誤，請套用下列設定：

1. 通過菜單開啟IIS **[!UICONTROL Start > Control Panel > Administrative tools]** 。
1. 在「連 **線** 」窗格中，選取為您的Adobe Campaign安裝所建立的網站，然後在主窗格中按兩下「 **設定編輯器** 」。
1. 在「區 **域** 」下拉式清單中，選 **取system.webServer** > **httpErrors**。
1. 在現有 **響應行** ，選擇 **「傳遞** 」值。

![](assets/ins_iis_httperrors.png)

