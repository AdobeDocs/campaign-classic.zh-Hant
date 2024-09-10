---
product: campaign
title: 個人化與隱私
description: 瞭解隱私權與個人化的安全性最佳實務
feature: Installation, Privacy, Privacy Tools, URL Personalization
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 2%

---

# 個人化與隱私 {#privacy}

## URL PERSONALIZATION {#url-personalization}

將個人化連結新增至您的內容時，請一律避免URL的主機名稱部分有任何個人化專案，以避免潛在的安全性缺口。 下列範例絕不應該用於所有URL屬性&lt;`a href="">`或`<img src="">`：

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 建議

若要驗證並確保您未使用上述功能，請透過[Campaign一般查詢編輯器](../../platform/using/steps-to-create-a-query.md)對追蹤URL表格執行查詢，或在[查詢活動](../../workflow/using/query.md)中建立具有篩選條件的工作流程。

例如：

1. 建立工作流程並新增&#x200B;**查詢**&#x200B;活動。 [了解更多](../../workflow/using/query.md)。

1. 開啟&#x200B;**查詢**&#x200B;活動並在`nmsTrackingUrl`資料表上建立篩選器，如下所示：

   `source URL starts with http://<% or source URL starts with https://<%`

1. 執行工作流程並檢查是否有結果。

1. 若是如此，請開啟輸出轉變以檢視URL清單。

   ![](assets/privacy-query-dynamic-url.png)


### URL簽章

為了提高安全性，我們引進了簽名機制，用於追蹤電子郵件中的連結。 它會從19.1.4 (9032@3a9dc9c)和20.2版本開始提供。此功能預設為啟用。

>[!NOTE]
>
>按一下格式錯誤的已簽署URL時，會傳回此錯誤： `Requested URL '…' was not found.`

此外，您可以使用增強功能來停用先前組建中產生的URL。 此功能預設為停用。 您可以聯絡[客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以啟用此功能。

如果您在19.1.4版本編號上執行，則可能會在使用追蹤連結或使用錨點標籤的推播通知傳送中遇到問題。 若是如此，建議您停用URL簽章。

身為行銷活動託管、受管理的Cloud Service或混合型客戶，您必須聯絡[客戶服務](https://helpx.adobe.com/tw/enterprise/using/support-for-experience-cloud.html)以停用URL簽章。

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

## 資料限制

您必須確定加密密碼無法由低許可權驗證的使用者存取。 若要這麼做，請限制僅能存取密碼欄位，或存取整個實體（需要組建>= 8770）。

此限制可讓您移除密碼欄位，但允許所有使用者從介面存取外部帳戶。 [了解更多](../../configuration/using/restricting-pii-view.md)。

若要執行此作業，請依照下列步驟操作：

1. 瀏覽至Campaign檔案總管的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**&#x200B;資料夾。

1. 建立資料結構描述，做為&#x200B;**[!UICONTROL Extension of a schema]**。

   ![](assets/privacy-data-restriction.png)

1. 選擇&#x200B;**[!UICONTROL External Account]** (extAccount)。

1. 在上一個助理畫面中，編輯新的「srcSchema」以限制所有密碼欄位的存取權：

   您可以將主要元素(`<element name="extAccount" ... >`)取代為：

   ```sql
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   因此，您的擴充式srcSchema看起來可能像這樣：

   ```sql
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >您可以使用`hasNamedRight('admin')`取代`$(loginId) = 0 or $(login) = 'admin'`，讓所有具有管理員許可權的使用者都能檢視這些密碼。

## 具有PI的Protect頁面

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


## 隱私權請求

請參閱[此頁面](../../platform/using/privacy-management.md)，瞭解隱私權管理的一般資訊以及Adobe Campaign中的實作步驟。 您也會找到最佳實務，以及使用者程式和角色的概觀。
