---
product: campaign
title: 在Adobe Campaign查找Tomcat版本
description: 瞭解如何查找在Adobe Campaign實例中使用的嵌入式Tomcat WebServlet的當前版本
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# 查找Tomcat版本{#locate-tomcat-version}



Adobe Campaign使用 **嵌入式Web Servlet，稱為Apache Tomcat** 處理應用程式和任何外部介面（包括客戶端控制台、跟蹤的URL連結、SOAP調用等）之間的HTTP/HTTPS請求。 對於任何面向外部的Adobe Campaign實例，其前面通常有外部Web伺服器（通常為IIS或Apache）。

按照以下步驟查找Tomcat在 **Campaign Classic本地實例** 以幫助解決問題。

## Tomcat在Adobe Campaign

Tomcat在Java上運行，需要安裝JDK。 有關詳細資訊，請參閱 [市場活動相容性清單](../../rn/using/compatibility-matrix.md) 的子菜單。

在Adobe Campaign使用的Tomcat是一個自定義的嵌入式版本，它不使用Tomcat的完整通用版本的所有功能，並且可能不會遭受完整版本的所有漏洞。 Tomcat也不應暴露在外部Internet中，所暴露的任何Adobe Campaign實例都應具有外部Web伺服器（IIS、Apache等） 來保護它。

Tomcat的嵌入式版本的新版本或升級版本僅隨Adobe Campaign本身的新版本一起發佈，而不作為Adobe Campaign版本之外的單獨修補程式發佈。

## 如何定位嵌入式Tomcat的版本

要在Adobe Campaign實例中查找嵌入式Tomcat的版本，請執行以下步驟。

>[!NOTE]
>
>您必須有權訪問需要檢查的Adobe Campaign伺服器上的檔案。 下面描述的過程僅適用於 **本地托管模式**。

1. 導航到 *\tomcat7\lib* Adobe Campaign安裝資料夾中的子資料夾(例如， *C:\Program Files\ [安裝資料夾]* 或 */usr/local/neolane/nl6* 在Linux中)。

   如果您使用Tomcat v6運行舊版本的Adobe Campaign，請使用 *\tomcat-6\lib*。

1. 複製檔案 *卡塔琳娜·賈爾* 到外部臨時資料夾（例如，案頭），並將副檔名從.jar更名為.zip。

1. 解壓縮複製的檔案。 它將產生許多子資料夾和檔案。

1. 在解壓縮的檔案/資料夾中，使用文本編輯器開啟或讀取以下包含的檔案： *org/apache/catalina/util/ServerInfo.properties*。 您可能需要添加.txt副檔名，以便使用文本編輯器開啟。

1. 完成後，如果它位於伺服器電腦上，請刪除您建立的臨時檔案。

例如， *ServerInfo.properties* Adobe Campaign的檔案將包含以下資訊，表示Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.builtd=MM DD YY HH:MM:SS*

一旦能夠確定特定實例中使用的Tomcat的準確版本，它可能有助於您排除與Tomcat相關的問題。

>[!NOTE]
>
>只有在主要版本的Adobe Campaign更改時才升級嵌入式Tomcat的主要版本（雖然舊版本可能不再受官方支援，但該資訊可能很有用，因為一些客戶可能仍在運行這些版本）。
>
>例如，Adobe Campaign6.02版始終使用Tomcat 6.x版。
