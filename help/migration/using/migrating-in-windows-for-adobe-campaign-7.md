---
product: campaign
title: 將Microsoft Windows平台移轉至Adobe Campaign v7
description: 瞭解如何將Microsoft Windows平台移轉至Adobe Campaign v7
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
hide: true
hidefromtoc: true
exl-id: 3743d018-3316-4ce3-ae1c-25760aaf5785
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---

# 將Microsoft Windows平台移轉至Campaign v7{#migrating-in-windows-for-adobe-campaign}



若為Microsoft Windows環境，移轉步驟如下：

1. 停止所有服務 —  [瞭解更多](#service-stop).
1. 備份您的資料庫 —  [瞭解更多](#back-up-the-database).
1. 遷移平台 —  [瞭解更多](#deploying-adobe-campaign-v7).
1. 移轉重新導向伺服器(IIS) - [瞭解更多](#migrating-the-redirection-server--iis-).
1. 重新啟動服務 —  [瞭解更多](#re-starting-the-services).
1. 刪除並清除舊版Adobe Campaign - [瞭解更多](#deleting-and-cleansing-adobe-campaign-previous-version).

## 服務停止 {#service-stop}

首先，停止在所有相關電腦上存取資料庫的所有程式。

1. 所有使用重新導向模組的伺服器(**webmdl** service)必須停止。 對於IIS，請執行以下命令：

   ```
   iisreset /stop
   ```

1. 此 **mta** 模組及其子模組(**matachild**)必須使用下列命令停止：

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. 停止所有伺服器上的Adobe Campaign服務。 以管理員許可權登入，然後執行下列命令：

   ```
   net stop nlserver6
   ```

<!--

   If you are migrating from v5.11, run the following command:

   ```
   net stop nlserver5
   ```

-->

1. 對於每個伺服器，請確定Adobe Campaign服務已正確停止。 以管理員許可權登入，然後執行下列命令：

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   此時會顯示作用中處理序的清單及其ID (PID)。

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. 如果一或多個Adobe Campaign程式在幾分鐘後仍處於作用中或封鎖狀態，請將其終止。 以管理員許可權登入，然後執行下列命令：

   ```
   taskkill /IM nlserver* /T
   ```

1. 如果某些程式在幾分鐘後仍在使用中，您可以使用命令強制關閉它們：

   ```
   taskkill /F /IM nlserver* /T
   ```

## 備份Campaign資料庫 {#back-up-the-database}

以下是備份Adobe Campaign v6.1的程式。

<!--

### For Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v5** directory using the following command:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v5.back** folder and save it elsewhere in a safe location other than the server.

1. In the windows service management console, disable the automatic startup of the 5.11 application server service. You can also use the following command:

   ```
   sc config nlserver5 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v5. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

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

-->

<!--
### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v6** directory using the following command:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v6.back** folder and save it elsewhere in a safe location other than the server.

1. In the Windows service manager, deactivate the 6.02 application server automatic startup. You can also use the following command:

   ```
   sc config nlserver6 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v6. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

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

-->

1. 備份Adobe Campaign資料庫。
1. 備份 **Adobe Campaign v6** 目錄，使用下列命令：

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >為謹慎起見，建議您壓縮 **Adobe Campaign v6.back** 資料夾並將其儲存在伺服器以外的安全位置。

1. 在Windows服務管理主控台中，停用6.11應用程式伺服器服務的自動啟動。 您也可以使用下列指令：

   ```
   sc config nlserver6 start= disabled
   ```

## 部署Adobe Campaign v7 {#deploying-adobe-campaign-v7}

部署Adobe Campaign需要兩個階段：

* 安裝組建v7：必須在每個伺服器上執行此操作。
* 升級後：必須在每個執行個體上啟動此命令。

若要部署Adobe Campaign，請套用下列步驟：

1. Adobe Campaign執行 **setup.exe** 安裝檔案。 如需在Windows中安裝Adobe Campaign伺服器的詳細資訊，請參閱 [本節](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7預設會安裝在中 **C:\Program Files\Adobe\Adobe Campaign v7** 目錄。

1. 若要讓使用者端主控台安裝程式可供使用，請複製 **setup-client-7.0.XXXX.exe** 檔案放入Adobe Campaign安裝目錄： **C:\Program Files\Adobe\Adobe行銷活動v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >如需在Windows中安裝Adobe Campaign的詳細資訊，請參閱 [本節](../../installation/using/installing-the-server.md).

1. 使用下列命令啟動第一次使用的例證：

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >這些命令可讓您建立Adobe Campaign v7內部檔案系統： **conf** 目錄(使用 **config-default.xml** 和 **serverConf.xml** 檔案)， **var** 目錄等。

1. 複製並貼上（覆寫）每個執行個體的組態檔案和子資料夾，方法是透過 **Neolane v5.back**， **Neolane v6.back** 或 **Adobe Campaign v6.back** 備份檔案(視您要移轉的來源版本而定 — 請參閱 [本節](#back-up-the-database-and-the-current-installation))。
1. 根據您要移轉的版本，執行以下命令：

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
   >對於上述第一個指令，請勿複製 **config-default.xml** 檔案。

1. 在 **serverConf.xml** 和 **config-default.xml** Adobe Campaign v7的檔案，套用您在Adobe Campaign舊版中擁有的特定設定。 對於 **serverConf.xml** 檔案，使用 **Neolane v5/conf/serverConf.xml.diff**， **Neolane v6/conf/serverConf.xml.diff** 或 **Adobe Campaign v6/conf/serverConf.xml.diff** 檔案。

   >[!NOTE]
   >
   >報告從Adobe Campaign舊版到Adobe Campaign v7的配置時，請確保實體目錄的路徑指向Adobe Campaign v7 (而不是Neolane v5、Neolane v6或Adobe Campaign v6)。

1. 使用以下命令重新載入Adobe Campaign v7設定：

   ```
   nlserver config -reload
   ```

1. 使用以下命令啟動升級後程式：

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>尚未啟動Adobe Campaign服務：需要在IIS上進行一些變更。

## 移轉重新導向伺服器 {#migrating-the-redirection-server--iis-}

在這個階段，必須停止IIS伺服器。 請參閱 [服務停止](#service-stop).

1. 開啟 **網際網路資訊服務(IIS)管理員** 主控台。
1. 變更用於Adobe Campaign舊版的網站繫結（監聽連線埠）：

   * 以滑鼠右鍵按一下用於Adobe Campaign舊版的網站，然後選取 **[!UICONTROL Edit bindings]**.
   * 對於每種監聽連線埠型別(**[!UICONTROL http]** 和/或 **[!UICONTROL https]**)，選取適當的行並按一下 **[!UICONTROL Edit]**.
   * 輸入不同的連線埠。 依預設，http的監聽連線埠是80，https是443。 檢查新連線埠是否可用。

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >如果您的IIS伺服器包含數個使用進階設定（共用連線埠和不同的IP位址）的Adobe Campaign網站，請聯絡您的管理員。

1. 為Adobe Campaign v7建立新網站：

   * 以滑鼠右鍵按一下 **[!UICONTROL Sites]** 資料夾並選取 **[!UICONTROL Add Web Site...]**.

      ![](assets/_migration_iis_4.png)

   * 輸入網站名稱， **Adobe Campaign v7** 例如。
   * 不會使用網站基本目錄的存取路徑，但會使用 **[!UICONTROL Physical access path]** 欄位必須輸入。 輸入預設的IIS存取路徑： **C:\inetpub\wwwroot**.
   * 按一下 **[!UICONTROL Connect as...]** 作為按鈕，並確定 **[!UICONTROL Application user]** 選項時才會選擇此選項。
   * 您可以將預設值保留在 **[!UICONTROL IP address]** 和 **[!UICONTROL Port]** 欄位。 如果您想使用其他值，請確定IP位址和/或連線埠可用。
   * 檢查 **[!UICONTROL Start Web site immediately]** 方塊。

      ![](assets/_migration_iis_5_7.png)

1. 執行 **iis_neolane_setup.vbs** 指令碼，可自動在先前建立的虛擬目錄上設定Adobe Campaign伺服器使用的資源。

   * 此檔案位於 **`[Adobe Campaign v7]`\conf** 目錄，其中 **`[Adobe Campaign v7]`** 是Adobe Campaign安裝目錄的存取路徑。 執行指令碼的命令如下（適用於管理員）：

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
      cscript iis_neolane_setup.vbs
      ```

   * 按一下 **[!UICONTROL OK]** 以確認指令碼執行。

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * 輸入先前為Adobe Campaign v7建立的網站編號，然後按一下 **[!UICONTROL OK]**.

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * 應會顯示確認訊息：

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * 在 **[!UICONTROL Content view]** 索引標籤中，確認網站設定已正確設定Adobe Campaign資源：

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >如果未顯示樹狀結構，請重新啟動IIS。
      >
      >下列IIS設定步驟已詳載於 [本節](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

<!--
## Security zones {#security-zones}

If you are migrating from v6.02 or earlier, you must configure your security zones before starting services. [Learn more](../../migration/using/general-configurations.md#security)
-->

## 重新啟動服務 {#re-starting-the-services}

在下列各伺服器上啟動IIS和Adobe Campaign服務：

1. 追蹤和重新導向伺服器。
1. 中間來源伺服器.
1. 行銷伺服器。

繼續進行下一個步驟之前，請對新安裝執行完整測試，確認沒有回歸，且一切正常。

## 刪除先前版本 {#deleting-and-cleansing-adobe-campaign-previous-version}

以下是刪除Adobe Campaign v6.1的程式。

<!--

### For Adobe Campaign v5 {#adobe-campaign-v5}

Before you delete and cleanse the Adobe Campaign v5 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v5 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v5** website, then the **Neolane v5** application pool. 
1. Rename the **Neolane v5.back** folder as **Neolane v5**.
1. Uninstall Adobe Campaign v5 using the Add/remove components wizard. 

   ![](assets/migration_wizard_2.png)

1. Delete the **nlserver5** Windows service using the following command:

   ```
   sc delete nlserver5
   ```

1. Re-start the server.

### For Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Before you delete and cleanse the Adobe Campaign v6.02 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v6.02 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v6** website, then the **Neolane v6** application pool. 
1. Rename the **Neolane v6.back** folder as **Neolane v6**.
1. Uninstall Adobe Campaign v6.02 using the Add/remove components wizard. 

   ![](assets/migration_wizard_2.png)

1. Re-start the server.

-->

在刪除及清除Adobe Campaign v6安裝之前，您必須套用下列建議：

* 讓功能團隊對新安裝執行完整檢查。
* 只有在您確定不需要復原後，才能解除安裝Adobe Campaign v6。

1. 在IIS中，刪除 **Adobe Campaign v6** 網站，然後 **Adobe Campaign v6** 應用程式集區。
1. 重新命名 **Adobe Campaign v6.back** 資料夾為 **Adobe Campaign v6**.
1. 使用「新增/移除元件」精靈解除安裝Adobe Campaign v6。

   ![](assets/migration_wizard_2.png)

1. 重新啟動伺服器。
