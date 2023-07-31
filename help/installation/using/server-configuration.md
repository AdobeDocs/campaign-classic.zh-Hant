---
product: campaign
title: 伺服器安全性設定
description: 深入瞭解伺服器設定最佳實務
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 4%

---

# 伺服器安全性設定 {#server-configuration}

## 檔案上傳保護

向作業使用者確認他們使用Campaign使用者端主控台或網頁介面上傳到伺服器的檔案型別。 提醒您，業務需求可以是：

* 影像(jpg、gif、png、...)
* 內容(zip、html、css、...)
* 行銷資產(doc、xls、pdf、psd、tiff、...)
* 電子郵件附件(doc， pdf， ...)
* ETL (txt、csv、tab、...)
* 等等。

在serverConf/shared/datastore/@uploadAllowlist （有效的Java規則運算式）中新增所有這些變數。 在[本頁](../../installation/using/file-res-management.md)中瞭解更多。

Adobe Campaign不會限制檔案大小。 但您可以透過設定IIS/Apache來執行此操作。 若要了解詳細資訊，請參閱[本章節](../../installation/using/web-server-configuration.md)。

## 轉送

請參閱 [此頁面](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 以取得詳細資訊。

依預設，所有動態頁面都會自動轉送到其Web模組啟動之電腦的本機Tomcat伺服器。 您可以選擇不轉送其中部分。 如果您沒有使用某些Adobe Campaign模組（例如webapp、互動、某些jsp），您可以從轉送規則中將其移除。

我們已強制使用http (httpAllowed=&quot;true&quot;)立即顯示一般使用者資源。 由於這些頁面可顯示部分PII （例如電子郵件內容、地址）、兌換優惠券、選件，因此您應該在這些路徑上再次強制使用HTTPS。

如果您使用不同的主機名稱（一個公用名稱，另一個用於操作員），您也可以防止操作員透過公用DNS名稱轉送某些所需的資源。

## 傳出連線的保護

可由您的 Campaign Classic 執行個體的 JavaScript 程式碼 (工作流程等等) 呼叫之預設 URL 清單有限。 若要允許新URL，管理員需要在 [serverConf.xml檔案](../../installation/using/the-server-configuration-file.md).

有三種連線保護模式：

* **封鎖** ：所有不屬於允許清單的URL都會遭到封鎖，並顯示錯誤訊息。 這是升級後使用的預設模式。
* **許可** ：允許所有不屬於允許清單的URL。
* **警告** ：允許不在允許清單上的所有URL，但JS解譯器會發出警告，讓管理員可以收集。 此模式會新增JST-310027警告訊息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

新使用者端將使用封鎖模式。 如果他們想要允許新的URL，則需要聯絡其管理員以將其新增到允許清單。

來自移轉的現有客戶可使用警告模式一段時間。 同時，他們需要在授權URL之前分析傳出流量。

## 命令限制（伺服器端）

封鎖清單中包含數個命令，無法使用execCommand函式執行。 專用的Unix使用者提供額外的保全性以執行外部命令。 對於託管安裝，此限制會自動套用。 對於內部部署安裝，您可以遵循中的指示，手動設定此限制 [此頁面](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). 此外， **[!UICONTROL Script]** 和 **[!UICONTROL External task]** 無法使用工作流程活動（新安裝的執行個體）。

## 其他設定

您可以為所有頁面新增額外的HTTP標題(如需詳細資訊，請參閱 [此頁面](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands))：

* 您可以新增一些額外的標頭，例如HSTS、X-FRAME-OPTIONS、CSP...
* 您必須在測試環境中測試這些變數，才能將其套用於生產環境。

  >[!IMPORTANT]
  >
  >您可以新增特定標題來中斷Adobe Campaign。

Adobe Campaign可讓您在 `<dbcnx .../>` 元素。 請勿使用此功能。

依預設，Adobe Campaign不會將工作階段固定到特定IP，但您可以將其啟動以防止工作階段遭竊。 若要這麼做，請在 [serverConf.xml檔案](../../installation/using/the-server-configuration-file.md)，將checkIPConsistent屬性設為 **true** 在 `<authentication>` 節點。

依預設，Adobe Campaign的MTA不使用安全連線將內容傳送至SMTP伺服器。 您必須啟用此功能（可能會降低傳送速度）。 若要這麼做，請設定 **enableTLS** 至 **true** 在 `<smtp ...>` 節點。

您可以縮短驗證節點（sessionTimeOutSec屬性）中工作階段的存留期。
