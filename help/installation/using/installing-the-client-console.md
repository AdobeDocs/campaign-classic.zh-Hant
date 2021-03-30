---
solution: Campaign Classic
product: campaign
title: 安裝客戶端主控台
description: 瞭解如何安裝客戶端控制台
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: c96a7faf5c65848a3f383a5721bfa45048ecea57
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 5%

---


# 安裝和更新促銷活動用戶端主控台{#installing-the-client-console}


「促銷活動用戶端主控台」是rich client，可讓您連線至您的Campaign應用程式伺服器。

在開始之前，您必須檢查促銷活動[相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)，取得您的促銷活動伺服器URL和使用者認證。

>[!CAUTION]
>
>促銷活動用戶端主控台和促銷活動應用程式伺服器必須在相同的產品版本上執行。 Adobe也建議使用相同的產品組建版本。

![](assets/do-not-localize/how-to-video.png) 瞭解如何在視訊中安裝和設定Adobe Campaign客 [戶端](#video)

安裝或更新用戶端主控台的程式會因您實作的Adobe Campaign Classic而異。
請檢閱下列詳細資訊，以瞭解您的實作需要什麼。


## Adobe代管實施{#hosted-customers}

要安裝或更新客戶機控制台，請執行以下操作：

1. Adobe可以直接部署。 在更新主控台後，系統會在快顯視窗中提示使用者下載最新的用戶端主控台版本。

1. 您可以從[Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)下載至您的用戶端主控台

   **使用者需要管理員存取權才能完成更新。如果用戶沒有管理員權限，系統管理員將需要部署到所有客戶端控制台**



## 混合式和完全內部部署實施{#hybrid-onprem-customers}

為了讓Adobe Campaign用戶能夠登錄您建立和配置的實例，他們需要使用客戶機控制台。

### 使控制台對用戶{#make-console-available}可用

當用於啟動Adobe Campaign應用程式伺服器(nlserver web)的電腦從客戶端控制台接收用戶連接時，可以配置它，使Adobe Campaign富客戶端的安裝程式通過HTML介面可用。 每當有新版本的用戶端主控台可供使用時，啟動其用戶端主控台時，都會邀請使用者下載。

若要這麼做，您必須：

1. 選擇包含控制台安裝程式的軟體包。

   此檔案對v7稱為setup-client-7.X.XXXX.exe ，對v6.1則稱為setup-client-6.X.XXXX.exe ，其中X是Adobe Campaign的子版本，XXXX是內部版本   編號。

1. 將此套件複製並貼至Adobe Campaign安裝資料夾（在混合安裝的行銷伺服器上），位於/datakit/nl/eng/jsp下。

1. 啟動Adobe Campaign伺服器。

>[!CAUTION]
>
>  Adobe建議取消選擇&#x200B;**[!UICONTROL No longer ask this question]**&#x200B;選項，以確保在控制台有新版本時所有用戶都收到警報。  如果選取此選項，使用者將不會收到新可用版本的通知。

如果已選擇&#x200B;**[!UICONTROL No longer ask this question]**，則可重設此提示。 只有熟悉編輯Windows註冊表的系統管理員才應進行以下更改：

1. 使用&#x200B;**[!UICONTROL Start > Run]**&#x200B;菜單中的&#x200B;**regedit**&#x200B;命令開啟註冊表編輯器。

1. 搜索節點並展開該節點。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除&#x200B;**confCommendedUpgrade**&#x200B;條目並關閉註冊表編輯器。

>[!NOTE]
>
>如果您要將更新的主控台套用至現有的實施，使用者會自動收到更新其主控台的提示。 如果您是第一次實作促銷活動，使用者將需要下載主控台。 請參閱下方，以取得兩個選項的詳細資訊

### 更新控制台——現有實施{#update-the-client-console}

在「促銷活動伺服器」檔案夾中提供主控台後，系統會在快顯視窗中提示使用者下載最新的用戶端主控台版本。

**使用者需要管理員存取權才能完成更新。如果用戶沒有管理員權限，系統管理員將需要部署到所有客戶端控制台**


### 下載主控台——新建實施{#download-the-client-console}

使用者現在應依照下列步驟下載並安裝主控台：

1. 開啟網頁瀏覽器並從下列位址下載主控台：

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. 在標識窗口中，輸入您的登錄名和密碼。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，請使用在建立執行個體期間定義的內部帳戶認證。

1. 按一下安裝頁上的&#x200B;**[!UICONTROL Download]**&#x200B;連結。
1. 下載並儲存用戶端設定檔案。
1. 在Windows上的電腦上執行下載的檔案：安裝即會啟動。 根據您的Adobe Campaign版本，客戶機控制台的預設安裝路徑是&#x200B;**$PROGRAMFILES$/Adobe/Adobe Campaign ClassicvX客戶機**，其中&#39;X&#39;是&#39;6&#39;或&#39;7&#39;。

### 建立連線——首次使用者僅{#create-the-connection}

安裝客戶機控制台後，請按照以下步驟建立與應用程式伺服器的連接：

1. 從&#x200B;**Adobe Campaign**&#x200B;程式組中的Windows **[!UICONTROL Start]**&#x200B;菜單啟動控制台。

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下&#x200B;**[!UICONTROL Add > Connection]**&#x200B;並輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 指定透過URL連線至您的Adobe Campaign應用程式伺服器。 使用DNS或電腦的別名或您的IP地址。

   例如，您可以使用[`https://<machine>.<domain>.com`](https://myserver.adobe.com)類型URL。

1. 如果已為您的組織設定AdobeIMS，請勾選選項&#x200B;**[!UICONTROL Connect with an Adobe ID]**

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以儲存您的設定。

例如，您可以視需要新增多個連線，以連線至測試、舞台和生產環境。

>[!NOTE]
>
>**[!UICONTROL Add]**&#x200B;按鈕可讓您建立&#x200B;**[!UICONTROL folders]**&#x200B;來組織所有連線。 只需將每個連線拖放到資料夾中即可。

### 登錄Adobe Campaign

要登錄到現有實例，請執行以下步驟：

1. 從&#x200B;**Adobe Campaign**&#x200B;程式組中的Windows **[!UICONTROL Start]**&#x200B;菜單啟動控制台。

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。

1. 選取您登入時需要的促銷活動例項。

1. 按一下 **[!UICONTROL Ok]**

1. 輸入您的用戶登錄憑據，然後按一下&#x200B;**[!UICONTROL Log in]**



**相關主題**

* [建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md).
* [相容性矩陣](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## 教學課程影片

本視頻介紹如何安裝和設定Adobe Campaign客戶端。

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

其他Campaign Classichow-to影片可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
