---
product: campaign
title: 升級至新組建
description: 了解升級至新組建的技術步驟
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 2%

---

# 升級至新組建（內部部署）{#upgrading}

開始升級程式之前，請判斷並確認要升級至哪個Adobe Campaign版本，並參閱[發行說明](../../rn/using/latest-release.md) 。

>[!IMPORTANT]
>
>* Adobe強烈建議在更新前對每個執行個體進行資料庫備份。 如需詳細資訊，請參閱[本區段](../../production/using/backup.md)。
>* 若要執行升級，請確定您具備存取執行個體和記錄檔的能力和權限。
>* 開始之前，請閱讀[本節](../../installation/using/general-architecture.md)和[build upgrade](https://helpx.adobe.com/tw/campaign/kb/acc-build-upgrade.html)章節。

>



## Windows {#in-windows}

在Windows環境中，請依照下列步驟，將Adobe Campaign更新至新組建：

* [關閉服務](#shut-down-services),
* [升級應用程式伺服器](#upgrade-the-adobe-campaign-server-application),
* [同步資源](#synchronize-resources),
* [重新啟動服務](#restart-services)。

要了解如何更新客戶端控制台，請參閱[此部分](../../installation/using/client-console-availability-for-windows.md)。

### 關閉服務{#shut-down-services}

若要以新版本取代所有檔案，您需要關閉nlserver服務的所有執行個體。

1. 關閉以下服務：

   * Web服務(IIS):

      **iisreset /stop**

   * Adobe Campaign服務：**net stop nlserver6**
   >[!IMPORTANT]
   >
   >您還需要確保重定向伺服器(webmdl)已停止，以便IIS使用的&#x200B;**nlsrvmod.dll**&#x200B;檔案可以替換為新版本。

1. 通過運行&#x200B;**nlserver pdump**&#x200B;命令，檢查沒有任務處於活動狀態。 應出現下列內容：

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   您可以使用Windows任務管理器來確保所有進程都已停止。

### 升級Adobe Campaign伺服器應用程式{#upgrade-the-adobe-campaign-server-application}

要運行升級檔案，請應用以下步驟：

1. 運行&#x200B;**setup.exe**。

   若要下載此檔案，請使用您的用戶憑據連接到[軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。 了解更多[本頁](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)中的軟體分發。

1. 選擇安裝模式：選擇&#x200B;**[!UICONTROL Update or repair]**
1. 按一下 **[!UICONTROL Next]**。
1. 按一下 **[!UICONTROL Finish]**。

   然後，安裝程式將複製新檔案。

1. 操作完成後，按一下&#x200B;**[!UICONTROL Finish]** 。

### 同步資源{#synchronize-resources}

使用下列命令列：

**nlserver config -postupgrade -allinstances**

這可讓您執行下列操作：

* 同步資源
* 更新結構
* 更新資料庫

>[!NOTE]
>
>此操作只應執行一次，並且只應在(**nlserver web**)應用程式伺服器上執行。

然後檢查同步是否生成錯誤或警告。 有關詳細資訊，請參閱[解決升級衝突](#resolving-upgrade-conflicts)。

### 重新啟動服務{#restart-services}

要重新啟動的服務包括：

* Web服務(IIS):

   **isreset /start**

* Adobe Campaign服務：**net start nlserver6**

## Linux {#in-linux}

在Linux環境中，請依照下列步驟，將Adobe Campaign更新至新組建：

* [下載更新的套件](#obtain-updated-packages),
* [執行更新](#perform-an-update),
* [重新啟動Web伺服器](#reboot-the-web-server)。

[深入了解用戶端主控台可用性](../../installation/using/client-console-availability-for-windows.md)。

>[!NOTE]
>
>從8757組建版本開始，就不再需要協力廠商程式庫。

### 獲取更新的包{#obtain-updated-packages}

首先，請恢復Adobe Campaign的兩個更新套件：使用您的用戶憑據連接到[Software distribution portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。 了解更多[本頁](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)中的軟體分發。

檔案為&#x200B;**nlserver6-v7-XXX.rpm**

### 執行更新{#perform-an-update}

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
>[本節](../../installation/using/installing-campaign-standard-packages.md)中詳細說明了完整的安裝過程。 資源會自動同步，但您必須確定未發生任何錯誤。 有關詳細資訊，請參閱[解決升級衝突](#resolving-upgrade-conflicts)。

### 重新啟動Web伺服器{#reboot-the-web-server}

您必須關閉Apache，新程式庫才可適用。

要執行此操作，請執行以下命令：

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* 您的指令碼可能稱為&#x200B;**httpd**，而非&#x200B;**apache**。
>* 您必須執行此命令，直到獲得以下答復：

   >
   >   
   若要讓Apache套用新程式庫，必須執行此操作。


然後重新啟動Apache:

```
/etc/init.d/apache start
```

## 解決升級衝突{#resolving-upgrade-conflicts}

在資源同步期間， **postupgrade**&#x200B;命令允許您檢測同步是否生成了錯誤或警告。

### 查看同步結果{#view-the-synchronization-result}

查看同步結果有兩種方式：

* 在命令行介面中，錯誤由三個>>**>>實現，並自動停止同步。**&#x200B;警告由雙>形&#x200B;**>>**&#x200B;實現，並且必須在同步完成後進行解析。 在升級後的結尾處，命令提示符中將顯示一個摘要。 可能如下所示：

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   如果警告涉及資源衝突，則需要用戶注意才能解決該問題。

* **postupgrade_`<server version number>_<time of postupgrade>`.log**&#x200B;日誌檔案包含同步結果。 預設可在下列目錄中使用：**`<installation directory>/var/<instance/postupgrade`**。 錯誤和警告由錯誤和警告屬性指示。

### 解決衝突{#resolving-conflicts}

要解決衝突，請應用以下進程：

1. 在Adobe Campaign樹中，前往&#x200B;**[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** 。
1. 在清單中選擇要解決的衝突。

解決衝突有三種方法：

* **[!UICONTROL Declare as resolved]** :需要事先進行用戶干預。
* **[!UICONTROL Accept the new version]** :如果使用者未變更隨Adobe Campaign提供的資源，則建議使用。
* **[!UICONTROL Keep the current version]** :表示已拒絕更新。

   >[!IMPORTANT]
   >
   >如果選擇此解析模式，則新版本中的更正可能不會使您受益。

如果您選擇手動解決衝突，請按以下步驟繼續：

1. 在窗口的下半部分，搜索&#x200B;**_conflict_**&#x200B;字串以查找具有衝突的實體。 隨新版本安裝的實體包含&#x200B;**new**&#x200B;引數，與舊版相符的實體包含&#x200B;**cus**&#x200B;引數。

   ![](assets/s_ncs_production_conflict002.png)

1. 刪除您不想保留的版本。 刪除要保留的實體的&#x200B;**_conflict_argument_**&#x200B;字串。

   ![](assets/s_ncs_production_conflict003.png)

1. 轉到已解決的衝突。 按一下&#x200B;**[!UICONTROL Actions]**&#x200B;圖示並選取&#x200B;**[!UICONTROL Declare as resolved]** 。
1. 儲存您的變更：衝突現在已經解決。

### 最佳實務{#best-practices}

更新失敗可能連結到資料庫配置。 確保技術管理員和資料庫管理員執行的配置相容。

例如，Unicode資料庫不僅必須授權儲存LATIN1資料等。

## 警告客戶端控制台可用更新{#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

在安裝Adobe Campaign應用程式伺服器的電腦上(**nlserver web**)，下載並複製檔案&#x200B;**setup-client-6.XXXX.exe**，位於應用程式]/datakit/nl/eng/jsp **的**[&#x200B;路徑中。

下次連接客戶端控制台時，窗口將通知用戶更新的可用性，並為用戶提供下載和安裝更新的可能性。

>[!NOTE]
>
>請確保IIS_XPG用戶具有此安裝檔案的適當讀取權限，並參閱[安裝指南](../../installation/using/general-architecture.md)以了解詳細資訊。

### Linux {#in-linux-1}

在安裝Adobe Campaign應用程式伺服器(**nlserver web**)的電腦上，檢索&#x200B;**setup-client-6.XXXX.exe**&#x200B;包並複製它，另存為&#x200B;**/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

下次連接客戶端控制台時，窗口將通知用戶更新的可用性，並為用戶提供下載和安裝更新的可能性。

>[!NOTE]
>
>請確定Apache使用者擁有此安裝檔案的適當讀取權限，並參閱[安裝指南](../../installation/using/general-architecture.md)以取得詳細資訊。
