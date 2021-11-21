---
product: campaign
title: 升級至新組建
description: 了解升級至新組建的技術步驟
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 3%

---

# 升級至新組建（內部部署）{#upgrading}

![](../../assets/v7-only.svg)

開始升級程式之前，請判斷並確認要升級至哪個Adobe Campaign版本，並洽詢 [發行說明](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* Adobe強烈建議在更新前對每個執行個體進行資料庫備份。 如需詳細資訊，請參閱[本區段](../../production/using/backup.md)。
>* 若要執行升級，請確定您具備存取執行個體和記錄檔的能力和權限。
>* 閱讀 [本節](../../installation/using/general-architecture.md) 和 [版本升級](https://helpx.adobe.com/tw/campaign/kb/acc-build-upgrade.html) 章節。

>


## Windows {#in-windows}

在Windows環境中，請依照下列步驟，將Adobe Campaign更新至新組建：

* [關閉服務](#shut-down-services),
* [升級應用程式伺服器](#upgrade-the-adobe-campaign-server-application),
* [同步資源](#synchronize-resources),
* [重新啟動服務](#restart-services).

要了解如何更新客戶端控制台，請參閱 [本節](../../installation/using/client-console-availability-for-windows.md).

### 關閉服務 {#shut-down-services}

若要以新版本取代所有檔案，您需要關閉nlserver服務的所有執行個體。

1. 關閉以下服務：

   * Web服務(IIS):

      **iisreset /stop**

   * Adobe Campaign服務： **net stop nlserver6**
   >[!IMPORTANT]
   >
   >您還需要確保重定向伺服器(webmdl)已停止，以便 **nlsrvmod.dll** IIS使用的檔案可以替換為新版本。

1. 運行 **nlserver pdump** 命令。 應出現下列內容：

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   您可以使用Windows任務管理器來確保所有進程都已停止。

### 升級Adobe Campaign伺服器應用程式 {#upgrade-the-adobe-campaign-server-application}

要運行升級檔案，請應用以下步驟：

1. 執行 **setup.exe**.

   若要下載此檔案，請連線至 [軟體發佈門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 使用您的使用者憑證。 深入了解Software Distribution，位於 [本頁](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant?lang=en).

1. 選擇安裝模式：選擇 **[!UICONTROL Update or repair]**
1. 按一下&#x200B;**[!UICONTROL Next]**。
1. 按一下&#x200B;**[!UICONTROL Finish]**。

   然後，安裝程式將複製新檔案。

1. 操作完成後，按一下 **[!UICONTROL Finish]** .

### 同步資源 {#synchronize-resources}

使用下列命令列：

**nlserver config -postupgrade -allinstances**

這可讓您執行下列操作：

* 同步資源
* 更新結構
* 更新資料庫

>[!NOTE]
>
>此操作只應執行一次，且僅對(**nlserver web**)應用程式伺服器。

然後檢查同步是否生成錯誤或警告。 有關詳細資訊，請參閱 [解決升級衝突](#resolving-upgrade-conflicts).

### 重新啟動服務 {#restart-services}

要重新啟動的服務包括：

* Web服務(IIS):

   **isreset /start**

* Adobe Campaign服務： **net start nlserver6**

## Linux {#in-linux}

在Linux環境中，請依照下列步驟，將Adobe Campaign更新至新組建：

* [下載更新的套件](#obtain-updated-packages),
* [執行更新](#perform-an-update),
* [重新啟動Web伺服器](#reboot-the-web-server).

[深入了解用戶端主控台可用性](../../installation/using/client-console-availability-for-windows.md).

>[!NOTE]
>
>從8757組建版本開始，就不再需要協力廠商程式庫。

### 取得更新的套件 {#obtain-updated-packages}

首先，請恢復兩個更新的Adobe Campaign套件：連線至 [軟體發佈門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 使用您的使用者憑證。 深入了解Software Distribution，位於 [本頁](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

檔案是 **nlserver6-v7-XXX.rpm**

### 執行更新 {#perform-an-update}

* 基於RPM的分發(RedHat、SuSe)

   若要安裝，請以根目錄執行：

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   其中XXX是檔案的版本。

   rpm檔案對包具有依賴性，您可以在CentOS/Red Hat分發上找到這些包。 如果您不想使用其中的一些依賴項，則可能需要使用rpm的「nodeps」選項：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* DEB型分送(Debian)

   若要安裝，請以根目錄執行：

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>完整的安裝程式在 [本節](../../installation/using/installing-campaign-standard-packages.md). 資源會自動同步，但您必須確定未發生任何錯誤。 有關詳細資訊，請參閱 [解決升級衝突](#resolving-upgrade-conflicts).

### 重新啟動Web伺服器 {#reboot-the-web-server}

您必須關閉Apache，新程式庫才可適用。

要執行此操作，請執行以下命令：

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* 可能會呼叫您的指令碼 **httpd** 而非 **apache**.
>* 您必須執行此命令，直到獲得以下答復：

   >
   >   若要讓Apache套用新程式庫，必須執行此操作。


然後重新啟動Apache:

```
/etc/init.d/apache start
```

## 解決升級衝突 {#resolving-upgrade-conflicts}

在資源同步期間， **postugrade** 命令可以檢測同步是否生成錯誤或警告。

### 查看同步結果 {#view-the-synchronization-result}

查看同步結果有兩種方式：

* 在命令行介面中，錯誤由三個>形形成 **>>** 並自動停止同步。 雙形箭頭就會發出警告 **>>** 同步完成後，和必須解析。 在升級後的結尾處，命令提示符中將顯示一個摘要。 可能如下所示：

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   如果警告涉及資源衝突，則需要用戶注意才能解決該問題。

* 此 **postupgrade_`<server version number>_<time of postupgrade>`.log** 日誌檔案包含同步結果。 預設可在下列目錄中使用： **`<installation directory>/var/<instance/postupgrade`**. 錯誤和警告由錯誤和警告屬性指示。

### 解決衝突 {#resolving-conflicts}

要解決衝突，請應用以下進程：

1. 在Adobe Campaign樹中，前往 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. 在清單中選擇要解決的衝突。

解決衝突有三種方法：

* **[!UICONTROL Declare as resolved]** :需要事先進行用戶干預。
* **[!UICONTROL Accept the new version]** :如果使用者未變更隨Adobe Campaign提供的資源，則建議使用。
* **[!UICONTROL Keep the current version]** :表示已拒絕更新。

   >[!IMPORTANT]
   >
   >如果選擇此解析模式，則新版本中的更正可能不會使您受益。

如果您選擇手動解決衝突，請按以下步驟繼續：

1. 在視窗的下方，搜尋 **_衝突_** 字串，以找出具有衝突的實體。 隨新版本安裝的實體包含 **new** 引數中，與上一版本匹配的實體包含 **cus** 引數。

   ![](assets/s_ncs_production_conflict002.png)

1. 刪除您不想保留的版本。 刪除 **_conflict_argument_** 您要保留的實體字串。

   ![](assets/s_ncs_production_conflict003.png)

1. 轉到已解決的衝突。 按一下 **[!UICONTROL Actions]** 圖示並選取 **[!UICONTROL Declare as resolved]** .
1. 儲存您的變更：衝突現在已經解決。

### 最佳實務 {#best-practices}

更新失敗可能連結到資料庫配置。 確保技術管理員和資料庫管理員執行的配置相容。

例如，Unicode資料庫不僅必須授權儲存LATIN1資料等。

## 警告客戶端控制台可用更新 {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

在安裝Adobe Campaign應用程式伺服器的電腦上(**nlserver web**)、下載並複製檔案  **setup-client-6.XXXX.exe** i n **[應用程式的路徑]/datakit/nl/eng/jsp**.

下次連接客戶端控制台時，窗口將通知用戶更新的可用性，並為用戶提供下載和安裝更新的可能性。

>[!NOTE]
>
>請確保IIS_XPG用戶對此安裝檔案具有適當的讀取權限，並參閱 [安裝指南](../../installation/using/general-architecture.md) 以取得更多資訊。

### Linux {#in-linux-1}

在Adobe Campaign應用程式伺服器(**nlserver web**)，則擷取  **setup-client-6.XXXX.exe** 包並複製，另存為 **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

下次連接客戶端控制台時，窗口將通知用戶更新的可用性，並為用戶提供下載和安裝更新的可能性。

>[!NOTE]
>
>請確定Apache使用者擁有此安裝檔案的適當讀取權限，並參閱 [安裝指南](../../installation/using/general-architecture.md) 以取得更多資訊。
