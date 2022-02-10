---
product: campaign
title: ACS連接器入門
description: ACS連接器原理和資料週期
feature: ACS Connector
exl-id: 689b6117-5143-4f85-8582-2c74cae72ca2
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '1985'
ht-degree: 0%

---

# ACS連接器入門{#acs-connector-gs}

![](../../assets/v7-only.svg)

ACS連接器橋接Adobe Campaignv7和Adobe Campaign Standard。 它是Campaign v7中的一個整合功能，可自動將資料複製到Campaign Standard中，將兩個應用程式中的最佳組合在一起。 市場活動v7具有高級工具，可管理主要市場營銷資料庫。 Campaign v7中的資料複製使Campaign Standard能夠在用戶友好的環境中利用豐富的資料。

![](assets/acs_connect_puzzle_link_01.png)

使用ACS Connector，數字營銷人員將繼續使用Campaign Standard來設計、定向和執行市場活動，而市場活動v7是專門為面向資料的用戶定製的。

>[!IMPORTANT]
>
>ACS連接器僅作為Adobe CampaignPrime產品的一部分提供。 有關如何許可Adobe CampaignPrime的詳細資訊，請與客戶經理聯繫。
>
>ACS連接器僅可用於托管和混合體系結構。 它不可用於完整的內部安裝。
>
>要使用此功能，您必須與Adobe ID(IMS)連接到Campaign。 請參閱 [通過Adobe ID連接](../../integrations/using/about-adobe-id.md)。

本文檔介紹ACS連接器功能。 以下各節提供了有關此功能如何複製資料的資訊，以及有關如何使用已複製配置檔案的說明。

* [進程](#process):ACS連接器概述以及如何管理資料複製。
* [實施](#implementation):如何開始使用ACS Connector的概述，以及如何複製基本和高級資料的說明。
* [同步配置檔案](../../integrations/using/synchronizing-profiles.md):有關如何複製配置檔案以及如何使用配置檔案建立交貨的說明。
* [同步受眾](../../integrations/using/synchronizing-audiences.md):有關如何在市場活動v7中確定收件者清單目標，然後將清單複製為作為受眾Campaign Standard的說明。
* [同步Web應用程式](../../integrations/using/synchronizing-web-applications.md):有關如何將市場活動v7 Web應用程式連結到Campaign Standard的說明。
* [診斷ACS連接器](../../integrations/using/troubleshooting-the-acs-connector.md):查看常見問題的答案。

>[!NOTE]
>
>ACS Connector隨市場活動v7一起提供，並符合許可協定。 要使用ACS連接器，請確保可以在Campaign v7和Campaign Standard之間切換。 如果您不確定您的版本及其附帶的功能，請與管理員聯繫。

## 程序 {#process}

### 資料複製 {#data-replication}

![](assets/acs_connect_flows_01.png)

ACS連接器將定期從市場活動v7複製以下項目到Campaign Standard:

* **收件人**
* **訂閱**
* **服務**
* **登陸頁面**

預設情況下，ACS連接器的定期複製每15分鐘一次。 可以根據您的需要調整定期複製的範圍。 如果需要更改，請與顧問聯繫。

收件人、訂閱、服務和登錄頁的資料複製是增量的，這意味著只有新收件人和對現有收件人的修改才從「市場活動第7版」複製到「Campaign Standard」。 但是，在單個實例中複製受眾。 您可以在Campaign v7中建立受眾，然後將其複製一次到Campaign Standard。 複製是立即的，無法為常規更新配置。 有關說明，請參見 [同步受眾](../../integrations/using/synchronizing-audiences.md)。

>[!NOTE]
>
>請耐心等待大型資料庫的初始複製，因為它可能需要幾個小時。 但是，後續複製是增量複製，而且速度要快得多。

ACS連接器將定期從Campaign Standard複製到市場活動v7 :

* **[!UICONTROL Delivery IDs]**
* **[!UICONTROL Email broad logs]**
* **[!UICONTROL Email tracking logs]**

複製交付ID和電子郵件日誌允許從「活動7」訪問v7收件人的交付和跟蹤資料的歷史記錄。

>[!IMPORTANT]
>
>只有電子郵件廣播和跟蹤日誌才會從Campaign Standard複製到市場活動v7。

### 資料同步 {#data-synchronization}

![](assets/acs_connect_flows_02.png)

ACS連接器在Campaign v7和Campaign Standard之間同步隔離。

例如，從「市場活動」v7複製到「Campaign Standard」的配置檔案包括電子郵件地址。 如果電子郵件地址被Campaign Standard隔離，則在下次同步期間資料將傳遞給市場活動v7。 有關隔離的詳細資訊，請參見 [隔離管理](../../delivery/using/understanding-quarantine-management.md) 和 [Campaign Standard隔離](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)。

### 使用複製的配置檔案 {#using-replicated-profiles}

Campaign Standard和市場活動v7可以使用複製的配置檔案，以在市場活動中確定工作流的目標。

有關如何使用複製的配置檔案以Campaign Standard方式發送交貨的說明，請參見 [同步配置檔案](../../integrations/using/synchronizing-profiles.md)。 另外還提供了在市場活動v7和Campaign Standard之間共用未訂閱資料的說明。

### 限制 {#limitations}

複製的配置檔案可供交付使用，但在Campaign Standard方面有某些限制。 查看以下項目，瞭解如何最好地管理這些項目。

* **只讀配置檔案，用於Campaign Standard**:複製的配置檔案在Campaign Standard中為只讀。 但是，您可以在「市場活動7」中編輯收件人，修改將通過ACS連接器自動Campaign Standard更新。
* **在Campaign Standard中建立的配置檔案**:ACS連接器將收件人資料從市場活動v7複製到Campaign Standard。 因此，源於Campaign Standard的配置檔案不會複製到市場活動v7。
* **基本收件人資料，用於Campaign Standard**:ACS連接器複製適合Campaign Standard的收件人資料。 它包括收件人的姓名、地址、電子郵件地址、行動電話號碼、家庭電話號碼和其他相關聯繫資訊。 如果市場活動v7中提供的其他收件人欄位和自定義目標表對您的工作流至關重要，請與顧問聯繫。
* **正在導入隔離的配置檔案**:不想與其聯繫的配置檔案清單可以作為隔離配置檔案導入市場活動v7或Campaign Standard。 配置檔案的狀態包含在應用程式之間的隔離同步中，不會在交貨中使用它們。
* **取消訂閱Campaign Standard中的服務**:取消訂閱交貨的選項不會從Campaign Standard同步到市場活動v7。 但是，您可以配置Campaign Standard傳遞以將其未訂閱連結定向到市場活動v7。 按一下取消訂閱連結的收件人的配置檔案將在市場活動v7中更新，資料將複製到Campaign Standard。 請參閱 [更改取消訂閱連結](../../integrations/using/synchronizing-profiles.md#changing-the-unsubscription-link)。
* 只有電子郵件廣播和跟蹤日誌才會從Campaign Standard複製到市場活動v7。

### 計費 {#billing}

您選擇發送交貨、市場活動v7或Campaign Standard時，計費不受您的選擇影響。 開單資訊在市場活動v7和Campaign Standard之間協調。 因此，如果您使用兩個應用程式將交貨發送給同一收件人，則它仍被視為一個活動配置檔案。

## 實施 {#implementation}

ACS連接器有兩種實現類型。 這兩個角色始終由Adobe Campaign咨詢團隊執行。

>[!IMPORTANT]
>
>本節僅供專家用戶使用，為他們提供實施過程及其主要步驟的全局視圖。
>
>不要嘗試自己執行任何這些實施。 這項工作嚴格由Adobe Campaign顧問負責。

的 **基本實現** 允許您複製收件人（現成欄位）、服務和訂閱、Web應用程式和訪問群體。 這是從Campaign v7到Campaign Standard的單向複製。

的 **高級實施** 將允許您執行更複雜的使用案例，例如，如果您有其他收件人欄位或自定義收件人表（例如，事務表）。 請參閱 [高級實施](#advanced-implementation)。

### 安裝軟體包 {#installing-the-package}

要使用特徵， **[!UICONTROL ACS Connector]** 需要安裝軟體包。 這始終由Adobe技術管理員或顧問執行。

與ACS連接器相關的所有技術元素均可在 **[!UICONTROL Administration > ACS Connector]** 的子菜單。

### 技術和複製工作流 {#technical-and-replication-workflows}

安裝軟體包後，可在以下位置獲得兩個技術工作流 **[!UICONTROL Administration > ACS Connector > Process]**。

>[!IMPORTANT]
>
>切勿嘗試修改這些工作流。 它們不應出錯或暫停。 如果發生這種情況，請聯繫您的Adobe Campaign顧問。

![](assets/acs_connect_implementation_3.png)

* **[!UICONTROL `[ACS] Quarantine synchronization`]** (quarantineSync):此工作流將同步所有隔離資訊。 市場活動v7中的所有新隔離都複製到Campaign Standard。 所有新的隔離與Campaign Standard都複製到Campaign v7中。 這保證所有排除規則都在市場活動v7和Campaign Standard之間同步。
* **[!UICONTROL `[ACS] Security group synchronization`]** (securityGroupSync):此工作流用於權限轉換。 請參閱 [權利轉換](#rights-conversion)。

以下複製工作流可用作「準備使用」模板。 這需要由你的Adobe Campaign顧問來實施。

![](assets/acs_connect_implementation_2.png)

* **[!UICONTROL `[ACS] Profile replication`]** (newProfileReplication):此增量工作流將收件人複製到Campaign Standard。 預設情況下，它複製所有出廠設定的收件人欄位。 請參閱 [預設收件人欄位](#default-recipient-fields)。
* **[!UICONTROL `[ACS] Service replication`]** （新服務複製）:此增量工作流將所選服務複製到Campaign Standard。 請參閱用例 [同步Web應用程式](../../integrations/using/synchronizing-web-applications.md)。
* **[!UICONTROL `[ACS] Landing pages replication`]** (newLandingPageReplication):此增量工作流將選定的Web應用程式複製到Campaign Standard。 市場活動v7 Web應用程式將作為登錄頁在Campaign Standard中顯示。 請參閱用例 [同步Web應用程式](../../integrations/using/synchronizing-web-applications.md)。
* **[!UICONTROL `[ACS] New replication`]** （新複製）:此增量工作流是可用於複製自定義表的示例。 請參閱 [高級實施](#advanced-implementation)。
* **[!UICONTROL `[ACS] Delivery-message replication`]** (newDlvMsgAcelification):此增量工作流將傳遞消息從Campaign Standard複製到市場活動v7。
* **[!UICONTROL `[ACS] Profile delivery log replication`]** (newRcpDeliveryLogReplication):此增量工作流將交付ID、電子郵件廣泛日誌和電子郵件跟蹤日誌從Campaign Standard複製到市場活動v7。 它只考慮從Campaign Standard發送到屬於市場活動v7的nms:recipients表的配置檔案的交貨。
* **[!UICONTROL `[ACS] New delivery log replication`]** (newRcpDeliveryLogReplication):此增量工作流將交付ID、電子郵件廣泛日誌和電子郵件跟蹤日誌從Campaign Standard複製到市場活動v7。 它只考慮從Campaign Standard發送到作為市場活動v7特定表（定義nms:recipients以外的）一部分的配置檔案的交貨。

### 預設收件人欄位 {#default-recipient-fields}

如果您有任何附加欄位或自定義表（例如，事務表），則預設情況下不會複製這些欄位或自定義表。 需要執行高級配置。 請參閱 [高級實施](#advanced-implementation)。

您將在與基本實現一起複製的收件人欄位清單下找到。 這些是現成欄位：

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 源ID<br /> </td> 
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
   <td> @gender<br /> </td> 
  </tr> 
  <tr> 
   <td> 稱呼<br /> </td> 
   <td> @salutation<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再聯繫（通過任何渠道）<br /> </td> 
   <td> @blackList<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再通過電子郵件聯繫<br /> </td> 
   <td> @blackListEmail<br /> </td> 
  </tr> 
  <tr> 
   <td> 不再通過SMS聯繫。<br /> </td> 
   <td> @blackListMobile<br /> </td> 
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
   <td> [位置/@address1]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址2<br /> </td> 
   <td> [位置/@address2]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址3（數字和街道）<br /> </td> 
   <td> [位置/@address3]<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址4（縣）<br /> </td> 
   <td> [位置/@address4]<br /> </td> 
  </tr> 
  <tr> 
   <td> 郵遞區號<br /> </td> 
   <td> [位置/@zipCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> 城市<br /> </td> 
   <td> [位置/@city]<br /> </td> 
  </tr> 
  <tr> 
   <td> 省/自治區代碼<br /> </td> 
   <td> [位置/@stateCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> 國家/地區代碼<br /> </td> 
   <td> [位置/@countryCode]<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 權利轉換 {#rights-conversion}

在Campaign v7和Campaign Standard中，權限的處理方式不同。 在Campign v7中，權限管理基於資料夾，而在Campaign Standard中，權限管理基於單位訪問（組織/地理單位）。 Campaign Standard用戶屬於包含限制上下文的安全組。 因此，需要轉換Campign v7權限系統以匹配Campaign Standard。 執行權限轉換有幾種方法。 您將在下面找到一個實施示例。

1. 下 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**，使用 **[!UICONTROL Synchronize]** 按鈕以檢索所有Campaign Standard安全組。 排除了出廠設定Campaign Standard組。

   ![](assets/acs_connect_implementation_4.png)

1. 如果權限管理是基於資料夾的，請轉到 **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** 並將每個所需資料夾與安全組映射。

   ![](assets/acs_connect_implementation_5.png)

1. 然後，複製工作流將使用此資訊，並將相應的組織/地理單位添加到要複製的每個對象中。

### 高級實施 {#advanced-implementation}

本節介紹高級實施方面的一些可能性。

>[!IMPORTANT]
>
>此資訊只能用作一般准則。 請聯繫您的Adobe Campaign顧問，瞭解實施情況。

高級實施將根據客戶的需要添加自定義複製工作流。 以下是幾個示例：

* 交付複製
* 市場活動複製
* 程式複製
* 種子成員複製
* 事務性複製
* 等。

**在收件人上複製擴展欄位**

通過基本實現，可複製現成收件欄位。 如果要複製添加到收件人架構的自定義欄位，則需要標識它們。

1. 下 **[!UICONTROL Administration > ACS Connector > Data mapping]**，在 **[!UICONTROL nms:recipient]** 的子菜單。

   ![](assets/acs_connect_implementation_6.png)

1. 選擇要複製的附加欄位和其他所需資訊（索引、連結、標識鍵）。

   ![](assets/acs_connect_implementation_7.png)

1. 開啟專用配置檔案複製工作流（不是模板，而是工作流實例本身）。 修改 **[!UICONTROL Query]** 和 **[!UICONTROL Update data]** 活動以包括這些欄位。 請參閱 [技術和複製工作流](#technical-and-replication-workflows)。

   ![](assets/acs_connect_implementation_8.png)

   ![](assets/acs_connect_implementation_9.png)

**複製自定義配置檔案表**

通過基本實現，可複製現成收件表。 如果添加了自定義收件人表，下面是如何標識這些表。

1. 下 **[!UICONTROL Administration > ACS Connector > Data mapping]**，在自定義配置檔案表上建立目標映射。

   ![](assets/acs_connect_implementation_10.png)

1. 定義要複製的標識資料、索引、連結和欄位。

   ![](assets/acs_connect_implementation_10.png)

1. 如果權限管理基於資料夾，請轉到 **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]**，並為連結到自定義表的資料夾定義安全組。 請參閱 [權利轉換](#rights-conversion)。
1. 使用 **[!UICONTROL New replication]** 工作流（不是模板，而是工作流實例本身），以包括要複製的自定義表和欄位。 請參閱 [技術和複製工作流](#technical-and-replication-workflows)。
