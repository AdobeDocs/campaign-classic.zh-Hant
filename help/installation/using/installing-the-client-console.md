---
product: campaign
title: 安裝客戶端主控台
description: 了解如何安裝用戶端主控台
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 4%

---

# 安裝和更新Campaign用戶端主控台{#installing-the-client-console}

![](../../assets/v7-only.svg)

Campaign用戶端主控台是一個豐富用戶端，可讓您連線至您的Campaign應用程式伺服器。

開始安裝客戶端控制台之前，您需要：

* 在[相容性矩陣](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)中檢查您的系統和工具與Adobe Campaign的相容性
* 取得您的Campaign伺服器URL
* 取得您的使用者認證

安裝或更新用戶端主控台的程式會因您實作Adobe Campaign Classic而異。
請檢閱下列詳細資訊，了解實作所需的項目。

![](assets/do-not-localize/how-to-video.png) 了解如何在影片中安裝和設定Adobe Campaign  [Client](#video)

>[!CAUTION]
>
>Campaign用戶端主控台和Campaign應用程式伺服器必須在相同產品版本&#x200B;**上執行**。 Adobe也強烈建議使用&#x200B;**相同的產品組建**。 了解如何在[本區段](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的Campaign用戶端和伺服器版本。

## Adobe托管實作 {#hosted-customers}

廣告代管客戶後，您有兩個選項可安裝或更新用戶端主控台：

1. Adobe可直接部署。 更新主控台後，系統會在快顯視窗中提示使用者下載最新的用戶端主控台版本。

1. 您可以從[Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)下載至用戶端主控台

   **使用者需要管理員存取權才能完成更新。如果用戶沒有管理員權限，則系統管理員需要部署到所有客戶端控制台**

## 混合式與內部部署實作 {#hybrid-onprem-customers}

Adobe Campaign使用者若想登入您建立和設定的執行個體，必須使用用戶端主控台。

### 讓使用者能使用主控台 {#make-console-available}

用來啟動Adobe Campaign應用程式伺服器(nlserver web)的電腦從用戶端主控台接收使用者連線時，您可以加以設定，讓Adobe Campaign豐富用戶端的設定程式可透過HTML介面使用。 每當有新版本的用戶端主控台可用時，就會邀請使用者在啟動其用戶端主控台時下載。

要執行此操作，您必須：

1. 選擇包含控制台安裝程式的包。

   此檔案稱為setup-client-7.X.XXXX.exe（適用於v7）或setup-client-6.X.XXXX.exe（適用於v6.1），其中X是Adobe Campaign的子版本，XXXX是組建   數字。

1. 將此套件複製並貼到Adobe Campaign安裝資料夾（位於混合式安裝的行銷伺服器上）的/datakit/nl/eng/jsp下。

1. 啟動Adobe Campaign伺服器。


### 不再提出此問題選項

Adobe建議取消選取&#x200B;**[!UICONTROL No longer ask this question]**&#x200B;選項，以確保在有新版本的控制台可用時，所有使用者都會收到警報。  如果選取此選項，系統不會通知使用者新的可用版本。

如果已選取&#x200B;**[!UICONTROL No longer ask this question]**，則可重設此提示。 只有熟悉編輯Windows註冊表的系統管理員才應進行以下更改：

1. 使用&#x200B;**[!UICONTROL Start > Run]**&#x200B;菜單中的&#x200B;**regedit**&#x200B;命令開啟註冊表編輯器。

1. 搜尋節點並展開它。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除&#x200B;**confDescuredUpgrade**&#x200B;條目並關閉註冊表編輯器。

>[!NOTE]
>
>如果您將更新的主控台套用至現有實作，使用者會自動收到更新其用戶端主控台的提示。 如果您是第一次實作Campaign，使用者將需要下載主控台。 請參閱下文，了解有關這兩個選項的詳細資訊

### 更新現有實作的主控台{#update-the-client-console}

一旦主控台可在Campaign伺服器資料夾中使用，系統就會在快顯視窗中提示使用者下載最新的用戶端主控台版本。

**使用者需要管理員存取權才能完成更新。如果用戶沒有管理員權限，則系統管理員需要部署到所有客戶端控制台**


### 下載主控台以進行新實作{#download-the-client-console}

使用者現在應依照下列步驟下載並安裝主控台：

1. 開啟Web瀏覽器，然後從以下地址下載控制台：

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. 在標識窗口中，輸入您的登錄名和密碼。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，請使用建立執行個體期間定義之內部帳戶的認證。

1. 按一下安裝頁面上的&#x200B;**[!UICONTROL Download]**&#x200B;連結。
1. 下載並保存客戶端安裝檔案。
1. 在Windows上執行下載的檔案：安裝程式隨即啟動。 根據您的Adobe Campaign版本，客戶端控制台的預設安裝路徑為&#x200B;**$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX客戶端**，其中「X」為「6」或「7」。

### 建立連線 — 僅限首次使用者{#create-the-connection}

安裝客戶端控制台後，請按照以下步驟建立與應用程式伺服器的連接：

1. 從&#x200B;**Adobe Campaign**&#x200B;程式組的Windows **[!UICONTROL Start]**&#x200B;菜單啟動控制台。

1. 按一下認證欄位右上角的連結，以存取連線設定視窗。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下&#x200B;**[!UICONTROL Add > Connection]** ，然後輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 透過URL指定與Adobe Campaign應用程式伺服器的連線。 使用電腦的DNS、別名或IP地址。

   例如，您可以使用[`https://<machine>.<domain>.com`](https://myserver.adobe.com)類型URL。

1. 如果貴組織已設定Adobe IMS，請核取選項&#x200B;**[!UICONTROL Connect with an Adobe ID]**

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以儲存設定。

例如，您可以視需要新增連線，以連線至您的測試、預備和生產環境。

>[!NOTE]
>
>**[!UICONTROL Add]**&#x200B;按鈕可讓您建立&#x200B;**[!UICONTROL folders]**&#x200B;來組織所有連線。 只需將每個連線拖放到資料夾中即可。

### 登入Adobe Campaign

若要登入現有執行個體，請遵循下列步驟：

1. 從&#x200B;**Adobe Campaign**&#x200B;程式組的Windows **[!UICONTROL Start]**&#x200B;菜單啟動控制台。

1. 按一下認證欄位右上角的連結，以存取連線設定視窗。

1. 選取您需要登入的Campaign執行個體。

1. 按一下 **[!UICONTROL Ok]**

1. 輸入用戶登錄憑據，然後按一下&#x200B;**[!UICONTROL Log in]**


**相關主題**

* [建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md).
* [相容性對較表](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

## 教學課程影片

此影片說明如何安裝和設定Adobe Campaign Client。

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

其他Campaign Classic操作說明影片可在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
