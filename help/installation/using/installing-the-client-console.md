---
solution: Campaign Classic
product: campaign
title: 安裝客戶端主控台
description: 瞭解如何安裝客戶端控制台
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: cea4a26935312b1cb119a3fa671af7bf00788fe9
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 8%

---


# 安裝Campaign客戶端控制台{#installing-the-client-console}

促銷活動用戶端主控台是rich client，可讓您連線至您的促銷活動應用程式伺服器。

在開始之前，您必須檢查促銷活動[相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)，取得您的促銷活動伺服器URL和使用者認證。

>[!CAUTION]
>
>促銷活動用戶端主控台和促銷活動應用程式伺服器必須在相同的產品版本上執行。 Adobe也建議使用相同的產品組建版本。

![](assets/do-not-localize/how-to-video.png) 瞭解如何在視訊中安裝和設定Adobe Campaign用 [戶端](#video)

## 下載控制台{#download-the-client-console}

若要下載並安裝Adobe Campaign用戶端主控台，請遵循下列步驟：

1. 開啟網頁瀏覽器並從下列位址下載主控台：

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. 在標識窗口中，輸入您的登錄名和密碼。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，請使用在建立執行個體期間定義的內部帳戶認證。

1. 按一下安裝頁上的&#x200B;**[!UICONTROL Download]**&#x200B;連結。
1. 下載並儲存用戶端設定檔案。
1. 在Windows上的電腦上執行下載的檔案：安裝即會啟動。 根據您的Adobe Campaign版本，用戶端主控台的預設安裝路徑為&#x200B;**$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**，其中&#39;X&#39;為&#39;6&#39;或&#39;7&#39;。

>[!NOTE]
>
>在Windows上，您可以直接從Windows伺服器上的`[INSTALL]/bin`目錄啟動&#x200B;**nlclient.exe**&#x200B;檔案，其中`[INSTALL]`是Adobe Campaign安裝資料夾的存取路徑。

## 建立連接{#create-the-connection}

安裝客戶機控制台後，請按照以下步驟建立與應用程式伺服器的連接：

1. 從&#x200B;**Adobe Campaign**&#x200B;程式群組的Windows **[!UICONTROL Start]**&#x200B;功能表啟動主控台。

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下&#x200B;**[!UICONTROL Add > Connection]**，然後輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 指定透過URL連線至Adobe Campaign應用程式伺服器。 使用DNS或電腦的別名或您的IP地址。

   例如，您可以使用[`https://<machine>.<domain>.com`](https://myserver.adobe.com)類型URL。

1. 如果您的組織已設定Adobe IMS，請勾選&#x200B;**[!UICONTROL Connect with an Adobe ID]**&#x200B;選項

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以儲存您的設定。

例如，您可以視需要新增多個連線，以連線至測試、舞台和生產環境。

>[!NOTE]
>
>**[!UICONTROL Add]**&#x200B;按鈕可讓您建立&#x200B;**[!UICONTROL folders]**&#x200B;來組織所有連線。 只需將每個連線拖放到資料夾中即可。

## 登入Adobe Campaign

要登錄到現有實例，請執行以下步驟：

1. 從&#x200B;**Adobe Campaign**&#x200B;程式群組的Windows **[!UICONTROL Start]**&#x200B;功能表啟動主控台。

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。

1. 選取您登入時需要的促銷活動例項。

1. 按一下 **[!UICONTROL Ok]**

1. 輸入您的用戶登錄憑據，然後按一下&#x200B;**[!UICONTROL Log in]**

**相關主題**

* [建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md).
* [相容性矩陣](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## 教學課程影片

此影片說明如何安裝和設定Adobe Campaign Client。

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

其他Campaign Classic操作視訊可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
