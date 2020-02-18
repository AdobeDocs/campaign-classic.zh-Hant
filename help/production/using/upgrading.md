---
title: 升級
seo-title: 升級
description: 升級
seo-description: null
page-status-flag: never-activated
uuid: f24552d4-6bdf-411c-a1f2-b8f339c311f4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: f8e3633d-7232-44a5-842b-1a70c4f2bca2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8fd9949ec03b7c2cdf88a9d5fcf5c8d8fd85f7d0

---


# 升級{#upgrading}

在開始升級程式之前，請確定並確認要升級至哪個Adobe Campaign版本，並參閱版 [本說明](https://docs.campaign.adobe.com/doc/AC/en/RN.html)。

>[!CAUTION]
>
>我們強烈建議在更新之前對每個實例進行資料庫備份。 有關詳細資訊，請參 [閱Backup](../../production/using/backup.md)。\
>若要執行升級，請確定您擁有存取例項和記錄檔的能力和權限。

>[!NOTE]
>
>另請參閱安裝 [指南](../../installation/using/general-architecture.md) ，以及 [組建升級](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 。

## 在Windows中 {#in-windows}

若要在傳送新組建版本時以新版本更新Adobe Campaign,Windows應套用下列程式：

* [關閉服務](#shut-down-services),
* [升級Adobe Campaign伺服器應用程式](#upgrade-the-adobe-campaign-server-application),
* [同步資源](#synchronize-resources),
* [重新啟動服務](#restart-services)。

要瞭解如何更新客戶機控制台，請參 [閱本節](../../installation/using/client-console-availability-for-windows.md)。

### 關閉服務 {#shut-down-services}

為了用新版本替換所有檔案，您需要關閉nlserver服務的所有實例。

1. 關閉以下服務：

   * 網站服務(IIS):

      **iisreset /stop**

   * Adobe Campaign服務：網 **站停止nlserver6**
   >[!CAUTION]
   >
   >您還需要確保重定向伺服器(webmdl)已停止，以便IIS使用的 **nlsrvmod.dll** 檔案可以替換為新版本。

1. 運行nlserver pdump命令檢查沒有任 **務處於活動狀態** 。 應出現以下內容：

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   您可以使用Windows任務管理器來確保所有進程都已停止。

### 升級Adobe Campaign伺服器應用程式 {#upgrade-the-adobe-campaign-server-application}

若要執行升級檔案，請套用下列步驟：

1. 運行 **setup.exe**。

   若要下載此檔案，請透過下載中心連結前往Adobe Campaign支 [援頁面](https://support.neolane.net/)( **https://support.neolane.net/** )。

1. 選擇安裝模式：選擇 **[!UICONTROL Update or repair]**
1. 按一下 **[!UICONTROL Next]** .
1. 按一下 **[!UICONTROL Finish]** .

   然後，安裝程式會複製新檔案。

1. 操作完成後，按一下 **[!UICONTROL Finish]** 。

### 同步資源 {#synchronize-resources}

使用以下命令行：

**nlserver config -postupgrade-allinstances**

這可讓您執行下列作業：

* 同步資源、
* 更新方案，
* 更新資料庫。

>[!NOTE]
>
>此操作只應在(nlserver web **)應用程式伺服器上執行一次，並且**&#x200B;僅在該伺服器上執行。

然後檢查同步是否生成了錯誤或警告。 有關詳細資訊，請參閱解決 [升級衝突](#resolving-upgrade-conflicts)。

### 重新啟動服務 {#restart-services}

要重新啟動的服務包括：

* 網站服務(IIS):

   **iisreset /start**

* Adobe Campaign服務： **net start nlserver6**

## 在Linux中 {#in-linux}

若要在傳送新建版本時更新Adobe Campaign,Linux的程式如下：

* [獲取更新的包](#obtain-updated-packages),
* [執行更新](#perform-an-update),
* [重新啟動Web伺服器](#reboot-the-web-server)。

要瞭解如何更新客戶機控制台，請參 [閱本節](../../installation/using/client-console-availability-for-linux.md)。

>[!NOTE]
>
>從建置8757起，就不再需要協力廠商資料庫。

### 獲取更新的包 {#obtain-updated-packages}

從恢復Adobe Campaign的兩個更新套件開始：透過下載中心連結，前往Adobe Campaign支 [援頁面](https://support.neolane.net/)( **https://support.neolane.net/** )。

檔案為 **nlserver6-v7-XXX.rpm**

### 執行更新 {#perform-an-update}

* 以RPM為基礎的散發(RedHat、SuSe)

   要安裝它們，請以root用戶身份執行：

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   其中XXX是檔案的版本。

   rpm檔案對包具有依賴性，您可以在CentOS/Red hat分發上找到這些包。 如果您不想使用其中一些依賴項，則可能必須使用rpm的「nodeps」選項：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* 以DEB為基礎的散發(Debian)

   要安裝它們，請以root用戶身份執行：

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>本節將詳述完整的安 [裝過程](../../installation/using/installing-campaign-standard-packages.md)。 資源會自動同步，但您需要確保未發生任何錯誤。 有關詳細資訊，請參閱解決 [升級衝突](#resolving-upgrade-conflicts)。

### 重新啟動Web伺服器 {#reboot-the-web-server}

您必須關閉Apache，新程式庫才能適用。

要執行此操作，請執行以下命令：

```
/etc/init.d/apache stop
```

>[!CAUTION]
>
>* 您的指令碼可能會被 **稱為httpd** ，而非 **apache**。
>* 您必須執行此命令，直到您獲得以下回覆：
   >Apache必須執行此操作，才能應用新庫。
>



然後重新啟動Apache:

```
/etc/init.d/apache start
```

## 解決升級衝突 {#resolving-upgrade-conflicts}

在資源同步期間， **postupgrade** 命令使您能夠檢測同步是否生成了錯誤或警告。

### 查看同步結果 {#view-the-synchronization-result}

查看同步結果有兩種方法：

* 在命令行介面中，錯誤由三重Chevron **>>>實** 現，並自動停止同步。 警告由雙雪佛龍 **>>實** 現，並且必須在同步完成後解決。 在postupgrade的末尾，將在命令提示符中顯示一個摘要。 它可能如下所示：

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   如果警告涉及資源衝突，則需要使用者注意才能解決。

* postupgrade_ **.log`<server version number>_<time of postupgrade>`** 日誌檔案包含同步結果。 預設情況下，它位於以下目錄： **`<installation directory>/var/<instance/postupgrade`**。 錯誤和警告由錯誤和警告屬性指示。

### 解決衝突 {#resolving-conflicts}

要解決衝突，請應用以下流程：

1. 在Adobe Campaign樹狀結構中，前往 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** 。
1. 在清單中選擇要解決的衝突。

解決衝突的方法有三種：

* **[!UICONTROL Declare as resolved]** :需要事先進行使用者干預。
* **[!UICONTROL Accept the new version]** :如果使用者未變更隨Adobe Campaign提供的資源，則建議使用。
* **[!UICONTROL Keep the current version]** :表示更新遭拒。

   >[!CAUTION]
   >
   >如果您選取此解析度模式，新版本中的修正可能不會讓您受益。

如果您選擇手動解決衝突，請按如下步驟進行：

1. 在窗口的下半部分中，搜索衝 **_突字串_** ，以查找具有衝突的實體。 隨新版本安裝的實體包含 **new** 引數，與舊版相符的實體包含 **cus** 引數。

   ![](assets/s_ncs_production_conflict002.png)

1. 刪除您不想保留的版本。 刪除 **_要保留的實體的conflict_argument_** 字串。

   ![](assets/s_ncs_production_conflict003.png)

1. 前往您已解決的衝突。 按一下圖 **[!UICONTROL Actions]** 示並選取 **[!UICONTROL Declare as resolved]** 。
1. 儲存變更：衝突現已解決。

### 最佳實務 {#best-practices}

更新失敗可能與資料庫配置相連結。 確保技術管理員和資料庫管理員執行的配置相容。

例如，Unicode資料庫不僅必須授權儲存LATIN1資料等。

## 警告客戶端控制台可用更新 {#warn-the-client-consoles-of-the-available-update}

### 在Windows中 {#in-windows-1}

在安裝(**nlserver web**)Adobe Campaign應用程式伺服器的機器上，下載並複製檔案

**setup-client-6。** XXXX **.exe**

在**應[用程式的路徑]**datakitlengjsp

下次連接客戶機控制台時，窗口將通知用戶更新的可用性，並為用戶提供下載和安裝更新的可能性。

>[!NOTE]
>
>請確定IIS_XPG用戶具有該安裝檔案的適當讀權限，並參閱安裝指 [南](../../installation/using/general-architecture.md) ，以瞭解詳細資訊。

### 在Linux中 {#in-linux-1}

在安裝Adobe Campaign應用程式伺服器(**nlserver web**)的機器上，擷取下列套件：

**setup-client-6。** XXXX **.exe**

並複製，另存 **為/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

下次連接客戶機控制台時，窗口將通知用戶更新的可用性，並為用戶提供下載和安裝更新的可能性。

>[!NOTE]
>
>請確定Apache用戶具有此安裝檔案的適當讀權限，並參閱安裝指 [南](../../installation/using/general-architecture.md) ，以瞭解詳細資訊。

