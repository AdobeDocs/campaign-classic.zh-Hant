---
product: campaign
title: 伺服器安全配置
description: 進一步了解伺服器設定最佳實務
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: 4661a65c83f3b9b7da9ea902f387155c5933e59f
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 4%

---

# 伺服器安全性設定 {#server-configuration}

![](../../assets/v7-only.svg)

## 檔案上傳保護

使用Campaign用戶端主控台或網頁介面，向營運使用者檢查他們上傳到伺服器的檔案類型。 提醒您，業務需求可以是：

* 影像(jpg、gif、png、...)
* 內容(zip、html、css、...)
* 行銷資產(doc、xls、pdf、psd、tiff、...)
* 電子郵件附件(doc、pdf、..)
* ETL(txt、csv、Tab、...)
* 等。

將所有這些變數新增至serverConf/shared/datastore/@uploadAllowlist（有效的java規則運算式）。 在[本頁](../../installation/using/file-res-management.md)中瞭解更多。

Adobe Campaign不會限制檔案大小。 但您可以透過設定IIS/Apache來執行此作業。 進一步了解[本節](../../installation/using/web-server-configuration.md)。

## 中繼

如需詳細資訊，請參閱[此頁面](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays)。

預設情況下，所有動態頁都會自動中繼到啟動Web模組的電腦的本地Tomcat伺服器。 你可以選擇不轉送其中一部分。 如果您沒有使用某些Adobe Campaign模組（例如webapp、interaction、jsp），則可以從中繼規則中刪除這些模組。

現成可用，我們已強制使用http(httpAllowed=&quot;true&quot;)顯示一般使用者資源。 由於這些頁面可顯示某些PII（例如電子郵件內容、地址）、兌換抵用券、優惠方案，因此您應在這些路徑上再次強制HTTPS。

如果您使用不同的主機名稱（一個公用主機名稱，另一個用於運算子），您也可以阻止操作員通過公用DNS名稱轉發某些資源。

## 傳出連線的保護

可由您的 Campaign Classic 執行個體的 JavaScript 程式碼 (工作流程等等) 呼叫之預設 URL 清單有限。 若要允許新URL，管理員需要在[serverConf.xml檔案](../../installation/using/the-server-configuration-file.md)中參照該URL。

存在三種連接保護模式：

* **阻止** :所有不屬於允許清單的URL都會遭到封鎖，並顯示錯誤訊息。這是升級後的預設模式。
* **許可** :允許屬於允許清單的所有URL。
* **警告** :允許所有未列在允許清單上的URL，但JS解釋器會發出警告，以便管理員可以收集這些URL。此模式添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

新客戶端將使用阻塞模式。 如果他們想要允許新的URL，則需要聯絡管理員以將其新增至允許清單。

來自移轉的現有客戶可能會使用警告模式一段時間。 同時，在授權URL之前，他們需要分析傳出流量。

## 命令限制（伺服器端）

多個命令列入黑名單，無法使用execCommand函式執行。 專用的Unix用戶為執行外部命令提供了額外的安全性。 對於托管安裝，會自動套用此限制。 對於內部部署安裝，您可以依照[此頁面](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)的指示，手動設定此限制。 此外，**[!UICONTROL Script]**&#x200B;和&#x200B;**[!UICONTROL External task]**&#x200B;工作流活動不可用（新安裝的實例）。

## 其他配置

您可以為所有頁面新增額外的HTTP標題（如需詳細資訊，請參閱[此頁面](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)）:

* 您可以新增一些其他標題，例如HSTS、X-FRAME-OPTIONS、CSP..
* 您必須先在測試環境中測試，才能在生產環境中套用。

   >[!IMPORTANT]
   >
   >Adobe Campaign可透過新增特定標題來劃分。

Adobe Campaign可讓您在`<dbcnx .../>`元素中設定純密碼。 請勿使用此功能。

依預設，Adobe Campaign不會將工作階段固定至特定IP，但您可以啟用該IP，以防止工作階段被盜用。 要執行此操作，請在[serverConf.xml檔案](../../installation/using/the-server-configuration-file.md)中，將`<authentication>`節點中的checkIPConsistent屬性設定為&#x200B;**true**。

依預設，Adobe Campaign的MTA不會使用安全連線將內容傳送至SMTP伺服器。 您必須啟用此功能（可能會降低傳送速度）。 要執行此操作，請在`<smtp ...>`節點中將&#x200B;**enableTLS**&#x200B;設定為&#x200B;**true**。

您可以在驗證節點（sessionTimeOutSec屬性）中縮短工作階段的存留期。
