---
product: campaign
title: 隱私權
description: 進一步了解有關隱私權的最佳實務。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 5%

---

# 隱私權 {#privacy}

## 隱私權要求

Adobe Campaign 提供一套工具，以協助您遵循隱私權法規（GDPR、CCPA 等）。

如需隱私權管理的一般資訊，請參閱[本頁面](../../platform/using/privacy-management.md)以及Adobe Campaign中的實作步驟。 您也會找到最佳實務，並概述使用者程式和角色。

## URL個人化{#url-personalization}

將個人化連結新增至內容時，請一律避免URL的主機名稱部分出現任何個人化，以避免潛在的安全漏洞。 所有URL屬性&lt;`a href="">`或`<img src="">`中一律不應使用下列範例：

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 建議

若要驗證並確保您未使用上述功能，請透過[促銷活動一般查詢編輯器](../../platform/using/steps-to-create-a-query.md)執行追蹤URL表格的查詢，或在[查詢活動](../../workflow/using/query.md)中使用篩選條件建立工作流程。

範例:

1. 建立工作流程並新增「查詢」活動。 瞭解更多。

1. 開啟「查詢」活動，並依照下列方式在nmsTrackingUrl表格上建立篩選器：源URL以http://&lt;%開頭，或源URL以https://&lt;%開頭。

1. 執行工作流程並檢查是否有結果。

1. 若存在，請開啟輸出轉變以檢視URL清單。

<img src="assets/privacy-query-dynamic-url.png">

### 簽名機制

為了改善安全性，在版本編號19.1.4(9032@3a9dc9c)中推出了新的電子郵件追蹤連結簽名機制，並在版本編號19.1.4(9032@3a9dc9c)和Campaign 20.2中提供。依預設，會為所有客戶啟用此選項。

>[!NOTE]
>
>點按格式錯誤的簽名URL時，會傳回下列錯誤：&quot;未找到請求的URL &#39;..&#39;。&quot;

此外，自Campaign 20.2和[!DNL Gold Standard]發行版本開始，托管和混合客戶可使用增強功能來停用從舊版組建產生的URL。 預設會停用此選項。 您可以聯絡[客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)以啟用此功能。

若要啟用此新機制，內部部署客戶必須在所有Campaign伺服器上遵循下列步驟：

1. 在伺服器配置檔案(serverConf.xml)中，將&#x200B;**blockRedirectForUnsignedTrackingLink**&#x200B;更改為&#x200B;**true**。
1. 重新啟動&#x200B;**nlserver**&#x200B;服務。
1. 在追蹤伺服器上，重新啟動Web伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

在[!DNL Gold Standard] 19.1.4上執行的客戶可能會在使用追蹤連結的推播通知傳送，或使用錨點標籤的傳送發生問題。 若存在，Adobe建議停用追蹤連結的新簽章機制：

**托管和混合** 客戶必須聯絡客戶 [服務](https://helpx.adobe.com/tw/enterprise/using/support-for-experience-cloud.html) 人員，才能停用此機制。

**內部部署** 客戶遵循下列步驟：

1. 在伺服器配置檔案(serverConf.xml)中，將&#x200B;**signEmailLinks**&#x200B;更改為&#x200B;**false**。
1. 重新啟動&#x200B;**nlserver**&#x200B;服務。
1. 在追蹤伺服器上，重新啟動Web伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

## 資料限制

您必須確保已加密密碼無法由低權限已驗證的使用者存取。 要做到這一點，有兩種主要方式：僅限訪問密碼欄位或限制訪問整個實體（需要生成>= 8770）。

此限制可讓您移除密碼欄位，但讓所有使用者都能從介面存取外部帳戶。 請參見[此頁面](../../configuration/using/restricting-pii-view.md)。

1. 前往&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**。

1. 建立新的&#x200B;**[!UICONTROL Extension of a schema]**。

   ![](assets/privacy-data-restriction.png)

1. 選擇&#x200B;**[!UICONTROL External Account]**(extAccount)。

1. 在最後一個嚮導螢幕中，您可以編輯新的srcSchema以限制對所有密碼欄位的訪問：

   您可以以下列方式取代主要元素(`<element name="extAccount" ... >`):

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

   因此，您的延伸srcSchema看起來可能像：

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
   >您可以透過`hasNamedRight('admin')`移除`$(loginId) = 0 or $(login) = 'admin'`，讓所有具有管理員權限的使用者看到這些密碼。

## 保護包含PII的頁面

我們強烈建議內部部署客戶保護可能包含個人資訊的頁面，例如鏡像頁面、網頁應用程式等。

此程式的目標是防止這些頁面被索引，從而避免潛在的安全風險。 以下是一些實用的文章：

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

若要保護您的頁面，請依照下列步驟操作：

1. 在Web伺服器（Apache或IIS）的根目錄中新增robots.txt檔案。 以下是檔案的內容：

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   若為IIS，請參閱[此頁面](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files)。

   若使用Apache，您可以將檔案放在&#x200B;**/var/www/robots.txt**(Debian)中。

1. 有時候，添加&#x200B;**robots.txt**&#x200B;檔案在安全性方面是不夠的。 例如，如果其他網站包含您頁面的連結，則可能會顯示在搜尋結果中。

除了&#x200B;**robots.txt**&#x200B;檔案外，還建議添加&#x200B;**X-Robots-Tag**&#x200B;標題。 您可以在Apache或IIS中，以及在&#x200B;**serverConf.xml**&#x200B;配置檔案中執行此操作。

如需詳細資訊，請參閱[本文章](https://developers.google.com/search/reference/robots_meta_tag)。
