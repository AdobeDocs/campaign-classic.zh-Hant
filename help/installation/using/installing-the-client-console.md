---
title: 安裝客戶機控制台
seo-title: 安裝客戶機控制台
description: 安裝客戶機控制台
seo-description: null
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# 安裝客戶機控制台{#installing-the-client-console}

Adobe Campaign主控台安裝程式詳述如下。

在安裝Adobe Campaign主控台之前，請先檢查相容性矩陣中列出的必 [要條件](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

若要安裝Adobe Campaign主控台，請套用下列步驟：

1. 開啟網頁瀏覽器並從下列位址下載主控台：

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. 在標識窗口中，輸入您的登錄名和密碼。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，請使用在建立執行個體期間定義的內部帳戶認證。

1. 按一下安 **[!UICONTROL Download]** 裝頁面上的連結。
1. 下載並儲存用戶端設定檔案。
1. 在Windows上的電腦上執行下載的檔案：安裝即會啟動。 根據您的Adobe Campaign版本，用戶端主控台的預設安裝路徑是 **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**，其中&#39;X&#39;為&#39;6&#39;或&#39;7&#39;。
1. 安裝程式完成後，從Windows功能表(在 **[!UICONTROL Start]****Adobe Campaign程式群組中** )啟動主控台。

>[!NOTE]
>
>在Windows上，您可以直接從 **Windows伺服器上的目錄啟動nlclient.exe** 檔案，其中是 `[INSTALL]/bin``[INSTALL]` Adobe Campaign安裝檔案夾的存取路徑。\
>要建立新連接，請參 [閱建立實例和登錄](../../installation/using/creating-an-instance-and-logging-on.md)。

