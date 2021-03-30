---
solution: Campaign Classic
product: campaign
title: 伺服器組態
description: 進一步瞭解伺服器組態最佳實務。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 2%

---


# 伺服器配置{#server-configuration}

## 配置安全區

自構建8977起，安全區自助服務用戶介面不再提供。 如果您未在AWS上托管，請聯繫Adobe支援團隊，將IP添加到允許清單。 否則，必須將IP添加到允許清單中必須在[控制面板](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)中執行。

要檢查您的實例是否托管在AWS上，請遵循本頁[中詳細介紹的步驟。](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)

>[!NOTE]
> 
>所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本章節](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel)中。
>
>請注意，您的實例必須裝載在AWS上，並使用最新的[Gold Standard](../../rn/using/gs-overview.md)組建版本或[最新的GA組建版本(21.1)](../../rn/using/latest-release.md)進行升級。 瞭解如何在[本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的版本。


* 請確定子網中不允許您的反向代理。 如果是這樣，將檢測到&#x200B;**all**&#x200B;通信來自此本地IP，因此將受信任。

* 將sessionTokenOnly=&quot;true&quot;的使用降至最低：

   * 警告：如果此屬性設定為true，則操作員可以暴露在&#x200B;**CRSF攻擊**&#x200B;中。
   * 此外，sessionToken Cookie不會使用httpOnly標幟來設定，因此有些用戶端javascript程式碼可以讀取。
   * 但是，多個執行儲存格上的訊息中心需要sessionTokenOnly:建立新的安全區域，並將sessionTokenOnly設為&quot;true&quot;，並在此區域中僅新增所需的IP **。**

* 如果可能，請將allowHTTP、showErrors設為false（非localhost）並加以檢查。

   * allowHTTP = &quot;false&quot;:強制運算子使用HTTPS
   * showErrors = &quot;false&quot;:隱藏技術錯誤（包括SQL錯誤）。 它可避免顯示太多資訊，但降低行銷人員解決錯誤的能力（毋需向管理員要求更多資訊）

* 只有在行銷使用者／管理員使用的IP上，將allowDebug設為true，而這些IP需要建立（實際上是預覽）調查、webApps和報表。 此標誌允許這些IP獲得顯示的中繼規則並對它們進行調試。

* 請勿將allowEmptyPassword、allowUserPassword、allowSQLInjeption設為true。 這些屬性僅允許從v5和v6.0順暢移轉：

   * **allowEmptyPasswordlet** 運算子具有空密碼。如果是這種情況，請通知所有營運商要求他們在期限內設定密碼。 在此期限過後，請將此屬性變更為false。

   * **allowUserPasswordlets** 運算子會將其認證傳送為參數（因此會由apache/IIS/proxy記錄）。此功能過去曾用來簡化API使用。 您可以登入您的Cookbook（或在規格中），看看是否有某些協力廠商應用程式使用它。 如果是，您必須通知他們，以變更他們使用我們API的方式，並盡快移除此功能。

   * **allowSQLInjection** 可讓使用者使用舊語法來執行SQL插入。盡快執行[本頁](../../migration/using/general-configurations.md)中所述的更正，以便能夠將此屬性設定為false。 您可以使用/nl/jsp/ping.jsp?zones=true來檢查安全區配置。 此頁顯示當前IP的安全措施（使用這些安全標誌計算）的活動狀態。

* HttpOnly cookie/useSecurityToken:請參閱&#x200B;**sessionTokenOnly**&#x200B;旗標。

* 將新增至允許清單的IP降至最低：現在，在安全區中，我們為專用網路添加了3個範圍。 您不太可能使用這些IP位址。 所以只保留您需要的。

* 將webApp/internal運算子更新為只能在localhost中存取。

## 檔案上傳保護

使用nlclient/web介面，向操作用戶檢查他們上傳到伺服器的檔案類型。 提醒您，業務需求可以是：

* 影像(jpg、gif、png、...)
* 內容(zip、html、css、...)
* 行銷資產(doc、xls、pdf、psd、tiff...)
* 電子郵件附件(doc, pdf, ...)
* ETL(txt、csv、tab、...)
* 等等。

將所有這些內容都添加到serverConf/shared/datastore/@uploadAllowlist（有效的java規則運算式）中。 進一步瞭解[本頁](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files)。

Adobe Campaign不限制檔案大小。 但是，您可以通過配置IIS/Apache來實現。 進一步瞭解[本節](../../installation/using/web-server-configuration.md)。

## 中繼

如需詳細資訊，請參閱[本頁](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays)。

預設情況下，所有動態頁都會自動中繼到啟動Web模組的電腦的本地Tomcat伺服器。 你可以選擇不再轉讓其中一些。 如果您不使用某些Adobe Campaign模組（如webapp、交互、某些jsp），則可以從中繼規則中刪除這些模組。

現在，我們已強制使用http(httpAllowed=&quot;true&quot;)來顯示使用者資源。 由於這些頁面可顯示某些PII（例如電子郵件內容、地址）、兌換抵用券、優惠，因此您應在這些路徑上再次強制使用HTTPS。

如果您使用不同的主機名稱（一個公用主機名稱，另一個用於營運商），您也可以防止營運商在公用DNS名稱上傳送所需的部分資源。

## 傳出連線的保護

可由您的 Campaign Classic 執行個體的 JavaScript 程式碼 (工作流程等等) 呼叫之預設 URL 清單限制。 要允許新URL，管理員需要在[serverConf.xml檔案](../../installation/using/the-server-configuration-file.md)中引用它。

存在三種連接保護模式：

* **阻止** :不屬於允許清單的所有URL都被阻止，並出現錯誤消息。這是postupgrade之後的預設模式。
* **權限** :允許所有不屬於允許清單的URL。
* **警告** :不允許允許清單上的所有URL，但JS解譯器會發出警告，讓管理員可以收集這些URL。此模式添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

新客戶機將使用阻塞模式。 如果他們想要允許新的URL，則必須聯絡其管理員，才能將它新增至允許清單。

來自移轉的現有客戶可使用警告模式一段時間。 同時，在授權URLS之前，他們需要分析出站流量。

## 命令限制（伺服器端）

多個命令列入黑名單，無法使用execCommand函式執行。 專用的Unix用戶為執行外部命令提供了額外的安全性。 對於代管安裝，會自動套用此限制。 對於內部部署安裝，您可以按照[本頁](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)中的說明手動設定此限制。 此外，**[!UICONTROL Script]**&#x200B;和&#x200B;**[!UICONTROL External task]**&#x200B;工作流活動不可用（新安裝的實例）。

## 其他配置

您可以新增所有頁面的額外HTTP標題（如需詳細資訊，請參閱[本頁](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)）:

* 您可以新增一些額外的標題，例如HSTS、X-FRAME-OPTIONS、CSP...
* 您必須先在測試環境中進行測試，才能在生產中套用。

   >[!IMPORTANT]
   >
   >Adobe Campaign可以透過新增特定標題來劃分。

Adobe Campaign可讓您在`<dbcnx .../>`元素中設定簡單密碼。 請勿使用此功能。

依預設，Adobe Campaign不會將工作階段固定在特定IP上，但您可以啟用它，以防止工作階段被盜。 若要這麼做，請在[serverConf.xml檔案](../../installation/using/the-server-configuration-file.md)中，在`<authentication>`節點中將checkIPConsistent屬性設為&#x200B;**true**。

預設情況下，Adobe Campaign的MTA不使用安全連接將內容發送到SMTP伺服器。 您必須啟用此功能（可能會降低傳送速度）。 為此，請在`<smtp ...>`節點中將&#x200B;**enableTLS**&#x200B;設為&#x200B;**true**。

您可以減少驗證節點（sessionTimeOutSec屬性）中會話的存留期。
