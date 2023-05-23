---
product: campaign
title: 升級到新生成
description: 瞭解升級到新版本的技術步驟
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 3%

---

# 升級到新構建（內部部署）{#upgrading}



在啟動升級過程之前，確定並確認要升級哪個版本的Adobe Campaign，並咨詢 [發行說明](../../rn/using/latest-release.md) 。

>[!IMPORTANT]
>
>* Adobe強烈建議在更新之前對每個實例執行資料庫備份。 如需詳細資訊，請參閱[本區段](../../production/using/backup.md)。
>* 要執行升級，請確保您具有訪問實例和日誌的能力和權限。
>* 讀出 [此部分](../../installation/using/general-architecture.md) 和 [構建升級](https://helpx.adobe.com/tw/campaign/kb/acc-build-upgrade.html) 開始前先寫章。
>


## Windows {#in-windows}

在Windows環境中，按照以下步驟將Adobe Campaign更新為新生成：

* [關閉服務](#shut-down-services)。
* [升級應用程式伺服器](#upgrade-the-adobe-campaign-server-application)。
* [同步資源](#synchronize-resources)。
* [重新啟動服務](#restart-services)。

要瞭解如何更新客戶端控制台，請參閱 [此部分](../../installation/using/client-console-availability-for-windows.md)。

### 關閉服務 {#shut-down-services}

要用新版本替換所有檔案，需要關閉nlserver服務的所有實例。

1. 關閉以下服務：

   * Web服務(IIS):

      **isreset /stop**

   * Adobe Campaign社： **網站停止nlserver6**
   >[!IMPORTANT]
   >
   >您還需要確保重定向伺服器(webmdl)已停止，以便 **nlsrvmod.dll** IIS使用的檔案可替換為新版本。

1. 通過運行 **nlserver pdump** 的子菜單。 應出現以下內容：

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   您可以使用Windows任務管理器確保所有進程都已停止。

### 升級Adobe Campaign伺服器應用程式 {#upgrade-the-adobe-campaign-server-application}

要運行升級檔案，請應用以下步驟：

1. 運行 **setup.exe**。

   要下載此檔案，請連接到 [軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 使用用戶憑據。 瞭解有關中軟體分發的詳細資訊 [此頁](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant)。

1. 選擇安裝模式：選擇 **[!UICONTROL Update or repair]**
1. 按一下&#x200B;**[!UICONTROL Next]**。
1. 按一下&#x200B;**[!UICONTROL Finish]**。

   然後，安裝程式會複製新檔案。

1. 操作完成後，按一下 **[!UICONTROL Finish]** 。

### 同步資源 {#synchronize-resources}

使用以下命令行：

**nlserver config - postupgrade -allinstances**

這將使您能夠執行以下操作：

* 同步資源
* 更新架構
* 更新資料庫

>[!NOTE]
>
>此操作只應執行一次，且僅對(**nlserver web**)應用程式伺服器。

然後檢查同步是否生成了錯誤或警告。 有關此內容的詳細資訊，請參閱 [解決升級衝突](#resolving-upgrade-conflicts)。

### 重新啟動服務 {#restart-services}

要重新啟動的服務包括：

* Web服務(IIS):

   **isreset /start**

* Adobe Campaign社： **nlserver6**

## Linux {#in-linux}

在Linux環境中，按照以下步驟將Adobe Campaign更新為新版本：

* [下載更新的包](#obtain-updated-packages)。
* [執行更新](#perform-an-update)。
* [重新啟動Web伺服器](#reboot-the-web-server)。

[瞭解有關客戶端控制台可用性的詳細資訊](../../installation/using/client-console-availability-for-windows.md)。

>[!NOTE]
>
>從build 8757開始，不再需要第三方庫了。

### 獲取更新的包 {#obtain-updated-packages}

首先恢復兩個更新的Adobe Campaign包：連接到 [軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 使用用戶憑據。 瞭解有關中軟體分發的詳細資訊 [此頁](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant)。

檔案是 **nlserver6-v7-XXX.rpm**

### 執行更新 {#perform-an-update}

* 基於RPM的分發(RedHat 、 SuSe)

   要安裝它們，請以root身份執行：

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   其中XXX是檔案的版本。

   rpm檔案與CentOS/Red Hat分發上可找到的軟體包有依賴關係。 如果不想使用這些依賴項中的某些，則可能必須使用rpm的「nodeps」選項：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* 基於DEB的分發(Debian)

   要安裝它們，請以root身份執行：

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>完整的安裝過程詳見 [此部分](../../installation/using/installing-campaign-standard-packages.md)。 資源將自動同步，但您需要確保未發生錯誤。 有關此內容的詳細資訊，請參閱 [解決升級衝突](#resolving-upgrade-conflicts)。

### 重新啟動Web伺服器 {#reboot-the-web-server}

必須關閉Apache，新庫才能生效。

為此，請執行以下命令：

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* 可能會調用您的指令碼 **http** 而不是 **阿帕**。
>* 必須執行此命令，直到您獲得以下答復：

   >
   >   Apache要應用新庫，必須執行此操作。


然後重新啟動Apache:

```
/etc/init.d/apache start
```

## 解決升級衝突 {#resolving-upgrade-conflicts}

在資源同步期間， **坡道** 命令可用於檢測同步是否生成錯誤或警告。

### 查看同步結果 {#view-the-synchronization-result}

查看同步結果有兩種方法：

* 在命令行介面中，錯誤由三個V形 **>>** 同步將自動停止。 雙字形 **>** 並且必須在同步完成後進行解析。 在postupgrade的末尾，將在命令提示符下顯示摘要。 它可以是這樣的：

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   如果警告涉及資源衝突，則需要用戶注意才能解決。

* 的 **坡道`<server version number>_<time of postupgrade>`.日誌** 日誌檔案包含同步結果。 預設情況下，它可在以下目錄中使用： **`<installation directory>/var/<instance/postupgrade`**。 錯誤和警告屬性指示錯誤和警告。

### 解決衝突 {#resolving-conflicts}

要解決衝突，請應用以下流程：

1. 在Adobe Campaign樹上， **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** 。
1. 在清單中選擇要解決的衝突。

解決衝突有三種方法：

* **[!UICONTROL Declare as resolved]** :需要事先進行用戶干預。
* **[!UICONTROL Accept the new version]** :如果用戶未更改Adobe Campaign提供的資源，則建議使用。
* **[!UICONTROL Keep the current version]** :表示更新被拒絕。

   >[!IMPORTANT]
   >
   >如果選擇此解析模式，則新版本中的更正可能不會為您帶來好處。

如果選擇手動解決衝突，請按如下方式繼續：

1. 在窗口的下部，搜索 **_衝突_** 字串，以查找具有衝突的實體。 隨新版本安裝的實體包含 **新** 參數，與上一版本匹配的實體包含 **番** 參數。

   ![](assets/s_ncs_production_conflict002.png)

1. 刪除不想保留的版本。 刪除 **_衝突參數_** 所保留實體的字串。

   ![](assets/s_ncs_production_conflict003.png)

1. 轉到您已解決的衝突。 按一下 **[!UICONTROL Actions]** 表徵圖 **[!UICONTROL Declare as resolved]** 。
1. 保存更改：衝突現已解決。

### 最佳實務 {#best-practices}

更新失敗可能連結到資料庫配置。 確保技術管理員和資料庫管理員執行的配置相容。

例如，Unicode資料庫不僅必須授權儲存LATIN1資料等。

## 警告客戶端控制台可用更新 {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

在安裝Adobe Campaign應用程式伺服器的電腦上(**nlserver web**)，下載並複製檔案  **setup-client-6.XXXX.exe** 我 **[應用程式的路徑]/datakit/nl/eng/jsp**。

下次連接客戶端控制台時，窗口將通知用戶更新的可用性，並提供下載和安裝更新的可能性。

>[!NOTE]
>
>確保IIS_XPG用戶對此安裝檔案具有適當的讀取權限，並參閱 [安裝指南](../../installation/using/general-architecture.md) 的子菜單。

### Linux {#in-linux-1}

在Adobe Campaign應用程式伺服器(**nlserver web**)，檢索  **setup-client-6.XXXX.exe** 包並複製，另存為 **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

下次連接客戶端控制台時，窗口將通知用戶更新的可用性，並提供下載和安裝更新的可能性。

>[!NOTE]
>
>確保Apache用戶具有此安裝檔案的相應讀取權限，並參閱 [安裝指南](../../installation/using/general-architecture.md) 的子菜單。
