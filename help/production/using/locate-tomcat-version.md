---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign中尋找Tomcat版本
description: 瞭解如何瞭解Adobe Campaign實例中使用的內嵌Tomcat網頁servlet的最新版本。
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 49e49d5e35d14a31236cc4f78188cdf77353fbbf
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---


# 查找Tomcat版本{#locate-tomcat-version}

Adobe Campaign使用&#x200B;**內嵌的網頁servlet（稱為Apache Tomcat**），處理應用程式與任何外部介面（包括用戶端主控台、追蹤的URL連結、SOAP呼叫等）之間的HTTP/HTTPS要求。 對於任何外部對應的Adobe Campaign例項，通常會有外部Web伺服器（通常是IIS或Apache）出現在此之前。

請依照下列步驟，瞭解&#x200B;**Campaign Classic內部部署實例**&#x200B;中使用的Tomcat確切版本，以協助疑難排解問題。

## Adobe Campaign中使用的Tomcat

Tomcat可在Java上執行，需要安裝JDK。 如需詳細資訊，請參閱[促銷活動相容性表](../../rn/using/compatibility-matrix.md)一節中的Java開發套件(JDK)。

Adobe Campaign中使用的Tomcat是自訂的內嵌版本，不會使用完整公開發行版Tomcat的所有功能，而且可能不會遭受完整版本的所有弱點。 Tomcat也不應暴露在外部網際網路，而公開的任何Adobe Campaign例項都應具有外部網路伺服器（IIS、Apache等） 在Tomcat前面保護它。

Tomcat的內嵌版本新版或升級版僅隨新版Adobe Campaign一起發行，而非作為Adobe Campaign版以外的個別修補程式發行。

## 如何找到嵌入式Tomcat版本

若要在Adobe Campaign實例中找到內嵌Tomcat的版本，請遵循下列步驟。

>[!NOTE]
>
>您必須擁有Adobe Campaign伺服器上需要檢查之檔案的存取權。 以下所述的程式僅適用於&#x200B;**內部部署代管模型**。

1. 導覽至Adobe Campaign安裝資料夾內的&#x200B;*\tomcat-7\lib*&#x200B;子資料夾(例如，在Windows中為&#x200B;*C:\Program Files\ [Installation_folder]*，或在Linux中為&#x200B;*/usr/local/neolane/nl6*)。

   如果您使用Tomcat v6執行舊版Adobe Campaign，請使用&#x200B;*\tomcat-6\lib*。

1. 將檔案&#x200B;*catalina.jar*&#x200B;複製到外部臨時資料夾（例如，您的案頭），並將副檔名從。jar更名為。zip。

1. 解壓縮複製的檔案。 會產生許多子檔案夾和檔案。

1. 在解壓縮的檔案／檔案夾中，使用文字編輯器開啟或讀取下列包含的檔案：*org/apache/catalina/util/ServerInfo.properties*。 您可能需要新增。txt副檔名，以利使用文字編輯器開啟。

1. 完成後，如果它位於伺服器電腦上，請刪除您建立的臨時檔案。

例如，Adobe Campaign的&#x200B;*ServerInfo.properties*&#x200B;檔案將包含下列資訊，指出Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DD YYY HH:MM:SS*

在您能夠確定特定實例中使用的Tomcat的確切版本後，它可能會幫助您排除與Tomcat相關的問題。

>[!NOTE]
>
>內嵌Tomcat的主要版本只有在Adobe Campaign的主要版本變更時才會升級（雖然舊版可能不再受官方支援，但是這些資訊可能會很有用，因為有些客戶可能仍在執行這些版本）。
>
>例如，Adobe Campaign 6.02版將一律使用Tomcat 6.x版。