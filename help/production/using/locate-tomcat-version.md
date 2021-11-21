---
product: campaign
title: 在Adobe Campaign中找到Tomcat版本
description: 了解如何找出Adobe Campaign例項中使用的內嵌Tomcat Web servlet的目前版本。
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# 找到Tomcat版本{#locate-tomcat-version}

![](../../assets/v7-only.svg)

Adobe Campaign使用 **名為Apache Tomcat的嵌入式Web servlet** 處理應用程式與任何外部介面（包括用戶端主控台、追蹤的URL連結、SOAP呼叫等）之間的HTTP/HTTPS要求。 對於任何面向外部的Adobe Campaign例項，此前通常會有外部Web伺服器（通常是IIS或Apache）。

請依照下列程式，了解 **Campaign Classic內部部署例項** 以協助疑難排解問題。

## 用於Adobe Campaign的Tomcat

Tomcat在Java上運行，需要安裝JDK。 如需詳細資訊，請參閱 [Campaign相容性矩陣](../../rn/using/compatibility-matrix.md) 區段。

Adobe Campaign中使用的Tomcat是自訂的內嵌版本，不會使用完整公開發行版Tomcat的所有功能，且可能不會受到完整版本的所有弱點影響。 也不應將Tomcat公開給外部internet，而公開的任何Adobe Campaign實例都應具有外部Web伺服器（IIS、Apache等） 來保護它。

新版或升級版本的Tomcat只會隨新的Adobe Campaign組建一起發行，而不會在Adobe Campaign組建之外以個別修補程式的形式發行。

## 如何定位嵌入式Tomcat的版本

要在Adobe Campaign實例中查找嵌入式Tomcat的版本，請執行以下步驟。

>[!NOTE]
>
>您必須擁有所需檢查之Adobe Campaign伺服器上之檔案的存取權。 下列程式僅適用於 **內部部署托管模型**.

1. 導覽至 *\tomcat7\lib* Adobe Campaign安裝資料夾中的子資料夾(例如 *C:\Program Files\ [Installation_folder]* 或 */usr/local/neolane/nl6* （在Linux）。

   如果您使用Tomcat v6執行舊版Adobe Campaign，請使用 *\tomcat6\lib*.

1. 複製檔案 *卡塔利娜.jar* 重新命名為外部臨時資料夾（例如您的案頭），並將副檔名從.jar重新命名為.zip。

1. 將複製的檔案解壓縮。 會產生許多子資料夾和檔案。

1. 在解壓縮的檔案/資料夾中，使用文本編輯器開啟或讀取以下包含的檔案： *org/apache/catalina/util/ServerInfo.properties*. 您可能需要新增.txt副檔名，以利使用文字編輯器開啟。

1. 完成後，如果它位於伺服器電腦上，請刪除您建立的臨時檔案。

例如， *ServerInfo.properties* Adobe Campaign的檔案將包含下列資訊，表示Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM DD YY HH:MM:SS*

在您能夠建立特定例項中使用的Tomcat的確切版本後，可能會有助於疑難排解Tomcat相關問題。

>[!NOTE]
>
>只有在主要版本的Adobe Campaign有所變更時，才會升級內嵌的Tomcat主要版本（雖然舊版可能不再受到正式支援，但這些資訊可能會很有用，因為某些客戶可能仍在執行這些版本）。
>
>例如，Adobe Campaign v6.02一律會使用Tomcat v6.x。
