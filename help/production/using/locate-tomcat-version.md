---
product: campaign
title: 在Adobe Campaign中找到Tomcat版本
description: 瞭解如何確定Adobe Campaign執行個體中使用的內嵌Tomcat Web servlet的目前版本
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: fd4a815bca23b94590012c4883cfaa9c29b6f118
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# 找到Tomcat版本{#locate-tomcat-version}

Adobe Campaign使用名為Apache Tomcat **的**&#x200B;內嵌Web servlet來處理應用程式與任何外部介面(包括使用者端主控台、追蹤的URL連結、SOAP呼叫等)之間的HTTP/HTTPS要求。 在任何面對外部的Adobe Campaign執行個體中，通常有一個外部網頁伺服器（通常是IIS或Apache）位於此伺服器之前。

請依照下列程式，找出用於&#x200B;**Campaign Classic內部部署執行個體**&#x200B;的確切版本Tomcat，以協助疑難排解問題。

## Adobe Campaign中使用的Tomcat

Tomcat會在Java上執行，並需要安裝JDK。 如需詳細資訊，請參閱[Campaign相容性矩陣](../../rn/using/compatibility-matrix.md)一節中的Java開發套件(JDK)。

Adobe Campaign中使用的Tomcat是自訂的內嵌版本，該版本未使用Tomcat完整一般可用版本的所有功能，並且可能沒有完整版本的所有漏洞。 Tomcat也不應該公開給外部網際網路，而任何公開的Adobe Campaign執行個體都應該有外部網頁伺服器（IIS、Apache等） 在Tomcat前保護它。

Tomcat內嵌版本的新版本或升級版本只會隨Adobe Campaign本身的新組建發行，而不會作為Adobe Campaign組建以外的個別修補程式發行。

>[!AVAILABILITY]
>
>
>* 從Campaign v7.4.1開始，Tomcat 10.1是預設版本。
>
>* Adobe Campaign Classic不使用WebSocket和HTTP2通訊協定。
>


## 如何找到內嵌Tomcat的版本

若要在Adobe Campaign執行個體中找出內嵌Tomcat的版本，請遵循下列步驟。

>[!NOTE]
>
>您必須擁有Adobe Campaign伺服器上需要檢查之檔案的存取權。 下列程式僅適用於&#x200B;**內部部署託管模型**。

1. 導覽至Adobe Campaign安裝資料夾內的&#x200B;*\tomcat-11\lib*&#x200B;子資料夾(例如，在Windows中為&#x200B;*C:\Program Files\ [Installation_folder]*，或在Linux中為&#x200B;*/usr/local/neolane/nl6*)。

1. 將檔案&#x200B;*catalina.jar*&#x200B;複製到外部的暫存資料夾（例如您的案頭），並將副檔名從.jar重新命名為.zip。

1. 將複製的檔案解壓縮。 這會產生許多子資料夾和檔案。

1. 在解壓縮的檔案/資料夾中，使用文字編輯器開啟或讀取下列包含的檔案： *org/apache/catalina/util/ServerInfo.properties*。 您可能需要新增.txt副檔名，以利使用文字編輯器開啟。

1. 完成後，如果檔案位於伺服器電腦上，請刪除您建立的暫存檔案。

例如，Adobe Campaign的&#x200B;*ServerInfo.properties*&#x200B;檔案包含下列資訊，指出Tomcat v11.X：

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

當您能夠建立用於特定執行個體的Tomcat的精確版本後，它可以幫助您疑難排解Tomcat相關問題。

>[!NOTE]
>
>內嵌Tomcat的主要版本只有在Adobe Campaign的主要版本變更時才會升級（雖然較舊版本可能不再受到正式支援，但此資訊可能有所幫助，因為有些客戶可能仍在執行這些版本）。
>

