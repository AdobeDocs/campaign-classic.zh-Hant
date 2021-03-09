---
solution: Campaign Classic
product: campaign
title: 隱私權
description: 進一步瞭解有關隱私權的最佳實務。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 4%

---


# 隱私權 {#privacy}

## 隱私權要求

Adobe Campaign 提供一套工具，以協助您遵循隱私權法規（GDPR、CCPA 等）。

請參閱[本頁](../../platform/using/privacy-management.md)以取得有關隱私權管理的一般資訊，以及Adobe Campaign的實作步驟。 您也會找到最佳實務，並概述使用者程式與角色。

## URL個人化

在將個人化連結新增至您的內容時，請務必避免URL的主機名稱部分有任何個人化，以避免潛在的安全性缺口。 以下範例不應用於所有URL屬性&lt;`a href="">`或`<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 建議

若要驗證並確保您未使用上述功能，請透過[促銷活動一般查詢編輯器](../../platform/using/steps-to-create-a-query.md)執行追蹤URL表格的查詢，或在[查詢活動](../../workflow/using/query.md)中建立具有篩選條件的工作流程。

範例:

1. 建立工作流程並新增查詢活動。 進一步了解.

1. 開啟「查詢」活動，並在nmsTrackingUrl表格上建立篩選，如下所示：來源URL以http://&lt;%開頭，或來源URL以https://&lt;%開頭。

1. 執行工作流程並檢查是否有結果。

1. 如果是，請開啟輸出轉場以檢視URL清單。

<img src="assets/privacy-query-dynamic-url.png">

### 簽名機制

為了改善安全性，Build 19.1.4(9032@3a9dc9c)中已引進新的電子郵件追蹤連結簽名機制，Build 19.1.4(9032@3a9dc9c)和Campaign 20.2中也提供此機制。預設會為所有客戶啟用此選項。

>[!NOTE]
>
>當點按格式錯誤的簽名URL時，會傳回下列錯誤：&quot;找不到請求的URL &#39;... &#39;。&quot;

此外，Build 19.1.4(9032@3a9dc9c和9032@800be2e)和Campaign 20.2的代管和混合型客戶可使用增強功能來停用從舊版建置產生的URL。 此選項預設為停用。 您可以聯絡[客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以啟用此功能。

若要啟用此新機制，內部部署客戶必須在所有Campaign伺服器上執行下列步驟：

1. 在伺服器設定檔(serverConf.xml)中，將&#x200B;**blockRedirectForUnsignedTrackingLink**&#x200B;變更為&#x200B;**true**。
1. 重新啟動&#x200B;**nlserver**&#x200B;服務。
1. 在追蹤伺服器上，重新啟動Web伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

在Build 19.1.4(9032@3a9dc9c)上執行的客戶可能會在使用追蹤連結進行推播通知傳送或使用錨記進行傳送時遇到問題。 如果是，Adobe建議停用追蹤連結的新簽名機制：

**代管和混合** 式客戶必須聯絡 [客](https://helpx.adobe.com/tw/enterprise/using/support-for-experience-cloud.html) 戶服務，以停用此機制。

**內部部署** 客戶遵循下列步驟：

1. 在伺服器設定檔(serverConf.xml)中，將&#x200B;**signEmailLinks**&#x200B;變更為&#x200B;**false**。
1. 重新啟動&#x200B;**nlserver**&#x200B;服務。
1. 在追蹤伺服器上，重新啟動Web伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

## 資料限制

您必須確保已加密密碼無法由低權限的已驗證用戶訪問。 要做到這一點，有兩種主要方式：僅限存取密碼欄位或整個實體（需要組建版本>= 8770）。

此限制允許您刪除密碼欄位，但允許所有用戶從介面訪問外部帳戶。 請參見[此頁面](../../configuration/using/restricting-pii-view.md)。

1. 進入&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**。

1. 建立新的&#x200B;**[!UICONTROL Extension of a schema]**。

   ![](assets/privacy-data-restriction.png)

1. 選擇&#x200B;**[!UICONTROL External Account]**(extAccount)。

1. 在最後一個精靈畫面中，您可以編輯新的srcSchema以限制對所有密碼欄位的存取：

   您可以以下列方式替換主要元素(`<element name="extAccount" ... >`):

   ```
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

   因此，擴展的srcSchema可以如下所示：

   ```
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
   >您可以將`$(loginId) = 0 or $(login) = 'admin'`依`hasNamedRight('admin')`移除，讓擁有管理員權限的所有使用者都能看到這些密碼。

## 保護包含PII的頁面

我們強烈建議內部部署客戶保護可能包含個人資訊（例如鏡像頁面、Web應用程式等）的頁面。

此程式的目標是防止這些頁面被編製索引，從而避免潛在的安全風險。 以下是一些有用的文章：

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

若要保護您的頁面，請依照下列步驟進行：

1. 在Web伺服器（Apache或IIS）的根目錄中添加robots.txt檔案。 以下是檔案的內容：

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   對於IIS，請參閱[此頁](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files)。

   對於Apache，您可將檔案置於&#x200B;**/var/www/robots.txt**(Debian)中。

1. 有時候，添加&#x200B;**robots.txt**&#x200B;檔案在安全性方面是不夠的。 例如，如果其他網站包含您頁面的連結，則可能會出現在搜尋結果中。

除了&#x200B;**robots.txt**&#x200B;檔案外，建議您新增&#x200B;**X-Robots-Tag**&#x200B;標題。 您可以在Apache或IIS以及&#x200B;**serverConf.xml**&#x200B;組態檔中執行此動作。

如需詳細資訊，請參閱[本文](https://developers.google.com/search/reference/robots_meta_tag)。
