---
product: campaign
title: 伺服器安全配置
description: 進一步了解伺服器設定最佳實務
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 4%

---

# 伺服器安全性設定 {#server-configuration}



## 檔案上傳保護

使用Campaign用戶端主控台或網頁介面，向營運使用者檢查他們上傳到伺服器的檔案類型。 提醒您，業務需求可以是：

* 影像(jpg、gif、png、...)
* 內容(zip、html、css、...)
* 行銷資產(doc、xls、pdf、psd、tiff、...)
* 電子郵件附件(doc、pdf、..)
* ETL(txt、csv、Tab、...)
* 等。

將所有這些變數新增至serverConf/shared/datastore/@uploadAllowlist（有效的java規則運算式）。 在[本頁](../../installation/using/file-res-management.md)中瞭解更多。

Adobe Campaign不會限制檔案大小。 但您可以透過設定IIS/Apache來執行此作業。 在[本章節](../../installation/using/web-server-configuration.md)了解更多資訊。

## 中繼

請參閱 [本頁](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 以取得更多資訊。

預設情況下，所有動態頁都會自動中繼到啟動Web模組的電腦的本地Tomcat伺服器。 你可以選擇不轉送其中一部分。 如果您沒有使用某些Adobe Campaign模組（例如webapp、interaction、jsp），則可以從中繼規則中刪除這些模組。

現成可用，我們已強制使用http(httpAllowed=&quot;true&quot;)顯示一般使用者資源。 由於這些頁面可顯示某些PII（例如電子郵件內容、地址）、兌換抵用券、優惠方案，因此您應在這些路徑上再次強制HTTPS。

如果您使用不同的主機名稱（一個公用主機名稱，另一個用於運算子），您也可以阻止操作員通過公用DNS名稱轉發某些資源。

## 傳出連線的保護

可由您的 Campaign Classic 執行個體的 JavaScript 程式碼 (工作流程等等) 呼叫之預設 URL 清單有限。 若要允許新URL，管理員需在 [serverConf.xml檔案](../../installation/using/the-server-configuration-file.md).

存在三種連接保護模式：

* **封鎖** :所有不屬於允許清單的URL都會遭到封鎖，並顯示錯誤訊息。 這是升級後的預設模式。
* **許可** :允許屬於允許清單的所有URL。
* **警告** :允許所有未列在允許清單上的URL，但JS解釋器會發出警告，以便管理員可以收集這些URL。 此模式添加JST-310027警告消息。

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

denylist中包含多個命令，無法使用execCommand函式執行。 專用的Unix用戶為執行外部命令提供了額外的安全性。 對於托管安裝，會自動套用此限制。 對於內部部署安裝，您可以依照 [本頁](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). 此外， **[!UICONTROL Script]** 和 **[!UICONTROL External task]** 工作流活動不可用（新安裝的實例）。

## 其他配置

您可以為所有頁面新增額外的HTTP標題(如需詳細資訊，請參閱 [本頁](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* 您可以新增一些其他標題，例如HSTS、X-FRAME-OPTIONS、CSP..
* 您必須先在測試環境中測試，才能在生產環境中套用。

   >[!IMPORTANT]
   >
   >Adobe Campaign可透過新增特定標題來劃分。

Adobe Campaign可讓您在 `<dbcnx .../>` 元素。 請勿使用此功能。

依預設，Adobe Campaign不會將工作階段固定至特定IP，但您可以啟用該IP，以防止工作階段被盜用。 若要這麼做，請在 [serverConf.xml檔案](../../installation/using/the-server-configuration-file.md)，將checkIPConsistent屬性設定為 **true** 在 `<authentication>` 節點。

依預設，Adobe Campaign的MTA不會使用安全連線將內容傳送至SMTP伺服器。 您必須啟用此功能（可能會降低傳送速度）。 要執行此操作，請設定 **enableTLS** to **true** 在 `<smtp ...>` 節點。

您可以在驗證節點（sessionTimeOutSec屬性）中縮短工作階段的存留期。
