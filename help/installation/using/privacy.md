---
product: campaign
title: 隱私權
description: 進一步了解有關隱私權的最佳實務
feature: URL Personalization, Privacy
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: 0e57ffba9b8c7fd05843c3353d2c0d64cbc83b8b
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 2%

---

# 個人化與隱私 {#privacy}

![](../../assets/v7-only.svg)


## URL個人化 {#url-personalization}

將個人化連結新增至內容時，請一律避免URL的主機名稱部分出現任何個人化，以避免潛在的安全漏洞。 所有URL屬性中一律不應使用下列範例&lt;`a href="">` 或 `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 建議

若要驗證並確認您未使用上述項目，請透過 [Campaign一般查詢編輯器](../../platform/using/steps-to-create-a-query.md) 或在 [查詢活動](../../workflow/using/query.md).

範例:

1. 建立工作流程並新增 **查詢** 活動。 [了解更多資訊](../../workflow/using/query.md)。

1. 開啟 **查詢** 活動和建立篩選器 `nmsTrackingUrl` 表如下：

   `source URL starts with http://<% or source URL starts with https://<%`

1. 執行工作流程並檢查是否有結果。

1. 若存在，請開啟輸出轉變以檢視URL清單。

   ![](assets/privacy-query-dynamic-url.png)


### URL簽名

為了改善安全性，引入了追蹤電子郵件中連結的簽名機制。 自組建版本19.1.4(9032@3a9dc9c)和20.2開始，即可使用。此功能預設為啟用。

>[!NOTE]
>
>點按格式錯誤的簽名URL時，會傳回此錯誤： `Requested URL '…' was not found.`

此外，您可以使用增強功能來停用先前組建中產生的URL。 此功能預設為停用。 您可以聯絡 [客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 啟用此功能。

如果您是在19.1.4組建版本上執行，則使用追蹤連結的推播通知傳送或使用錨點標籤的傳送可能會發生問題。 若有，建議您停用URL簽章。

作為托管的促銷活動、受管理的Cloud Services或混合客戶，您必須聯絡 [客戶服務](https://helpx.adobe.com/tw/enterprise/using/support-for-experience-cloud.html) 來停用URL簽名。

如果您是以混合架構執行Campaign，在啟用URL簽章之前，請確定托管的中間來源執行個體已升級如下：

* 首先是內部部署行銷例項
* 然後升級至與內部部署行銷執行個體相同的版本或稍高的版本

否則，可能會發生以下問題：

* 在升級中間來源例項之前，URL會透過此例項傳送，且無簽名。
* 在中間來源執行個體升級且兩個執行個體上都啟用URL簽章後，先前未透過簽章而傳送的URL會遭拒。 原因是行銷執行個體提供的追蹤檔案會要求籤名。

若要停用先前組建中產生的URL，請同時在所有Campaign伺服器上執行下列步驟：

1. 在伺服器配置檔案(`serverConf.xml`)，變更 **blockRedirectForUnsignedTrackingLink** 選項 **true**.
1. 重新啟動 `nlserver` 服務。
1. 在 `tracking` 伺服器，重新啟動 `web` 伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

若要啟用URL簽章，請同時在所有Campaign伺服器上執行下列步驟：

1. 在伺服器配置檔案(`serverConf.xml`)，變更 **signEmailLinks** 選項，至 **true**.
1. 重新啟動 **nlserver** 服務。
1. 在 `tracking` 伺服器，重新啟動 `web` 伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

## 資料限制

您必須確保已驗證的低權限用戶無法訪問加密密碼。 要執行此操作，請僅限訪問密碼欄位，或限制訪問整個實體（需要生成>= 8770）。

此限制可讓您移除密碼欄位，但讓所有使用者都能從介面存取外部帳戶。 [了解更多資訊](../../configuration/using/restricting-pii-view.md)。

若要執行此作業，請遵循下列步驟：

1. 瀏覽至 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** Campaign檔案總管的資料夾。

1. 建立資料結構，作為 **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. 選擇 **[!UICONTROL External Account]** (extAccount)。

1. 在最後一個嚮導螢幕中，編輯新的「srcSchema」以限制對所有密碼欄位的訪問：

   您可以取代主要元素(`<element name="extAccount" ... >`)依據：

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

   因此，您的延伸srcSchema看起來可能像：

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
   >您可以取代 `$(loginId) = 0 or $(login) = 'admin'` with `hasNamedRight('admin')` 允許所有具有管理員權限的使用者查看這些密碼。

## Protect頁面（含PI）

我們強烈建議內部部署客戶保護可能包含個人資訊(PI)的頁面，例如鏡像頁面、Web應用程式等。

此程式的目標是防止這些頁面被索引，從而避免潛在的安全風險。 以下是一些實用的文章：

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

若要保護您的頁面，請依照下列步驟操作：

1. 新增 `robots.txt` 檔案（Apache或IIS）。 以下是檔案的內容：

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   對於IIS，請參閱 [本頁](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   若使用Apache，您可將檔案置於 **/var/www/robots.txt** (Debian)。

1. 有時會新增 **robots.txt** 檔案在安全性方面不夠。 例如，如果其他網站包含您頁面的連結，則可能會顯示在搜尋結果中。

   除了 **robots.txt** 檔案，建議您新增 **X-Robots-Tag** 頁首。 您可以在Apache或IIS中執行，並在 **serverConf.xml** 設定檔。

   如需詳細資訊，請參閱 [這篇文章](https://developers.google.com/search/reference/robots_meta_tag).


## 隱私權請求

請參閱 [本頁](../../platform/using/privacy-management.md) 如需隱私權管理的一般資訊，以及Adobe Campaign中的實作步驟。 您也會找到最佳實務，並概述使用者程式和角色。
