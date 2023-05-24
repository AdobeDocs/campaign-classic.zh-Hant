---
product: campaign
title: 在Adobe Campaign中找到Tomcat版本
description: 瞭解如何找出在Adobe Campaign執行個體中使用的內嵌Tomcat Web servlet最新版本
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

# 找到Tomcat版本{#locate-tomcat-version}



Adobe Campaign使用 **稱為Apache Tomcat的內嵌Web servlet** 在應用程式和任何外部介面（包括使用者端主控台、追蹤的URL連結、SOAP呼叫等）之間處理HTTP/HTTPS請求。 在任何面對外部的Adobe Campaign執行個體中，通常有一個外部Web伺服器（通常是IIS或Apache）在這之前。

請依照下列程式操作，以找出使用於的Tomcat確切版本 **Campaign Classic內部部署執行個體** 以協助疑難排解問題。

## Adobe Campaign中使用的Tomcat

Tomcat會在Java上執行，並需要安裝JDK。 如需詳細資訊，請參閱「 」中的Java Development Kit (JDK) [Campaign相容性對照表](../../rn/using/compatibility-matrix.md) 區段。

Adobe Campaign中使用的Tomcat是自訂的內嵌版本，並未使用完整版一般可用的Tomcat的所有功能，且可能不會遭受完整版的所有漏洞。 Tomcat也不應該公開給外部網際網路，而公開的Adobe Campaign執行個體應該有外部網頁伺服器（IIS、Apache等） 在Tomcat前保護。

Tomcat內嵌版本的新版本或升級版本僅隨Adobe Campaign本身的新組建版本發行，不會作為Adobe Campaign組建以外的個別修補程式發行。

## 如何找到內嵌Tomcat的版本

若要在Adobe Campaign執行個體中找出內嵌Tomcat的版本，請遵循下列步驟。

>[!NOTE]
>
>您必須能存取Adobe Campaign伺服器上需要檢查的檔案。 以下所述的程式僅適用於 **內部部署託管模型**.

1. 導覽至 *\tomcat-7\lib* Adobe Campaign安裝資料夾中的子資料夾(例如， *C:\Program檔案\ [Installation_folder]* 在Windows中，或 */usr/local/neolane/nl6* （在Linux中）。

   如果您使用Tomcat v6執行較舊版本的Adobe Campaign，請使用 *\tomcat-6\lib*.

1. 複製檔案 *catalina.jar* 至外部暫存資料夾（例如您的案頭），並將副檔名從.jar重新命名為.zip。

1. 將複製的檔案解壓縮。 這會產生許多子資料夾和檔案。

1. 在解壓縮的檔案/資料夾中，使用文字編輯器開啟或讀取以下包含的檔案： *org/apache/catalina/util/ServerInfo.properties*. 您可能需要新增.txt副檔名，以利使用文字編輯器開啟。

1. 完成後，如果檔案位於伺服器電腦上，請刪除您建立的暫存檔案。

例如， *伺服器資訊。屬性* Adobe Campaign的檔案將包含下列資訊，指出Tomcat v8.5.X：

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.build=MM DD YYYY HH:MM:SS*

當您能夠建立用於特定執行個體的Tomcat確切版本後，它可能會協助您疑難排解Tomcat相關問題。

>[!NOTE]
>
>內嵌Tomcat的主要版本只有在Adobe Campaign的主要版本變更時才會升級（雖然舊版可能不再受到正式支援，但此資訊可能會有所幫助，因為有些客戶可能仍在執行這些版本）。
>
>例如，Adobe Campaign v6.02將一律使用Tomcat v6.x。
