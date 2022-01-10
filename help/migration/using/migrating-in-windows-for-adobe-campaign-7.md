---
product: campaign
title: 將Microsoft Windows平台移轉至Adobe Campaign v7
description: 了解如何將Microsoft Windows平台移轉至Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 3743d018-3316-4ce3-ae1c-25760aaf5785
source-git-commit: 63aca25a8d1ae24ef83849b35a44d1b37cfa5e96
workflow-type: tm+mt
source-wordcount: '1504'
ht-degree: 0%

---

# 將Microsoft Windows平台移轉至Campaign v7{#migrating-in-windows-for-adobe-campaign}

![](../../assets/v7-only.svg)

對於Microsoft Windows環境，移轉步驟如下：

1. 停止所有服務 —  [深入了解](#service-stop).
1. 備份資料庫 —  [深入了解](#back-up-the-database).
1. 移轉平台 —  [深入了解](#deploying-adobe-campaign-v7).
1. 遷移重定向伺服器(IIS)- [深入了解](#migrating-the-redirection-server--iis-).
1. 重新啟動服務 —  [深入了解](#re-starting-the-services).
1. 刪除並清除舊版Adobe Campaign - [深入了解](#deleting-and-cleansing-adobe-campaign-previous-version).

## 服務停止 {#service-stop}

首先，停止所有相關電腦上具有資料庫訪問權限的所有進程。

1. 使用重定向模組的所有伺服器(**webmdl** 服務)。 對於IIS，運行以下命令：

   ```
   iisreset /stop
   ```

1. 此 **mta** 模組及其子模組(**mtachild**)，則必須使用下列命令來停止：

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. 停止所有伺服器上的Adobe Campaign服務。 使用管理員權限登錄並運行以下命令：

   ```
   net stop nlserver6
   ```

   如果要從v5.11遷移，請運行以下命令：

   ```
   net stop nlserver5
   ```

1. 對於每個伺服器，請確定已正確停止Adobe Campaign服務。 使用管理員權限登錄並運行以下命令：

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   此時會顯示作用中程式的清單及其ID(PID)。

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. 如果一或多個Adobe Campaign程式在幾分鐘後仍處於作用中或封鎖狀態，請終止。 使用管理員權限登錄並運行以下命令：

   ```
   taskkill /IM nlserver* /T
   ```

1. 如果某些進程在幾分鐘後仍處於活動狀態，則可以使用命令強制它們關閉：

   ```
   taskkill /F /IM nlserver* /T
   ```

## 備份您的Campaign資料庫 {#back-up-the-database}

程式取決於您的Adobe Campaign舊版。

### 適用於Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. 備份Adobe Campaign資料庫。
1. 備份 **Neolane v5** 目錄（使用以下命令）:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >為了防患於未然，建議您將 **Neolane v5.back** 資料夾，並將其儲存在伺服器以外的安全位置。

1. 在windows服務管理控制台中，禁用5.11應用程式伺服器服務的自動啟動。 您也可以使用下列命令：

   ```
   sc config nlserver5 start= disabled
   ```

1. 編輯 **config-`<instance name>`.xml** (在 **Neolane v5。 back** 資料夾)，以防止 **mta**, **wfserver**, **stat**、等 服務自動啟動。 例如，取代 **autoStart** with **_autoStart**.

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

### 適用於Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. 備份Adobe Campaign資料庫。
1. 備份 **Neolane v6** 目錄（使用以下命令）:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >為了防患於未然，建議您將 **Neolane v6.back** 資料夾，並將其儲存在伺服器以外的安全位置。

1. 在Windows服務管理器中，停用6.02應用程式伺服器自動啟動。 您也可以使用下列命令：

   ```
   sc config nlserver6 start= disabled
   ```

1. 編輯 **config-`<instance name>`.xml** (在 **Neolane v6。 back** 資料夾)，以防止 **mta**, **wfserver**, **stat**、等 服務自動啟動。 例如，取代 **autoStart** with **_autoStart**.

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

### 適用於Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. 備份Adobe Campaign資料庫。
1. 備份 **Adobe Campaign v6** 目錄（使用以下命令）:

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >為了防患於未然，建議您將 **Adobe Campaign v6.back** 資料夾，並將其儲存在伺服器以外的安全位置。

1. 在windows服務管理控制台中，禁用6.11應用程式伺服器服務的自動啟動。 您也可以使用下列命令：

   ```
   sc config nlserver6 start= disabled
   ```

## 部署Adobe Campaign v7 {#deploying-adobe-campaign-v7}

部署Adobe Campaign需要兩個階段：

* 安裝組建v7:必須在每個伺服器上執行此操作。
* 升級後：必須在每個實例上啟動此命令。

若要部署Adobe Campaign，請套用下列步驟：

1. 執行 **setup.exe** 安裝檔案。 有關在Windows中安裝Adobe Campaign伺服器的詳細資訊，請參閱 [本節](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7預設會安裝在 **C:\Program Files\Adobe\Adobe Campaign v7** 目錄。

1. 要使客戶端控制台安裝程式可用，請複製 **setup-client-7.0.XXXX.exe** 檔案放入Adobe Campaign安裝目錄： **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >有關在Windows中安裝Adobe Campaign的詳細資訊，請參閱 [本節](../../installation/using/installing-the-server.md).

1. 啟動實例以便首次與以下命令一起使用：

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >以下命令可讓您建立Adobe Campaign v7內部檔案系統： **conf** 目錄(使用 **config-default.xml** 和 **serverConf.xml** 檔案), **var** 目錄等。

1. 複製並貼上（覆寫）每個執行個體的設定檔案和子資料夾，透過 **Neolane v5.back**, **Neolane v6.back** 或 **Adobe Campaign v6.back** 備份檔案(取決於您要從中遷移的版本 — 請參閱 [本節](#back-up-the-database-and-the-current-installation))。
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
   >對於上述第一個命令，請勿複製 **config-default.xml** 檔案。

1. 在 **serverConf.xml** 和 **config-default.xml** 檔案中的Adobe Campaign v7，則套用您在Adobe Campaign舊版中的特定設定。 若 **serverConf.xml** 檔案，使用 **Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** 或 **Adobe Campaign v6/conf/serverConf.xml.diff** 檔案。

   >[!NOTE]
   >
   >在將配置從Adobe Campaign舊版報告到Adobe Campaign v7時，請確保指向物理目錄的路徑導向Adobe Campaign v7(而不是Neolane v5、Neolane v6或Adobe Campaign v6)。

1. 使用下列命令重新載入Adobe Campaign v7設定：

   ```
   nlserver config -reload
   ```

1. 使用以下命令啟動升級後進程：

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>尚未啟動Adobe Campaign服務：需要對IIS進行一些更改。

## 遷移重定向伺服器 {#migrating-the-redirection-server--iis-}

此時，必須停止IIS伺服器。 請參閱 [服務停止](#service-stop).

1. 開啟 **Internet資訊服務(IIS)管理器** 控制台。
1. 更改用於Adobe Campaign舊版的站點的綁定（偵聽埠）:

   * 以滑鼠右鍵按一下Adobe Campaign舊版所用的網站，然後選取 **[!UICONTROL Edit bindings]**.
   * 對於每種類型的監聽埠(**[!UICONTROL http]** 和/或 **[!UICONTROL https]**)，選取適當的行，然後按一下 **[!UICONTROL Edit]**.
   * 輸入其他埠。 預設情況下，http為監聽埠80,https為443。 檢查新埠是否可用。

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >如果您的IIS伺服器包含多個具有高級配置（共用埠和不同IP地址）的Adobe Campaign網站，請與管理員聯繫。

1. 建立Adobe Campaign v7的新網站：

   * 以滑鼠右鍵按一下 **[!UICONTROL Sites]** 資料夾和選取 **[!UICONTROL Add Web Site...]**.

      ![](assets/_migration_iis_4.png)

   * 輸入網站名稱， **Adobe Campaign v7** 例如。
   * 未使用網站基本目錄的存取路徑，但會使用 **[!UICONTROL Physical access path]** 欄位。 輸入預設的IIS訪問路徑： **C:\inetpub\wwwroot**.
   * 按一下 **[!UICONTROL Connect as...]** as按鈕，確定 **[!UICONTROL Application user]** 選項。
   * 您可以將預設值保留在 **[!UICONTROL IP address]** 和 **[!UICONTROL Port]** 欄位。 如果您想使用其他值，請確定IP位址和/或連接埠可用。
   * 檢查 **[!UICONTROL Start Web site immediately]** 框。

      ![](assets/_migration_iis_5_7.png)

1. 執行 **iis_neolane_setup.vbs** 指令碼，用於自動配置先前建立的虛擬目錄上的Adobe Campaign伺服器所使用的資源。

   * 在 **`[Adobe Campaign v7]`\conf** 目錄，其中 **`[Adobe Campaign v7]`** 是Adobe Campaign安裝目錄的存取路徑。 用於執行指令碼的命令如下（適用於管理員）:

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
      cscript iis_neolane_setup.vbs
      ```

   * 按一下 **[!UICONTROL OK]** 確認指令碼執行。

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * 輸入先前為Adobe Campaign v7建立的網站編號，然後按一下 **[!UICONTROL OK]**.

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * 應會出現確認訊息：

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * 在 **[!UICONTROL Content view]** 標籤，確認網站設定已正確設定Adobe Campaign資源：

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >如果未顯示樹結構，請重新啟動IIS。
      >
      >以下IIS配置步驟在 [本節](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

## 安全區域 {#security-zones}

如果您要從v6.02或更舊版本移轉，則必須先配置安全區域，才能啟動服務。 [了解更多](../../migration/using/general-configurations.md#security)

## 重新啟動服務 {#re-starting-the-services}

在以下每台伺服器上啟動IIS和Adobe Campaign服務：

1. 跟蹤和重定向伺服器。
1. 中間來源伺服器.
1. 行銷伺服器。

繼續進行下一步之前，請對新安裝執行完整測試，確定沒有回歸，而且所有項目都能依照 [本頁](../../migration/using/general-configurations.md).

## 刪除舊版 {#deleting-and-cleansing-adobe-campaign-previous-version}

程式取決於您的Adobe Campaign舊版。

### 適用於Adobe Campaign v5 {#adobe-campaign-v5}

在刪除及清除Adobe Campaign v5安裝之前，您必須套用下列建議：

* 請功能團隊對新安裝執行完整檢查。
* 只有在您確定不需要回滾時，才解除安裝Adobe Campaign v5。

1. 在IIS中，刪除 **Neolane v5** 網站，然後 **Neolane v5** 應用程式池。
1. 重新命名 **Neolane v5.back** 資料夾 **Neolane v5**.
1. 使用「新增/移除元件」精靈，解除安裝Adobe Campaign v5。

   ![](assets/migration_wizard_2.png)

1. 刪除 **nlserver5** 使用以下命令的Windows服務：

   ```
   sc delete nlserver5
   ```

1. 重新啟動伺服器。

### 適用於Adobe Campaign v6.02 {#adobe-campaign-v6-02}

刪除並清除Adobe Campaign v6.02安裝前，您必須套用下列建議：

* 請功能團隊對新安裝執行完整檢查。
* 只有在您確定不需要回滾時，才能解除安裝Adobe Campaign v6.02。

1. 在IIS中，刪除 **Neolane v6** 網站，然後 **Neolane v6** 應用程式池。
1. 重新命名 **Neolane v6.back** 資料夾 **Neolane v6**.
1. 使用「新增/移除元件」精靈，解除安裝Adobe Campaign v6.02。

   ![](assets/migration_wizard_2.png)

1. 重新啟動伺服器。

### 適用於Adobe Campaign v6.1 {#adobe-campaign-v6-1}

刪除並清除Adobe Campaign v6安裝前，您必須套用下列建議：

* 請功能團隊對新安裝執行完整檢查。
* 只有在您確定不需要回滾時，才能解除安裝Adobe Campaign v6。

1. 在IIS中，刪除 **Adobe Campaign v6** 網站，然後 **Adobe Campaign v6** 應用程式池。
1. 重新命名 **Adobe Campaign v6.back** 資料夾 **Adobe Campaign v6**.
1. 使用「新增/移除元件」精靈，解除安裝Adobe Campaign v6。

   ![](assets/migration_wizard_2.png)

1. 重新啟動伺服器。
