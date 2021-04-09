---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign找到Tomcat版本
description: 瞭解如何瞭解Adobe Campaign實例中使用的嵌入式Tomcat Web servlet的當前版本。
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# 找到Tomcat版本{#locate-tomcat-version}

Adobe Campaign使用&#x200B;**內嵌的Web servlet，稱為Apache Tomcat**，處理應用程式與任何外部介面（包括用戶端主控台、追蹤的URL連結、SOAP呼叫等）之間的HTTP/HTTPS要求。 對於任何外部對應的Adobe Campaign實例，通常在此之前都有外部Web伺服器（通常為IIS或Apache）。

請依照下列程式，瞭解&#x200B;**Campaign Classic內部部署實例**&#x200B;中使用的Tomcat確切版本，以協助疑難排解問題。

## 用於Adobe Campaign的Tomcat

Tomcat可在Java上執行，需要安裝JDK。 如需詳細資訊，請參閱[促銷活動相容性表](../../rn/using/compatibility-matrix.md)一節中的Java開發套件(JDK)。

Adobe Campaign使用的Tomcat是自訂的嵌入式版本，它不使用完整公開發行版Tomcat的所有功能，並且可能不會遭受完整版本的所有弱點。 Tomcat也不應暴露在外部Internet中，所有暴露的Adobe Campaign實例都應具有外部Web伺服器（IIS、Apache等） 在Tomcat前面保護它。

Tomcat的嵌入式版本的新版本或升級版僅隨新版本的Adobe Campaign本身一起發行，而不是作為Adobe Campaign版本以外的單獨修補程式發行。

## 如何找到嵌入式Tomcat版本

要在Adobe Campaign實例中找到嵌入式Tomcat版本，請執行以下步驟。

>[!NOTE]
>
>您必須有權訪問需要檢查的Adobe Campaign伺服器上的檔案。 以下所述的程式僅適用於&#x200B;**內部部署代管模型**。

1. 導覽至Adobe Campaign安裝資料夾內的&#x200B;*\tomcat-7\lib*&#x200B;子資料夾(例如，在Windows中為&#x200B;*C:\Program Files\ [Installation_folder]*，或在Linux中為&#x200B;*/usr/local/neolane/nl6*)。

   如果您使用Tomcat v6運行舊版Adobe Campaign，請使用&#x200B;*\tomcat-6\lib*。

1. 將檔案&#x200B;*catalina.jar*&#x200B;複製到外部臨時資料夾（例如，您的案頭），並將副檔名從。jar更名為。zip。

1. 解壓縮複製的檔案。 會產生許多子檔案夾和檔案。

1. 在解壓縮的檔案／檔案夾中，使用文字編輯器開啟或讀取下列包含的檔案：*org/apache/catalina/util/ServerInfo.properties*。 您可能需要新增。txt副檔名，以利使用文字編輯器開啟。

1. 完成後，如果它位於伺服器電腦上，請刪除您建立的臨時檔案。

例如，Adobe Campaign的&#x200B;*ServerInfo.properties*&#x200B;檔案將包含以下資訊，表示Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DD YYY HH:MM:SS*

在您能夠確定特定實例中使用的Tomcat的確切版本後，它可能會幫助您排除與Tomcat相關的問題。

>[!NOTE]
>
>嵌入式Tomcat的主要版本僅在Adobe Campaign主要版本更改時升級（雖然較舊版本可能不再得到正式支援，但這些資訊可能會很有用，因為某些客戶可能仍在運行這些版本）。
>
>例如，Adobe Campaignv6.02將一律使用Tomcat v6.x。
