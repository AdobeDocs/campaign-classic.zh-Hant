---
product: campaign
title: 安裝使用者端主控台
description: 瞭解如何安裝使用者端主控台
feature: Installation, Upgrade
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 2%

---

# 安裝和更新Campaign使用者端主控台{#installing-the-client-console}

Campaign使用者端主控台是豐富的使用者端，可讓您連線至您的Campaign應用程式伺服器。

開始安裝使用者端主控台之前，您需要：

* 在[相容性矩陣](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)中檢查您的系統與工具與Adobe Campaign的相容性
* 取得您的Campaign伺服器URL
* 取得您的使用者認證
* 在您的系統上安裝Microsoft Edge Webview2執行階段(來自Campaign Classic7.3建置版本)。 [了解更多](#webview)

安裝或更新使用者端主控台的程式會依您實作的Adobe Campaign Classic而有所不同。
請檢閱下列詳細資料，以瞭解實作所需的內容。

![](assets/do-not-localize/how-to-video.png)在[影片](#video)中探索如何安裝和設定Adobe Campaign使用者端

>[!CAUTION]
>
>* Campaign使用者端主控台和Campaign應用程式伺服器必須在相同的產品版本&#x200B;**上執行**。 Adobe也強烈建議使用&#x200B;**相同的產品組建**。 在[本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何檢查您的Campaign使用者端和伺服器版本。
>
>* 主控台安裝所在的安裝資料夾存取權應該僅限於目標使用者，確保寫入許可權受到相應的限制。



## Microsoft Edge Webview2執行階段安裝 {#webview}

從Campaign Classic7.3建置版本開始，任何主控台安裝都需要安裝Microsoft Edge Webview 2執行階段。

Web View預設會安裝為Windows 11作業系統的一部分。 如果系統尚未安裝該程式，則Campaign Classic主控台安裝程式會提示您從[Microsoft開發人員網站](https://www.adobe.com/go/acc-ms-webview2-runtime-download_tw)下載它。 請注意，下載連結在Internet Explorer 11瀏覽器上無法運作，因為Microsoft已停止支援。 請確定您使用不同的瀏覽器來存取連結。

## Adobe託管實作 {#hosted-customers}

作為託管客戶，您有兩個選項可安裝或更新使用者端主控台：

1. Adobe可以直接部署。 主控台更新後，系統會提示使用者在快顯視窗中下載最新的使用者端主控台版本。

1. 您可以從[Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)下載到您的使用者端主控台

   **使用者需要管理員存取權才能完成更新。 如果使用者沒有管理員許可權，系統管理員必須部署至所有使用者端主控台**

## 混合式與內部部署實作 {#hybrid-onprem-customers}

為了讓Adobe Campaign使用者能夠登入您已建立和設定的執行個體，他們需要使用使用者端主控台。

### 讓使用者可以使用主控台 {#make-console-available}

當用來啟動Adobe Campaign應用程式伺服器(nlserver web)的電腦收到來自使用者端主控台的使用者連線時，您可以將其設定為透過HTML介面提供Adobe Campaign豐富型使用者端的安裝程式。 每當有新版本的使用者端主控台可供使用時，使用者就會在啟動其使用者端主控台時進行下載。

若要這麼做，您必須：

1. 選取包含主控台安裝程式的套件。

   此檔案名為setup-client-7.X.XXXX.exe，其中X是Adobe Campaign的子版本，XXXX是組建編號。

1. 將此套件複製並貼到/datakit/nl/eng/jsp下的Adobe Campaign安裝資料夾（針對混合安裝位在Marketing伺服器上）。

1. 啟動Adobe Campaign伺服器。


### 不再詢問此問題選項

Adobe建議取消選取選項&#x200B;**[!UICONTROL No longer ask this question]**，以確保當有新版本的主控台可用時，所有使用者都會收到警示。  如果選取此選項，將不會通知使用者新的可用版本。

如果已選取&#x200B;**[!UICONTROL No longer ask this question]**，您可以重設此提示。 只有熟悉編輯Windows登入的系統管理員才應該進行下列變更：

1. 從&#x200B;**[!UICONTROL Start > Run]**&#x200B;功能表使用&#x200B;**regedit**&#x200B;命令開啟登入編輯程式。

1. 搜尋並展開節點。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除&#x200B;**confAdvisedUpgrade**&#x200B;專案並關閉登入編輯程式。

>[!NOTE]
>
>如果您將更新的主控台套用至現有的實作，使用者會自動收到提示以更新其使用者端主控台。 如果您是首次實作Campaign，使用者必須下載主控台。 請參閱下方以瞭解這兩個選項的詳細資訊

### 更新現有實作的控制檯{#update-the-client-console}

在Campaign伺服器資料夾中可以使用主控台後，系統會提示使用者在快顯視窗中下載最新的使用者端主控台版本。

**使用者需要管理員存取權才能完成更新。 如果使用者沒有管理員許可權，系統管理員必須部署至所有使用者端主控台**


### 下載主控台以進行新實作{#download-the-client-console}

使用者現在應該遵循下列步驟下載並安裝主控台：

1. 開啟網頁瀏覽器，並從下列地址下載主控台：

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`。

1. 在識別視窗中，輸入您的登入和密碼。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，請使用建立執行個體期間定義的內部帳戶認證。

1. 按一下安裝頁面上的&#x200B;**[!UICONTROL Download]**&#x200B;連結。
1. 下載並儲存使用者端安裝檔案。
1. 在Windows上的電腦上執行下載的檔案：安裝會啟動。 使用者端主控台的預設安裝路徑為&#x200B;**$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**，其中&#39;X&#39;為&#39;6&#39;或&#39;7&#39;(根據您的Adobe Campaign版本)。

### 建立連線 — 僅首次使用者{#create-the-connection}

安裝使用者端主控台後，請依照下列步驟建立與應用程式伺服器的連線：

1. 從&#x200B;**Adobe Campaign**&#x200B;程式群組中的Windows **[!UICONTROL Start]**&#x200B;功能表啟動主控台。

1. 按一下認證欄位右上角的連結以存取連線設定視窗。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下&#x200B;**[!UICONTROL Add > Connection]**&#x200B;並輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 指定透過URL連線至您的Adobe Campaign應用程式伺服器。 請使用電腦的DNS或別名，或您的IP位址。

   例如，您可以使用`https://<machine>.<domain>.com`型別URL。

1. 如果貴組織已設定Adobe IMS，請核取選項&#x200B;**[!UICONTROL Connect with an Adobe ID]**

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;儲存您的設定。

例如，您可以視需要新增許多連線，以連線至您的測試、中繼和生產環境。

>[!NOTE]
>
>「**[!UICONTROL Add]**」按鈕可讓您建立&#x200B;**[!UICONTROL folders]**&#x200B;以組織所有連線。 只需將每個連線拖放到資料夾中即可。

### 登入Adobe Campaign

若要登入現有執行個體，請遵循下列步驟：

1. 從&#x200B;**Adobe Campaign**&#x200B;程式群組中的Windows **[!UICONTROL Start]**&#x200B;功能表啟動主控台。

1. 按一下認證欄位右上角的連結以存取連線設定視窗。

1. 選取您需要登入的Campaign執行個體。

1. 按一下&#x200B;**[!UICONTROL Ok]**

1. 輸入您的使用者登入認證，然後按一下&#x200B;**[!UICONTROL Log in]**

>[!NOTE]
>
>對於campaign classic 7.3版本編號，Adobe Campaign使用者端主控台可能會在Proxy驗證期間要求Proxy憑證兩次。 這是因為Microsoft Edge Webview2不像Internet Explorer那樣將Proxy憑證儲存在快取/密碼存放區中。

**相關主題**

* [正在建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md)。
* [相容性對較表](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

## 教學課程影片

本影片說明如何安裝和設定Adobe Campaign使用者端。

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

其他 Campaign Classic 作法影片可在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
