---
product: campaign
title: 個人化與隱私
description: 瞭解隱私權與個人化的安全性最佳實務
feature: Installation, Privacy, Privacy Tools, URL Personalization
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
TQID: 'https://experienceleague.adobe.com/8u-ItsbouC0wIsamVYfyzQR1o-z-jY90Z3pKem-yarc'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
    internal-label: Security and privacy
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
subfeature_v2:
  - id: ac72e249-ebbf-4bb6-96c9-596af925419a
    internal-label: Privacy tools
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
    internal-label: Privacy
  - id: fb2a841f-c522-491f-9901-a1b939d252df
    internal-label: Security
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: f55cfb22-471c-4161-8ea1-12868351e460
    internal-label: URL personalization
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: 0fdce84d7da1ff42a406ace8f1a180f6a426646a
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 3%
---
# 個人化與隱私 {#privacy}

本頁涵蓋URL個人化、URL簽名以及包含個人資訊的頁面的保護。

>[!NOTE]
>
>作為從Campaign v7轉變到v8的一部分，Campaign Classic檔案集已簡化並重新組織。 Campaign v8檔案集中現在提供常見功能。 若要進一步瞭解資料限制和隱私權要求，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/privacy/security#data-restriction){target=_blank}。
>
>[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/privacy/security#data-restriction){target="_blank"}

在Campaign Classic v7中，限制存取整個實體需要版本編號8770或更新版本。

## URL PERSONALIZATION {#url-personalization}

將個人化連結新增至您的內容時，請一律避免URL的主機名稱部分有任何個人化專案，以避免潛在的安全性缺口。 下列範例絕不應該用於所有URL屬性&lt;`a href="">`或`<img src="">`：

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 建議

若要驗證並確保您未使用上文，請透過[Campaign一般查詢編輯器](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/data/query/query-editor){target="_blank"} （Campaign v8檔案）對追蹤URL表格執行查詢，或在查詢活動中建立具有篩選條件的工作流程。 請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=zh-Hant){target="_blank"}。

範例：

1. 建立工作流程並新增&#x200B;**查詢**&#x200B;活動。 請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=zh-Hant){target="_blank"}。

1. 開啟&#x200B;**查詢**&#x200B;活動並在`nmsTrackingUrl`資料表上建立篩選器，如下所示：

   `source URL starts with http://<% or source URL starts with https://<%`

1. 執行工作流程並檢查是否有結果。

1. 若是如此，請開啟輸出轉變以檢視URL清單。

   ![](assets/privacy-query-dynamic-url.png)


### URL簽章

為了提高安全性，我們引進了簽名機制，用於追蹤電子郵件中的連結。 它會從19.1.4 (9032@3a9dc9c)和20.2版本開始提供。 此功能預設為啟用。

>[!NOTE]
>
>按一下格式錯誤的已簽署URL時，會傳回此錯誤： `Requested URL '…' was not found.`

此外，您可以使用增強功能來停用先前組建中產生的URL。 此功能預設為停用。 您可以聯絡[客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以啟用此功能。

如果您在19.1.4版本編號上執行，則可能會在使用追蹤連結或使用錨點標籤的推播通知傳送中遇到問題。 若是如此，建議您停用URL簽章。

身為行銷活動託管、受管理的Cloud Services或混合型客戶，您必須聯絡[客戶服務](https://helpx.adobe.com/tw/enterprise/using/support-for-experience-cloud.html)以停用URL簽章。

如果您在混合架構中執行Campaign，在啟用URL簽名之前，請確定已依下列方式升級代管的中間來源執行個體：

* 先使用內部部署行銷執行個體
* 然後升級至與內部部署行銷執行個體相同的版本或稍微更高的版本

否則，可能會發生以下部分問題：

* 在升級中間來源執行個體之前，會透過此執行個體傳送URL，而不使用簽名。
* 升級中間來源執行個體並在兩個執行個體上啟用URL簽名後，先前未經簽名而傳送的URL會遭到拒絕。 原因是行銷執行個體提供的追蹤檔案需要簽名。

若要停用先前組建中產生的URL，請同時在所有Campaign伺服器上執行下列步驟：

1. 在伺服器設定檔(`serverConf.xml`)中，將&#x200B;**blockRedirectForUnsignedTrackingLink**&#x200B;選項變更為&#x200B;**true**。
1. 重新啟動`nlserver`服務。
1. 在`tracking`伺服器上，重新啟動`web`伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

若要啟用URL簽名，請同時在所有Campaign伺服器上執行下列步驟：

1. 在伺服器設定檔(`serverConf.xml`)中，將&#x200B;**signEmailLinks**&#x200B;選項變更為&#x200B;**true**。
1. 重新啟動&#x200B;**nlserver**&#x200B;服務。
1. 在`tracking`伺服器上，重新啟動`web`伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

## 使用PI保護頁面

我們強烈建議內部部署客戶保護可能包含個人資訊(PI)的頁面，例如映象頁面、網頁應用程式等。

此程式的目標是防止這些頁面被編制索引，從而避免潛在的安全性風險。 以下是一些實用的文章：

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

若要保護您的頁面，請遵循下列步驟：

1. 在網頁伺服器（Apache或IIS）的根目錄新增`robots.txt`檔案。 以下是檔案的內容：

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   若為IIS，請參閱[此頁面](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files)。

   若為Apache，您可以將檔案放在&#x200B;**/var/www/robots.txt** (Debian)中。

1. 有時新增&#x200B;**robots.txt**&#x200B;檔案的安全性不足。 例如，如果其他網站包含您頁面的連結，它可能會出現在搜尋結果中。

   除了&#x200B;**robots.txt**&#x200B;檔案，建議新增&#x200B;**X-Robots-Tag**&#x200B;標頭。 您可以在Apache或IIS以及&#x200B;**serverConf.xml**&#x200B;設定檔中執行此作業。

   如需詳細資訊，請參閱[本文章](https://developers.google.com/search/reference/robots_meta_tag)。
