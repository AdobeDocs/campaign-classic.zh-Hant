---
solution: Campaign Classic
product: campaign
title: 在 Windows 中移轉 Adobe Campaign 7
description: 在 Windows 中移轉 Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 1%

---


# 在 Windows 中移轉 Adobe Campaign 7{#migrating-in-windows-for-adobe-campaign}

## 一般過程{#general-procedure}

對於Windows，遷移步驟如下：

1. 停止服務：請參閱[服務停止](#service-stop)。
1. 備份資料庫：請參閱[備份資料庫和當前安裝](#back-up-the-database-and-the-current-installation)。
1. 移轉平台：請參閱[部署Adobe Campaign v7](#deploying-adobe-campaign-v7)。
1. 遷移重定向伺服器(IIS):請參閱[遷移重定向伺服器(IIS)](#migrating-the-redirection-server--iis-)。
1. 重新啟動服務：請參閱[重新啟動服務](#re-starting-the-services)。
1. 刪除及清除舊版Adobe Campaign:請參閱[刪除和清除Adobe Campaign舊版](#deleting-and-cleansing-adobe-campaign-previous-version)。

## 服務停止{#service-stop}

首先，在所有相關電腦上停止所有訪問資料庫的進程。

1. 必須停止使用重定向模組（**webmdl**&#x200B;服務）的所有伺服器。 對於IIS，運行以下命令：

   ```
   iisreset /stop
   ```

1. 必須使用以下命令停止&#x200B;**mta**&#x200B;模組及其子模組(**mtachild**):

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. 在所有伺服器上停止Adobe Campaign服務。 使用管理員權限登入並執行下列命令：

   ```
   net stop nlserver6
   ```

   如果您要從v5.11移轉，請執行下列命令：

   ```
   net stop nlserver5
   ```

1. 請確定Adobe Campaign服務已正確停止。 使用管理員權限登入並執行下列命令：

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   此時將顯示活動進程的清單及其ID(PID)。

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. 如果一或多個Adobe Campaign程式仍在作用中或幾分鐘後被封鎖，請停止它們。 使用管理員權限登入並執行下列命令：

   ```
   taskkill /IM nlserver* /T
   ```

1. 如果某些進程在幾分鐘後仍處於活動狀態，則可使用以下命令強制它們關閉：

   ```
   taskkill /F /IM nlserver* /T
   ```

## 備份資料庫和當前安裝{#back-up-the-database-and-the-current-installation}

此程式取決於您的Adobe Campaign舊版。

### 從Adobe Campaign 5.11 {#migrating-from-adobe-campaign-v5-11}版移轉

1. 備份Adobe Campaign資料庫。
1. 使用以下命令備份&#x200B;**Neolane v5**&#x200B;目錄：

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >為防患於未然，我們建議您壓縮&#x200B;**Neolane v5.back**&#x200B;資料夾，並將它儲存在伺服器以外的安全位置。

1. 在Windows服務管理控制台中，禁用5.11應用程式伺服器服務的自動啟動。 您也可以使用下列命令：

   ```
   sc config nlserver5 start= disabled
   ```

1. 編輯&#x200B;**config-`<instance name>`.xml**（在&#x200B;**Neolane v5中）。 back**&#x200B;資料夾)，以防止&#x200B;**mta**、**wfserver**、**stat**&#x200B;等。 服務自動啟動。 例如，將&#x200B;**autoStart**&#x200B;取代為&#x200B;**_autoStart**。

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### 從Adobe Campaign 6.02 {#migrating-from-adobe-campaign-v6-02}版移轉

1. 備份Adobe Campaign資料庫。
1. 使用以下命令備份&#x200B;**Neolane v6**&#x200B;目錄：

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >為防患於未然，我們建議您壓縮&#x200B;**Neolane v6.back**&#x200B;資料夾，並將它儲存在伺服器以外的安全位置。

1. 在Windows服務管理器中，停用6.02應用程式伺服器自動啟動。 您也可以使用下列命令：

   ```
   sc config nlserver6 start= disabled
   ```

1. 編輯&#x200B;**config-`<instance name>`.xml**（在&#x200B;**Neolane v6中）。 back**&#x200B;資料夾)，以防止&#x200B;**mta**、**wfserver**、**stat**&#x200B;等。 服務自動啟動。 例如，將&#x200B;**autoStart**&#x200B;取代為&#x200B;**_autoStart**。

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword" provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### 從Adobe Campaign 6.1 {#migrating-from-adobe-campaign-v6-1}版移轉

1. 備份Adobe Campaign資料庫。
1. 使用下列命令備份&#x200B;**Adobe Campaign v6**&#x200B;目錄：

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >為防患於未然，我們建議您壓縮&#x200B;**Adobe Campaign v6.back**&#x200B;資料夾，並將它儲存在伺服器以外的安全位置。

1. 在Windows服務管理控制台中，禁用6.11應用程式伺服器服務的自動啟動。 您也可以使用下列命令：

   ```
   sc config nlserver6 start= disabled
   ```

## 部署Adobe Campaign v7 {#deploying-adobe-campaign-v7}

部署Adobe Campaign需要兩個階段：

* 安裝組建版本v7:必須在每台伺服器上執行此操作。
* 升級後：必須在每個實例上啟動此命令。

若要部署Adobe Campaign，請套用下列步驟：

1. 執行&#x200B;**setup.exe**&#x200B;安裝檔案，以安裝最新的Adobe Campaign v7組建版本。 如需在Windows中安裝Adobe Campaign伺服器的詳細資訊，請參閱[本節](../../installation/using/installing-the-server.md)。

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7預設會安裝在&#x200B;**C:\Program Files\Adobe\Adobe Campaign v7**&#x200B;目錄中。

1. 若要讓用戶端主控台安裝程式可供使用，請將&#x200B;**setup-client-7.0.XXXX.exe**&#x200B;檔案複製至Adobe Campaign安裝目錄：**C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**。

   >[!NOTE]
   >
   >如需在Windows中安裝Adobe Campaign的詳細資訊，請參閱[本節](../../installation/using/installing-the-server.md)。

1. 使用下列命令啟動實例以便首次使用：

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >這些命令可讓您建立Adobe Campaign v7內部檔案系統：**conf**&#x200B;目錄（含&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;檔案）、**var**&#x200B;目錄等。

1. 透過&#x200B;**Neolane v5.back**、**Neolane v6.back**&#x200B;或&#x200B;**Adobe Campaign v6.back**&#x200B;備份檔案複製並貼上（覆寫）每個例項的設定檔案和子資料夾（視您要移轉的版本而定——請參閱[本節](#back-up-the-database-and-the-current-installation)）。
1. 根據要遷移的版本，執行以下命令：

   ```
   copy "Neolane v5.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v5.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v5.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Neolane v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Adobe Campaign v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Adobe Campaign v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Adobe Campaign v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   >[!IMPORTANT]
   >
   >對於上述第一個命令，請勿複製&#x200B;**config-default.xml**&#x200B;檔案。

1. 在Adobe Campaign v7的&#x200B;**serverConf.xml**&#x200B;和&#x200B;**config-default.xml**&#x200B;檔案中，套用您在Adobe Campaign舊版中的特定設定。 對於&#x200B;**serverConf.xml**&#x200B;檔案，請使用&#x200B;**Neolane v5/conf/serverConf.xml.diff**、**Neolane v6/conf/serverConf.xml.diff**&#x200B;或&#x200B;**Adobe Campaign v6/conf/serverConf.xml.diff**&#x200B;檔案。

   >[!NOTE]
   >
   >將Adobe Campaign舊版的組態報告至Adobe Campaign v7時，請確定實體目錄的路徑會導向Adobe Campaign v7（而非Neolane v5、Neolane v6或Adobe Campaign v6）。

1. 使用下列命令重新載入Adobe Campaign v7設定：

   ```
   nlserver config -reload
   ```

1. 使用以下命令啟動postupgrade進程：

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>請勿啟動Adobe Campaign服務：需要對IIS進行一些更改。

## 遷移重定向伺服器(IIS){#migrating-the-redirection-server--iis-}

此時，必須停止IIS伺服器。 請參閱[服務停止](#service-stop)。

1. 開啟&#x200B;**Internet Information Services(IIS)Manager**&#x200B;控制台。
1. 變更Adobe Campaign舊版網站的系結（監聽埠）:

   * 以滑鼠右鍵按一下Adobe Campaign舊版網站，然後選取&#x200B;**[!UICONTROL Edit bindings]**。
   * 對於每種監聽埠類型（**[!UICONTROL http]**&#x200B;和／或&#x200B;**[!UICONTROL https]**），選擇相應的行並按一下&#x200B;**[!UICONTROL Edit]**。
   * 輸入不同的埠。 預設情況下，http的監聽埠為80,https為443。 檢查新埠是否可用。

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >如果您的IIS伺服器包含數個使用進階組態（共用埠和不同IP位址）的Adobe Campaign網站，請聯絡您的管理員。

1. 建立Adobe Campaign v7的新網站：

   * 按一下右鍵&#x200B;**[!UICONTROL Sites]**&#x200B;資料夾，然後選擇&#x200B;**[!UICONTROL Add Web Site...]**。

      ![](assets/_migration_iis_4.png)

   * 輸入網站名稱，例如&#x200B;**Adobe Campaign v7**。
   * 不使用網站基本目錄的存取路徑，但必須輸入&#x200B;**[!UICONTROL Physical access path]**&#x200B;欄位。 輸入預設的IIS訪問路徑：**C:\inetpub\wwwroot**。
   * 按一下&#x200B;**[!UICONTROL Connect as...]**&#x200B;作為按鈕，並確保選中&#x200B;**[!UICONTROL Application user]**&#x200B;選項。
   * 您可以在&#x200B;**[!UICONTROL IP address]**&#x200B;和&#x200B;**[!UICONTROL Port]**&#x200B;欄位中保留預設值。 如果要使用其他值，請確定IP地址和／或埠可用。
   * 選中&#x200B;**[!UICONTROL Start Web site immediately]**&#x200B;框。

      ![](assets/_migration_iis_5_7.png)

1. 執行&#x200B;**iis_neolane_setup.vbs**&#x200B;指令碼，以自動設定Adobe Campaign伺服器在先前建立的虛擬目錄上所使用的資源。

   * 此檔案位於&#x200B;**`[Adobe Campaign v7]`\conf**&#x200B;目錄中，其中&#x200B;**`[Adobe Campaign v7]`**&#x200B;是Adobe Campaign安裝目錄的存取路徑。 用於執行指令碼的命令如下（對於管理員）:

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
      cscript iis_neolane_setup.vbs
      ```

   * 按一下&#x200B;**[!UICONTROL OK]**&#x200B;確認指令碼執行。

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * 輸入先前為Adobe Campaign v7建立的網站編號，然後按一下&#x200B;**[!UICONTROL OK]**。

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * 應顯示確認消息：

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * 在&#x200B;**[!UICONTROL Content view]**&#x200B;標籤中，請確定網站設定已正確設定Adobe Campaign資源：

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >如果未顯示樹結構，請重新啟動IIS。
      >
      >[本節](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server)將詳細介紹以下IIS配置步驟。

## 安全區{#security-zones}

如果您要從v6.02或更舊版本移轉，則必須先設定安全區，才能啟動服務。 有關詳細資訊，請參閱[Security](../../migration/using/general-configurations.md#security)。

## 重新啟動服務{#re-starting-the-services}

在下列每部伺服器上啟動IIS和Adobe Campaign服務：

1. 追蹤和重新導向伺服器。
1. 中間來源伺服器.
1. 行銷伺服器。

在執行下一步之前，請對新安裝執行完整測試，確保沒有回歸，並遵循[一般設定](../../migration/using/general-configurations.md)一節中的所有建議，確保一切正常運作。

## 刪除和清除Adobe Campaign舊版{#deleting-and-cleansing-adobe-campaign-previous-version}

此程式取決於您的Adobe Campaign舊版。

### Adobe Campaign v5 {#adobe-campaign-v5}

在刪除及清除Adobe Campaign v5安裝之前，您必須套用下列建議：

* 讓功能團隊對新安裝進行完整檢查。
* 只有在您確定不需要回溯時，才能解除安裝Adobe Campaign v5。

1. 在IIS中，刪除&#x200B;**Neolane v5**&#x200B;網站，然後刪除&#x200B;**Neolane v5**&#x200B;應用程式池。
1. 將&#x200B;**Neolane v5.back**&#x200B;資料夾重新命名為&#x200B;**Neolane v5**。
1. 使用「新增／移除元件」精靈，解除安裝Adobe Campaign v5。

   ![](assets/migration_wizard_2.png)

1. 使用以下命令刪除&#x200B;**nlserver5** Windows服務：

   ```
   sc delete nlserver5
   ```

1. 重新啟動伺服器。

### Adobe Campaign v6.02 {#adobe-campaign-v6-02}

在刪除並清除Adobe Campaign 6.02版安裝之前，您必須套用下列建議：

* 讓功能團隊對新安裝進行完整檢查。
* 只有在您確定不需要回溯時，才能解除安裝Adobe Campaign 6.02版。

1. 在IIS中，刪除&#x200B;**Neolane v6**&#x200B;網站，然後刪除&#x200B;**Neolane v6**&#x200B;應用程式池。
1. 將&#x200B;**Neolane v6.back**&#x200B;資料夾重新命名為&#x200B;**Neolane v6**。
1. 使用「新增／移除元件」精靈，解除安裝Adobe Campaign v6.02。

   ![](assets/migration_wizard_2.png)

1. 重新啟動伺服器。

### Adobe Campaign v6.1 {#adobe-campaign-v6-1}

在刪除並清除Adobe Campaign v6安裝之前，您必須套用下列建議：

* 讓功能團隊對新安裝進行完整檢查。
* 只有在您確定不需要回溯時，才能解除安裝Adobe Campaign v6。

1. 在IIS中，請刪除&#x200B;**Adobe Campaign v6**&#x200B;網站，然後刪除&#x200B;**Adobe Campaign v6**&#x200B;應用程式集。
1. 將&#x200B;**Adobe Campaign v6.back**&#x200B;檔案夾重新命名為&#x200B;**Adobe Campaign v6**。
1. 使用「新增／移除元件」精靈，解除安裝Adobe Campaign v6。

   ![](assets/migration_wizard_2.png)

1. 重新啟動伺服器。

