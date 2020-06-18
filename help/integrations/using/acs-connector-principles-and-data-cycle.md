---
title: ACS連接器原理和資料週期
seo-title: ACS連接器原理和資料週期
description: ACS連接器原理和資料週期
seo-description: null
page-status-flag: never-activated
uuid: ea62ee69-042e-4c18-aaea-d65872d07dd9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 64d87bea-2376-4684-ac93-6ca56fe0f262
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 54cb4143fc534aa436c4b8b28e031e87a2a02e40
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 0%

---


# ACS連接器原理和資料週期{#acs-connector-principles-and-data-cycle}

## 簡介 {#introduction}

ACS Connector將Adobe Campaign v7和Adobe Campaign Standard連接在一起。 它是Campaign v7中的整合功能，可自動將資料複製至Campaign Standard，將兩種應用程式的優點結合在一起。 Campaign v7提供進階工具來管理主要行銷資料庫。 從Campaign v7複製資料可讓Campaign Standard在使用者友好的環境中運用豐富的資料。

![](assets/acs_connect_puzzle_link_01.png)

有了ACS連接器，數位行銷人員會繼續使用Campaign Standard來設計、定位和執行促銷活動，而Campaign v7則是專為資料導向的使用者（例如資料庫行銷人員）量身打造。

>[!CAUTION]
>
>ACS Connector僅能做為Adobe Campaign Prime產品的一部分。 如需如何授權Adobe Campaign Prime的詳細資訊，請連絡您的客戶經理。
>
>ACS連接器僅適用於托管和混合體系結構。 它不適用於完整的內部部署安裝。
>
>若要使用此功能，您必須使用Adobe ID(IMS)連線至Campaign。 請參 [閱透過Adobe ID連線](../../integrations/using/about-adobe-id.md)。

本文檔介紹ACS連接器功能。 以下各節提供如何複製資料的資訊以及如何使用複製配置檔案的說明。

* [流程](#process): ACS連接器概述以及如何管理資料複製。
* [實施](#implementation): 概述如何開始使用ACS連接器，以及如何複製基本和高級資料的說明。
* [同步設定檔](../../integrations/using/synchronizing-profiles.md): 說明如何複製描述檔以及如何使用描述檔建立傳送。
* [同步對象](../../integrations/using/synchronizing-audiences.md): 說明如何在Campaign v7中定位收件者清單，然後將清單複製至Campaign Standard做為對象。
* [同步化Web應用程式](../../integrations/using/synchronizing-web-applications.md): 有關如何將Campaign v7網頁應用程式連結至Campaign Standard的指示。
* [ACS連接器故障排除](../../integrations/using/troubleshooting-the-acs-connector.md): 檢視常見問題的解答。

>[!NOTE]
>
>ACS連接器隨附於Campaign v7授權合約。 若要使用ACS連接器，請確定您可以在Campaign v7和Campaign Standard之間切換。 如果您不確定您的版本及其隨附的功能，請聯絡您的管理員。

## 程序 {#process}

### 資料複製 {#data-replication}

![](assets/acs_connect_flows_01.png)

ACS連接器會定期將下列項目從Campaign v7複製到Campaign Standard:

* **收件者**
* **訂閱**
* **服務**
* **登錄頁面**

預設情況下，ACS連接器的定期複製每15分鐘一次。 可以根據需要調整定期複製的範圍。 如果需要變更，請洽詢您的顧問。

收件者、訂閱、服務和著陸頁面的資料複製是遞增的，這表示只有新的收件者和現有收件者的修改會從Campaign v7複製到Campaign Standard。 不過，對象複製是在單一實例中進行的。 您可以在Campaign v7中建立對象，然後將其複製一次至Campaign Standard。 複製是立即的，無法為定期更新配置。 如需指示，請參閱同 [步觀眾](../../integrations/using/synchronizing-audiences.md)。

>[!NOTE]
>
>請耐心等待大型資料庫的初始複製，因為它可能需要幾個小時。 但是，後續的複製是增量的，而且速度要快得多。

ACS連接器會定期從Campaign Standard複製下列項目至Campaign v7:

* **[!UICONTROL Delivery IDs]**
* **[!UICONTROL Email broad logs]**
* **[!UICONTROL Email tracking logs]**

複製傳送ID和電子郵件記錄檔可讓您從Campaign v7存取v7收件者的傳送記錄和追蹤資料。

>[!CAUTION]
>
>只有電子郵件廣播和追蹤記錄檔會從Campaign Standard複製到Campaign v7。

### 資料同步 {#data-synchronization}

![](assets/acs_connect_flows_02.png)

ACS連接器可同步Campaign v7和Campaign Standard之間的隔離。

例如，從Campaign v7複製到Campaign Standard的描述檔包含電子郵件地址。 如果電子郵件地址被Campaign Standard隔離，則資料會在下次同步期間傳遞至Campaign v7。 有關隔離的詳細資訊，請參 [閱隔離管理](../../delivery/using/understanding-quarantine-management.md)[和Campaign Standard隔離](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)。

### 使用複製的配置檔案 {#using-replicated-profiles}

複製的設定檔可供Campaign Standard和Campaign v7用於定位行銷促銷活動的工作流程。

如需如何使用複製的設定檔在Campaign Standard中傳送傳送的指示，請參閱同步 [設定檔](../../integrations/using/synchronizing-profiles.md)。 另外還提供在Campaign v7和Campaign Standard之間共用取消訂閱資料的指示。

### 限制 {#limitations}

複製的設定檔可供傳送使用，但在Campaign Standard中有某些限制。 請檢閱下列項目，瞭解如何最佳化管理。

* **Campaign Standard的唯讀設定檔**: 複製的設定檔在Campaign Standard中為唯讀。 不過，您可以在Campaign v7中編輯收件者，而且ACS連接器會在Campaign Standard中自動更新修改。
* **在Campaign Standard中建立的設定檔**: ACS連接器將收件者資料從Campaign v7複製到Campaign Standard，以單一方向複製。 因此，源自Campaign Standard的設定檔不會複製至Campaign v7。
* **Campaign Standard的基本收件者資料**: ACS連接器可複製適合Campaign Standard的收件者資料。 其中包括收件者的姓名、地址、電子郵件地址、行動電話號碼、家庭電話號碼，以及其他相關聯絡資訊。 如果Campaign v7中提供的其他收件者欄位和自訂定位表格對您的工作流程至關重要，請與您的顧問聯絡。
* **導入隔離配置檔案**: 不想與其聯絡的個人檔案清單可匯入Campaign v7或Campaign Standard，做為隔離的個人檔案。 配置檔案的狀態包括在應用程式之間的隔離同步中，它們不會用於傳送。
* **取消訂閱Campaign Standard中的服務**: 取消訂閱傳送的選項不會從Campaign Standard同步到Campaign v7。 不過，您可以設定「促銷活動標準」傳送，將其取消訂閱連結導向至Campaign v7。 按一下取消訂閱連結的收件者的設定檔會在Campaign v7中更新，而且資料會複製到Campaign Standard。 請參 [閱變更取消訂閱連結](../../integrations/using/synchronizing-profiles.md#changing-the-unsubscription-link)。
* 只有電子郵件廣播和追蹤記錄檔會從Campaign Standard複製到Campaign v7。

### 帳單 {#billing}

您選擇傳送傳送、促銷活動v7或促銷活動標準的應用程式，並不會影響帳單。 帳單資訊可在Campaign v7和Campaign Standard之間調節。 因此，如果您使用兩個應用程式將傳送內容傳送至相同的收件者，則仍會計為一個作用中的描述檔。

## 實作 {#implementation}

ACS連接器有兩種實施類型。 兩者一律由Adobe Campaign Consulting團隊執行。

>[!CAUTION]
>
>本節僅針對專家使用者，提供他們實施程式及其主要步驟的全域檢視。
>
>請勿嘗試自行執行任何這些實作。 Adobe Campaign顧問會嚴格保留此資訊。

基 **本實作** ，可讓您複製收件者（現成可用欄位）、服務與訂閱、Web應用程式與觀眾。 這是從Campaign v7到Campaign Standard的單向複製。

進 **階實作** ，可讓您執行更複雜的使用案例，例如您有其他收件者欄位或自訂收件者表格（例如交易表格）。 請參閱 [進階實作](#advanced-implementation)。

### 安裝軟體包 {#installing-the-package}

若要使用此功能， **[!UICONTROL ACS Connector]** 需要安裝此套件。 這一律由Adobe技術管理員或顧問執行。

與ACS連接器相關的所有技術元素都可在瀏覽器 **[!UICONTROL Administration > ACS Connector]** 的節點中使用。

### 技術和複製工作流程 {#technical-and-replication-workflows}

在安裝軟體包後，可在下面提供兩個技術工作流程 **[!UICONTROL Administration > ACS Connector > Process]**。

>[!CAUTION]
>
>切勿嘗試修改這些工作流程。 它們不應出錯或暫停。 如果發生此情況，請連絡您的Adobe Campaign顧問。

![](assets/acs_connect_implementation_3.png)

* **[!UICONTROL `[ACS] Quarantine synchronization`]** (quarantineSync): 此工作流將同步所有隔離資訊。 Campaign v7中的所有新隔離都會複製到Campaign Standard中。 所有新的隔離都會複製到Campaign v7。 這可保證所有排除規則都會在Campaign v7和Campaign Standard之間同步。
* **[!UICONTROL `[ACS] Security group synchronization`]** (securityGroupSync): 此工作流程用於權限轉換。 請參閱 [權限轉換](#rights-conversion)。

以下複製工作流程可作為「準備使用」模板使用。 這些項目需由您的Adobe Campaign顧問實作。

![](assets/acs_connect_implementation_2.png)

* **[!UICONTROL `[ACS] Profile replication`]** (newProfileReplication): 此增量工作流程會將收件者複製至Campaign Standard。 預設情況下，它會複製所有現成可用的收件者欄位。 請參閱 [預設收件者欄位](#default-recipient-fields)。
* **[!UICONTROL `[ACS] Service replication`]** (newServiceReplication): 此增量工作流程會將所選服務複製至Campaign Standard。 請參閱同步化Web應 [用程式的使用案例](../../integrations/using/synchronizing-web-applications.md)。
* **[!UICONTROL `[ACS] Landing pages replication`]** (newLandingPageReplication): 此增量工作流程會將所選的Web應用程式複製至Campaign Standard。 Campaign v7網頁應用程式將顯示為Campaign Standard中的著陸頁面。 請參閱同步化Web應 [用程式的使用案例](../../integrations/using/synchronizing-web-applications.md)。
* **[!UICONTROL `[ACS] New replication`]** （新複製）: 此增量工作流是一個可用於複製自定義表的示例。 請參閱 [進階實作](#advanced-implementation)。
* **[!UICONTROL `[ACS] Delivery-mesage replication`]** (newDlvMsgQualification): 此增量工作流程會將傳送訊息從Campaign Standard複製到Campaign v7。
* **[!UICONTROL `[ACS] Profile delivery log replication`]** (newRcpDeliveryLogReplication): 此增量工作流程會將傳送ID、電子郵件廣泛記錄檔和電子郵件追蹤記錄檔從Campaign Standard複製到Campaign v7。 它只會考慮從Campaign Standard傳送至屬於Campaign v7 nms:recipients表一部分的描述檔的傳送。
* **[!UICONTROL `[ACS] New delivery log replication`]** (newRcpDeliveryLogReplication): 此增量工作流程會將傳送ID、電子郵件廣泛記錄檔和電子郵件追蹤記錄檔從Campaign Standard複製到Campaign v7。 它只會考慮從Campaign Standard傳送至Campaign v7特定表格（定義nms：接收者除外）的描述檔的傳送。

### 預設收件者欄位 {#default-recipient-fields}

如果您有任何其他欄位或自訂表格（例如，交易表格），則預設不會複製這些欄位或自訂表格。 需要執行進階設定。 請參閱 [進階實作](#advanced-implementation)。

您將在與基本實施一起複製的收件者欄位清單下找到。 這些是現成可用的欄位：

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 來源ID<br /> </td> 
   <td> @sourceId<br /> </td> 
  </tr> 
  <tr> 
   <td> 建立日期<br /> </td> 
   <td> @created<br /> </td> 
  </tr> 
  <tr> 
   <td> 修改日期<br /> </td> 
   <td> @lastModified<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
  </tr> 
  <tr> 
   <td> 姓氏<br /> </td> 
   <td> @lastName<br /> </td> 
  </tr> 
  <tr> 
   <td> 名字<br /> </td> 
   <td> @firstName<br /> </td> 
  </tr> 
  <tr> 
   <td> 中間名<br /> </td> 
   <td> @middleName<br /> </td> 
  </tr> 
  <tr> 
   <td> 行動裝置<br /> </td> 
   <td> @mobilePhone<br /> </td> 
  </tr> 
  <tr> 
   <td> 出生日期<br /> </td> 
   <td> @birthDate<br /> </td> 
  </tr> 
  <tr> 
   <td> 性別<br /> </td> 
   <td> @gedem<br /> </td> 
  </tr> 
  <tr> 
   <td> 問候語<br /> </td> 
   <td> @salutation<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再聯絡（透過任何管道）<br /> </td> 
   <td> @blockList<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再透過電子郵件聯絡<br /> </td> 
   <td> @blockListEmail<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再透過SMS聯絡<br /> </td> 
   <td> @blockListMobile<br /> </td> 
  </tr> 
  <tr> 
   <td> 電話<br /> </td> 
   <td> @phone<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳真<br /> </td> 
   <td> @fax<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址1（公寓）<br /> </td> 
   <td> [location/@address1]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址2<br /> </td> 
   <td> [location/@address2]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址3（編號和街道）<br /> </td> 
   <td> [location/@address3]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址4（縣）<br /> </td> 
   <td> [location/@address4]<br /> </td> 
  </tr> 
  <tr> 
   <td> 郵遞區號<br /> </td> 
   <td> [location/@zipCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> 城市<br /> </td> 
   <td> [location/@city]<br /> </td> 
  </tr> 
  <tr> 
   <td> 州／省代碼<br /> </td> 
   <td> [location/@stateCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> 國家／地區代碼<br /> </td> 
   <td> [location/@countryCode]<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 權利轉換 {#rights-conversion}

在Campaign v7和Campaign Standard中，權限的處理方式不同。 在Campaign v7中，權限管理是以資料夾為基礎，而在Campaign Standard中，則是以單位存取（組織／地理單位）為基礎。 「促銷活動標準」使用者屬於包含限制內容的安全性群組。 因此，必須轉換促銷活動v7權限系統，以符合促銷活動標準版。 執行權限轉換有幾種方式。 您會在下方找到實作範例。

1. 在下 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**&#x200B;方，使用按 **[!UICONTROL Synchronize]** 鈕來擷取所有Campaign Standard安全性群組。 排除現成可用的促銷活動標準群組。

   ![](assets/acs_connect_implementation_4.png)

1. 如果您的權限管理是基於資料夾，請轉至並 **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** 將每個需要的資料夾與安全組映射。

   ![](assets/acs_connect_implementation_5.png)

1. 然後，複製工作流將使用此資訊，並將相應的組織／地理單位添加到每個要複製的對象中。

### 進階實作 {#advanced-implementation}

本節說明進階實作的一些可能性。

>[!CAUTION]
>
>此資訊僅能用作一般准則。 請洽詢您的Adobe Campaign顧問以取得實作。

高級實施將根據客戶的需要添加自定義複製工作流。 以下是幾個範例：

* 交付複製
* 促銷活動複製
* 程式複製
* 種子成員複製
* 事務複製
* 等等。

**在收件者上複製延伸欄位**

在基本實作中，會複製現成可用的收件者欄位。 如果要複製添加到收件方案的自定義欄位，則需要標識這些欄位。

1. 在下 **[!UICONTROL Administration > ACS Connector > Data mapping]**&#x200B;方，在表格上建立定位 **[!UICONTROL nms:recipient]** 對應。

   ![](assets/acs_connect_implementation_6.png)

1. 選擇要複製的其他欄位和其他需要的資訊（索引、連結、標識鍵）。

   ![](assets/acs_connect_implementation_7.png)

1. 開啟專用的配置檔案複製工作流（不是模板，而是工作流實例本身）。 修改和 **[!UICONTROL Query]** 活動 **[!UICONTROL Update data]** 以包含這些欄位。 請參 [閱技術和複製工作流](#technical-and-replication-workflows)。

   ![](assets/acs_connect_implementation_8.png)

   ![](assets/acs_connect_implementation_9.png)

**複製自定義配置檔案表**

在基本實作中，會複製現成可用的收件者表格。 如果您新增自訂收件者表格，請以下是您如何識別這些表格。

1. 在下 **[!UICONTROL Administration > ACS Connector > Data mapping]**&#x200B;方，在自訂描述檔表格上建立定位對應。

   ![](assets/acs_connect_implementation_10.png)

1. 定義要複製的標識資料、索引、連結和欄位。

   ![](assets/acs_connect_implementation_10.png)

1. 如果您的權限管理是基於資料夾的，請轉 **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]**&#x200B;至，並為連結到自定義表的資料夾定義安全組。 請參閱 [權限轉換](#rights-conversion)。
1. 使用工 **[!UICONTROL New replication]** 作流程（不是範本，而是工作流程例項本身）來包含自訂表格和要複製的欄位。 請參 [閱技術和複製工作流](#technical-and-replication-workflows)。

