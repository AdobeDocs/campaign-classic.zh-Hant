---
product: campaign
title: 升級至新的組建
description: 瞭解升級至新組建版本的技術步驟
feature: Monitoring, Upgrade
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 1%

---

# 升級至新的組建（內部部署）{#upgrading}



在開始升級程式之前，請先決定並確認要升級至的Adobe Campaign版本，並參閱 [發行說明](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* Adobe強烈建議您在更新前先對每個執行個體進行資料庫備份。 如需詳細資訊，請參閱[本區段](../../production/using/backup.md)。
>* 若要執行升級，請確定您有存取執行個體和記錄的能力和許可權。
>* 讀出 [本節](../../installation/using/general-architecture.md) 和 [組建版本升級](https://helpx.adobe.com/tw/campaign/kb/acc-build-upgrade.html) 開始前的章節。
>

## Windows {#in-windows}

在Windows環境中，請依照下列步驟將Adobe Campaign更新為新組建版本：

* [關閉服務](#shut-down-services)，
* [升級應用程式伺服器](#upgrade-the-adobe-campaign-server-application)，
* [同步資源](#synchronize-resources)，
* [重新啟動服務](#restart-services).

若要瞭解如何更新使用者端主控台，請參閱 [本節](../../installation/using/client-console-availability-for-windows.md).

### 關閉服務 {#shut-down-services}

若要以新版本取代所有檔案，您必須關閉nlserver服務的所有執行個體。

1. 關閉下列服務：

   * 網站服務(IIS)：

     **iisreset /stop**

   * Adobe Campaign服務： **網路停止nlserver6**

   >[!IMPORTANT]
   >
   >您也必須確定重新導向伺服器(webmdl)已停止，以便 **nlsrvmod.dll** IIS使用的檔案可以用新版本取代。

1. 請執行 **nlserver pdump** 命令。 應該會出現下列內容：

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   您可以使用Windows工作管理員來確認所有處理程式都已停止。

### 升級Adobe Campaign伺服器應用程式 {#upgrade-the-adobe-campaign-server-application}

若要執行升級檔案，請套用下列步驟：

1. 執行 **setup.exe**.

   若要下載此檔案，請連線至 [軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 使用您的使用者認證。 進一步瞭解中的軟體發佈 [此頁面](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant).

1. 選取安裝模式：選擇 **[!UICONTROL Update or repair]**
1. 按一下 **[!UICONTROL Next]** .
1. 按一下 **[!UICONTROL Finish]** .

   然後，安裝程式會複製新檔案。

1. 作業完成後，按一下 **[!UICONTROL Finish]** .

### 同步資源 {#synchronize-resources}

使用下列命令列：

**nlserver config -postupgrade -allinstances**

這可讓您執行下列操作：

* 同步資源
* 更新方案
* 更新資料庫

>[!NOTE]
>
>此操作只應執行一次，且僅應在(**nlserver web**)應用程式伺服器。

然後檢查同步是否產生錯誤或警告。 有關詳細資訊，請參閱 [解決升級衝突](#resolving-upgrade-conflicts).

### 重新啟動服務 {#restart-services}

要重新啟動的服務包括：

* 網站服務(IIS)：

  **iisreset /start**

* Adobe Campaign服務： **網路啟動nlserver6**

## Linux {#in-linux}

在Linux環境中，請依照下列步驟將Adobe Campaign更新為新組建版本：

* [下載更新的套件](#obtain-updated-packages)，
* [執行更新](#perform-an-update)，
* [重新啟動Web伺服器](#reboot-the-web-server).

[深入瞭解使用者端主控台可用性](../../installation/using/client-console-availability-for-windows.md).

>[!NOTE]
>
>從Build 8757開始，不再需要協力廠商程式庫。

### 取得更新的套件 {#obtain-updated-packages}

首先恢復Adobe Campaign的兩個更新包：連線到 [軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 使用您的使用者認證。 進一步瞭解中的軟體發佈 [此頁面](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant).

檔案為 **nlserver6-v7-XXX.rpm**

### 執行更新 {#perform-an-update}

* 以RPM為基礎的配送(RedHat、SuSe)

  若要安裝，請以root身分執行：

  ```
  $rpm -Uvh nlserver6-v7-XXXX.rpm
  ```

  其中XXX是檔案的版本。

  rpm檔案與您可以在CentOS/Red Hat分配上找到的套裝程式相依性。 如果您不想使用其中的部分相依性，則可能必須使用rpm的「nodeps」選項：

  ```
  rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
  ```

* DEB型分佈(Debian)

  若要安裝，請以root身分執行：

  ```
  dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
  ```

>[!NOTE]
>
>完整安裝程式詳載於 [本節](../../installation/using/installing-campaign-standard-packages.md). 資源會自動同步化，但您必須確定沒有發生錯誤。 有關詳細資訊，請參閱 [解決升級衝突](#resolving-upgrade-conflicts).

### 重新啟動Web伺服器 {#reboot-the-web-server}

您必須關閉Apache，新程式庫才能適用。

要執行此操作，請執行以下命令：

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* 您的指令碼可能會被呼叫 **httpd** 而非 **apache**.
>* 您必須執行此命令，直到獲得下列回覆為止：
>
>   Apache必須執行此作業才能套用新程式庫。

然後重新啟動Apache：

```
/etc/init.d/apache start
```

## 解決升級衝突 {#resolving-upgrade-conflicts}

在資源同步處理期間， **升級後** 命令可讓您偵測同步處理是否產生錯誤或警告。

### 檢視同步化結果 {#view-the-synchronization-result}

檢視同步化結果的方式有兩種：

* 在命令列介面中，錯誤會以三個>形箭號具體化 **>>>** 和同步會自動停止。 以雙>形箭號具體化警告 **>>** 同步完成後，必須解析和。 升級後結束時，命令提示字元中會顯示摘要。 如下所示：

  ```
  2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
  2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
  2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  如果警告與資源衝突有關，則需要使用者注意才能解決。

* 此 **升級後_`<server version number>_<time of postupgrade>`.log** 記錄檔包含同步化結果。 預設可在下列目錄中使用： **`<installation directory>/var/<instance/postupgrade`**. 錯誤和警告屬性會指出錯誤和警告。

### 解決衝突 {#resolving-conflicts}

若要解決衝突，請套用下列程式：

1. 在Adobe Campaign樹中，前往 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. 在清單中選取要解決的衝突。

有三種方法可解決衝突：

* **[!UICONTROL Declare as resolved]** ：需要使用者事先干預。
* **[!UICONTROL Accept the new version]** ：如果使用者未變更隨Adobe Campaign提供的資源，則建議使用。
* **[!UICONTROL Keep the current version]** ：表示更新遭拒。

  >[!IMPORTANT]
  >
  >如果您選取此解決模式，則可能無法受益於新版本的更正。

如果您選擇手動解決衝突，請按照以下步驟進行：

1. 在視窗的下半部分，搜尋 **_衝突_** 字串來找出有衝突的實體。 與新版本一起安裝的實體包含 **新** 引數，符合先前版本的實體包含 **cus** 引數。

   ![](assets/s_ncs_production_conflict002.png)

1. 刪除您不想要保留的版本。 刪除 **_conflict_argument_** 要保留的實體的字串。

   ![](assets/s_ncs_production_conflict003.png)

1. 移至您已解決的衝突。 按一下 **[!UICONTROL Actions]** 圖示並選取 **[!UICONTROL Declare as resolved]** .
1. 儲存變更：衝突現已解決。

### 最佳實務 {#best-practices}

更新失敗可能會連結到資料庫設定。 請確定技術管理員和資料庫管理員執行的設定是相容的。

例如，Unicode資料庫不僅必須授權儲存LATIN1資料等，

## 警告使用者端主控台有可用的更新 {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

在安裝Adobe Campaign應用程式伺服器的電腦上(**nlserver web**)，下載並複製檔案  **setup-client-6.XXXX.exe** i n **[應用程式的路徑]/datakit/nl/eng/jsp**.

下次連線使用者端主控台時，會出現一個視窗，通知使用者是否有更新可用，並提供他們下載和安裝更新的可能性。

>[!NOTE]
>
>請確定IIS_XPG使用者擁有此安裝檔案的適當讀取許可權，並參閱 [安裝指南](../../installation/using/general-architecture.md) 以取得詳細資訊。

### Linux {#in-linux-1}

在Adobe Campaign應用程式伺服器(**nlserver web**)已安裝，請擷取  **setup-client-6.XXXX.exe** 封裝並複製，另存為 **/usr/local/neolane/nl6/datakit/nl/eng/jsp**：

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

下次連線使用者端主控台時，會出現一個視窗，通知使用者是否有更新可用，並提供他們下載和安裝更新的可能性。

>[!NOTE]
>
>請確定Apache使用者對此安裝檔案具有適當的讀取許可權，並參閱 [安裝指南](../../installation/using/general-architecture.md) 以取得詳細資訊。
