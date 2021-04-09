---
solution: Campaign Classic
product: campaign
title: 伺服器安全性設定
description: 進一步瞭解伺服器組態最佳實務
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 3%

---

# 伺服器安全性設定 {#server-configuration}

## 檔案上傳保護

使用Campaign Client Console或Web介面，向營運使用者檢查他們上傳到伺服器的檔案類型。 提醒您，業務需求可以是：

* 影像(jpg、gif、png、...)
* 內容(zip、html、css、...)
* 行銷資產(doc、xls、pdf、psd、tiff...)
* 電子郵件附件(doc, pdf, ...)
* ETL(txt、csv、tab、...)
* 等等。

將所有這些內容都添加到serverConf/shared/datastore/@uploadAllowlist（有效的java規則運算式）中。 進一步瞭解[本頁](../../installation/using/file-res-management.md)。

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
