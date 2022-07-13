---
product: campaign
title: 安裝客戶端主控台
description: 瞭解如何安裝客戶端控制台
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 0f63636e9cc22ac97e634a4f11dc585cb39b05c0
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 4%

---

# 安裝和更新市場活動客戶端控制台{#installing-the-client-console}

![](../../assets/v7-only.svg)

市場活動客戶端控制台是一個富客戶端，它使您能夠連接到市場活動應用程式伺服器。

在開始安裝客戶端控制台之前，您需要：

* 檢查您的系統和工具與Adobe Campaign的相容性 [相容性矩陣](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* 獲取您的市場活動伺服器URL
* 獲取您的用戶憑據

安裝或更新客戶端控制台的過程因您對Adobe Campaign Classic的實施而不同。
請查看下面的詳細資訊，瞭解實施需要什麼。

![](assets/do-not-localize/how-to-video.png) 瞭解如何在中安裝和設定Adobe Campaign客戶端 [視頻](#video)

>[!CAUTION]
>
>市場活動客戶端控制台和市場活動應用程式伺服器必須運行 **同一產品版本**。 Adobe還強烈建議使用 **同一產品**。 瞭解如何在中檢查市場活動客戶端和伺服器版本 [此部分](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

## Adobe托管實施 {#hosted-customers}

作為托管客戶，您有兩個選項可安裝或更新客戶端控制台：

1. Adobe可以直接部署。 控制台更新後，系統將提示用戶在彈出窗口中下載最新的客戶端控制台版本。

1. 您可以從下載到客戶端控制台 [軟體分發](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)

   **用戶需要管理員訪問權限才能完成更新。 如果用戶沒有管理員權限，則系統管理員需要部署到所有客戶端控制台**

## 混合和本地實施 {#hybrid-onprem-customers}

要使Adobe Campaign用戶能夠登錄到您建立和配置的實例，他們需要使用客戶端控制台。

### 使控制台可供用戶使用 {#make-console-available}

當用於啟動Adobe Campaign應用程式伺服器(nlserver web)的電腦從客戶端控制台接收用戶連接時，您可以配置它，使Adobe Campaign富客戶端的安裝程式通過HTML介面可用。 只要有新版本的客戶端控制台可用，用戶在啟動其客戶端控制台時將被邀請下載。

為此，您必須：

1. 選擇包含控制台安裝程式的包。

   此檔案稱為v7的setup-client-7.X.XXXX.exe或v6.1的setup-client-6.X.XXXX.exe，其中X是Adobe Campaign的子版本，XXXX是內部版本號。

1. 將此包複製並貼上到Adobe Campaign安裝資料夾（在混合安裝的市場營銷伺服器上）的/datakit/nl/eng/jsp下。

1. 啟動Adobe Campaign伺服器。


### 不再問此問題選項

Adobe建議保留 **[!UICONTROL No longer ask this question]** 未選定，以確保在新版本的控制台可用時向所有用戶發出警報。  如果選擇此選項，則用戶將不會獲悉新的可用版本。

如果 **[!UICONTROL No longer ask this question]**  已選擇，您可以重置此提示。 只有能夠編輯Windows註冊表的系統管理員才應進行以下更改：

1. 使用 **雷吉** 命令 **[!UICONTROL Start > Run]** 的子菜單。

1. 搜索節點並展開它。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除 **confAdvisedUpgrade** 並關閉註冊表編輯器。

>[!NOTE]
>
>如果將更新的控制台應用到現有實現，用戶將自動收到更新其客戶端控制台的提示。 如果您首次實施市場活動，則用戶需要下載控制台。 請參見下面，瞭解有關這兩個選項的詳細資訊

### 更新控制台以實現現有實現{#update-the-client-console}

控制台在「市場活動伺服器」資料夾中可用後，系統會提示用戶在彈出窗口中下載最新的客戶端控制台版本。

**用戶需要管理員訪問權限才能完成更新。 如果用戶沒有管理員權限，則系統管理員需要部署到所有客戶端控制台**


### 下載控制台以執行新實施{#download-the-client-console}

用戶現在應按照以下步驟下載並安裝控制台：

1. 開啟Web瀏覽器，然後從以下地址下載控制台：

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`。

1. 在標識窗口中，輸入登錄和密碼。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，請使用在實例建立過程中定義的內部帳戶的憑據。

1. 按一下 **[!UICONTROL Download]** 連結。
1. 下載並保存客戶端安裝檔案。
1. 在Windows上的電腦上執行下載的檔案：安裝開始。 客戶端控制台的預設安裝路徑是 **$PROGRAMFILES$/Adobe/Adobe Campaign ClassicvX客戶端**，其中&#39;X&#39;是&#39;6&#39;或&#39;7&#39;，根據您的Adobe Campaign版本。

### 建立連接 — 僅首次用戶{#create-the-connection}

安裝客戶端控制台後，請按照以下步驟建立與應用程式伺服器的連接：

1. 從Windows啟動控制台 **[!UICONTROL Start]** 的 **Adobe Campaign** 程式組。

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下 **[!UICONTROL Add > Connection]** 並輸入Adobe Campaign應用伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通過URL指定到Adobe Campaign應用程式伺服器的連接。 使用DNS或電腦的別名或IP地址。

   例如，您可以使用 [`https://<machine>.<domain>.com`](https://myserver.adobe.com) 鍵。

1. 如果為您的組織配置了Adobe IMS，請檢查選項 **[!UICONTROL Connect with an Adobe ID]**

1. 按一下 **[!UICONTROL Ok]** 的子菜單。

例如，您可以根據需要添加多個連接以連接到test、舞台和生產環境。

>[!NOTE]
>
>的 **[!UICONTROL Add]** 按鈕，您可以建立 **[!UICONTROL folders]** 來組織你的所有聯繫。 只需將每個連線拖放到資料夾中即可。

### 登錄Adobe Campaign

要登錄到現有實例，請執行以下步驟：

1. 從Windows啟動控制台 **[!UICONTROL Start]** 的 **Adobe Campaign** 程式組。

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。

1. 選擇要登錄的市場活動實例。

1. 按一下 **[!UICONTROL Ok]**

1. 輸入用戶登錄憑據，然後按一下 **[!UICONTROL Log in]**


**相關主題**

* [建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md).
* [相容性對較表](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

## 教程視頻

此視頻顯示如何安裝和設定Adobe Campaign客戶端。

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

可提供其他Campaign Classic操作視頻 [這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)。
