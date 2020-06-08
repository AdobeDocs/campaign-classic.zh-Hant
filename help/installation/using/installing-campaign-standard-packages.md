---
title: 安裝Campaign Classic標準套件
seo-title: 安裝Campaign Classic標準套件
description: 安裝Campaign Classic標準套件
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e059fc9e2bfade30454601f31990c3ec14b8a847
workflow-type: tm+mt
source-wordcount: '1212'
ht-degree: 0%

---


# 安裝Campaign Classic標準套件{#installing-campaign-standard-packages}

## 關於標準包 {#campaign-standard-packages}

軟體包是一組可根據需要安裝的功能。 這些選項可讓您新增更多選項至您的例項。

>[!CAUTION]
>
>您只能安裝與授權合約中提及的選項相對應的套件。
>
>安裝軟體包後，便無法卸載它。 安裝新套件可能會影響您的所有平台： 在最終部署之前，必須經過測試和驗證。

要安裝標準軟體包：

1. 從Adobe Campaign用戶端主控台 **[!UICONTROL Tools > Advanced > Package import...]** 存取套件匯入精靈。
1. Select **[!UICONTROL Install a standard package]**.
1. 在顯示的清單中，檢查要安裝的包。
   >[!NOTE]
   >
   >如果套件呈灰色，則無法安裝它。 這表示已安裝或與您的實例不相容。 例如，您無法在行銷例 **項上安裝Mid-sourcing平台** (Mid-sourcing platform)套件。 您可在下表中找到此資訊。
1. 按一下 **[!UICONTROL Next]**，然 **[!UICONTROL Start]** 後啟動軟體包安裝。

   安裝軟體包後，進度欄顯示 **100%** ，您可以在安裝日誌中看到以下消息： **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** 安裝窗口。

現在已安裝軟體包。

### 現成包清單 {#list-of-standard-packages}

下表列出所有標準套件及其說明、可安裝的例項類型（行銷、中端等） 及其他資訊。

<table> 
 <thead> 
  <tr> 
   <th> 封裝 </th> 
   <th> 說明 </th> 
   <th> 實例類型 </th> 
   <th> 更多資訊 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 傳送<br /> </td> 
   <td> 監控傳送的內容，以及傳送訊息時最終遇到的問題。<br /> </td> 
   <td> 全部</td> 
   <td> <a href="../../delivery/using/monitoring-a-delivery.md">進一步瞭解</a></td> 
  </tr> 
  <tr> 
   <td> 行銷促銷活動（促銷活動）<br /> </td> 
   <td> 定義、最佳化、執行和分析通訊和行銷宣傳。<br /> </td> 
   <td> 行銷</td> 
   <td> <a href="../../campaign/using/designing-marketing-campaigns.md">進一步瞭解</a> </td> 
  </tr> 
  <tr> 
   <td> 行銷資源(MRM)<br /> </td> 
   <td> 透過管理和追蹤工作、預算和行銷資源，以協作模式控制行銷動作。<br /> </td> 
   <td> 行銷</td> 
   <td> <a href="../../campaign/using/about-marketing-resource-management.md">進一步瞭解</a> </td> 
  </tr> 
  <tr> 
   <td> 選件引擎（互動）<br /> </td> 
   <td> 在與特定連絡人（客戶或目標）互動期間，透過將他們變成單一或數個適合的選件，即時回應。 <br /> </td> 
   <td> 全部<br /> </td> 
   <td> 選購，了 <a href="../../interaction/using/interaction-and-offer-management.md">解詳情</a></td> 
  </tr> 
  <tr> 
   <td> 具有執行例項的選件引擎控制<br /> </td> 
   <td> </td> 
   <td> 行銷<br /> </td> 
   <td> 可選</td> 
  </tr> 
  <tr> 
   <td> 執行例項的選件引擎<br /> </td> 
   <td> </td> 
   <td> Mid，執行 <br /> </td> 
   <td> 可選</td> 
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> 社交網路（Social行銷） <br /> </td> 
   <td> 將Adobe Campaign與Twitter和Facebook同步。<br /> </td> 
   <td> 全部</td> 
   <td> <a href="../../social/using/about-social-marketing.md">進一步瞭解</a> </td> 
  </tr> 
  <tr> 
   <td> 事務性消息控制（消息中心——控制）<br /> </td> 
   <td> 管理從資訊系統觸發的事件產生的觸發訊息。<br /> </td> 
   <td> 行銷<br /> </td> 
   <td> 選購，了 <a href="../../message-center/using/about-transactional-messaging.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 事務性消息執行（消息中心——執行） <br /> </td> 
   <td> 確保更高的可用性和更好的負載管理。<br /> </td> 
   <td> 執行<br /> </td> 
   <td> 選購，了 <a href="../../message-center/using/about-transactional-messaging.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 線路頻道<br /> </td> 
   <td> 使用LINE渠道與Adobe Campaign一起傳送傳送，<br /> </td> 
   <td> 全部<br /> </td> 
   <td> 可選，消息中心為必備</td> 
  </tr> 
  <tr> 
   <td> 直效郵件通道<br /> </td> 
   <td> 使用Adobe Campaign的直效郵件通道傳送傳送。<br /> </td> 
   <td> 全部<br /> </td> 
   <td> 選購，了 <a href="../../delivery/using/about-direct-mail-channel.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 行動通道(SMS) <br /> </td> 
   <td> 使用Adobe Campaign的行動／簡訊頻道傳送傳送。<br /> </td> 
   <td> 全部<br /> </td> 
   <td> 選購，了 <a href="../../delivery/using/sms-channel.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 電話頻道<br /> </td> 
   <td> 使用Adobe Campaign的電話頻道傳送遞送。<br /> </td> 
   <td> 全部<br /> </td> 
   <td> 可選</td> 
  </tr>
  <tr> 
   <td> 行動應用程式頻道<br /> </td> 
   <td> 使用Adobe Campaign平台透過應用程式將個人化通知傳送至iOS和Android終端機。 <br /> </td> 
   <td> 全部<br /> </td> 
   <td> 選購，了 <a href="../../delivery/using/about-mobile-app-channel.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 內容管理員<br /> </td> 
   <td> 建立定期電子報或網站，然後驗證並發佈訊息。<br /> </td> 
   <td> </td> 
   <td> <a href="../../delivery/using/about-content-management.md">進一步瞭解</a> </td> 
  </tr> 
  <tr> 
   <td> 線上調查（調查管理員）<br /> </td> 
   <td> 建立並管理線上表單，以新增或修改描述檔資訊、訂閱、取消訂閱或競爭參賽表單。<br /> </td> 
   <td> 行銷<br /> </td> 
   <td> 選購，了 <a href="../../web/using/about-surveys.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> 可讓您分析和測量資料、計算統計資料、簡化並最佳化報表建立和計算。 此外，您還可以建立報表並建立目標人口族群。 <br /> </td> 
   <td> 行銷<br /> </td> 
   <td> 選購，了 <a href="../../reporting/using/about-cubes.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 回應管理員<br /> </td> 
   <td> 衡量行銷宣傳的成功與獲利能力，或為所有通訊管道提供建議。<br /> </td> 
   <td> 行銷<br /> </td> 
   <td> 選購，了 <a href="../../campaign/using/about-response-manager.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 存取外部資料（同盟資料存取）<br /> </td> 
   <td> Provides the Federated Data Access (FDA) option in order to process information stored in one or more external databases so that you can access external data without changing the structure of Adobe Campaign data.<br /> </td> 
   <td> 全部<br /> </td> 
   <td> 選購，了 <a href="../../workflow/using/accessing-an-external-database--fda-.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 促銷活動最佳化<br /> </td> 
   <td> 控制、篩選和監控傳送的傳送，讓傳送的訊息最符合客戶的需求和期望，並符合公司通訊政策。 <br /> </td> 
   <td> 行銷<br /> </td> 
   <td> 選購，了 <a href="../../campaign/using/about-campaign-typologies.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 傳送能力監控（電子郵件傳送能力）<br /> </td> 
   <td> 測量促銷活動在到達收件者收件匣時是否成功，而不會反彈或標示為垃圾訊息。<br /> </td> 
   <td> 全部 </td> 
   <td> 選購，了 <a href="https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 抵用券管理<br /> </td> 
   <td> 建立一組抵用券，以新增至即將推出的行銷優惠。<br /> </td> 
   <td> 行銷<br /> </td> 
   <td> 選購，了 <a href="../../delivery/using/personalized-coupons.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 收件箱呈現(IR)<br /> </td> 
   <td> 可讓您預覽在可能收到訊息的不同上下文中傳送的訊息，並檢查主要桌上型電腦和應用程式的相容性。 你需要一個利特摩斯賬戶。<br /> </td> 
   <td> 行銷<br /> </td> 
   <td> 選購，了 <a href="../../delivery/using/inbox-rendering.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 中央／本地行銷（分佈式行銷）<br /> </td> 
   <td> 在中央實體（總部、行銷部門等）之間實施合作宣傳 及當地實體（銷售點、地區代理等）。<br /> </td> 
   <td> 行銷 </td> 
   <td> 選購，了 <a href="../../campaign/using/about-distributed-marketing.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> CRM連接器<br /> </td> 
   <td> Provides various CRM connectors for linking your Adobe Campaign platform to your third-party systems.<br /> </td> 
   <td> 行銷</td> 
   <td> <a href="../../platform/using/crm-connectors.md">進一步瞭解</a> </td> 
  </tr> 
  <tr> 
   <td> 網頁分析連接器<br /> </td> 
   <td> 可讓Adobe Campaign和Adobe Analytics透過Web Analytics連接器套件進行互動。<br /> </td> 
   <td> 行銷 </td> 
   <td> 與交易式訊息不相容，了 <a href="../../platform/using/adobe-analytics-data-connector.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> AEM整合<br /> </td> 
   <td> 可讓您直接在Adobe Experience Manager中管理電子郵件傳送內容及表單，以利運用AEM的內容編輯功能以及Adobe Campaign的傳送能力。<br /> </td> 
   <td> 行銷</td> 
   <td> <a href="../../integrations/using/about-adobe-experience-manager.md">進一步瞭解</a> </td> 
  </tr> 
  <tr> 
   <td> Adobe Marketing Cloud共用觀眾整合<br /> </td> 
   <td> 可讓您使用Adobe Experience Cloud解決方案和核心服務來交換和分享受眾／細分。<br /> </td> 
   <td> 行銷<br /> </td> 
   <td> 需要IMS，了 <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 與Adobe Marketing Cloud整合<br /> </td> 
   <td> 可讓您從不同的Adobe Marketing Cloud解決方案匯入和匯出觀眾／區段至Adobe Campaign。 </td> 
   <td> 行銷</td> 
   <td> 選購，了 <a href="../../integrations/using/configuring-ims.md#installing-the-package">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 隱私權資料保護法規<br /> </td> 
   <td> 包含其他功能，可協助您在Campaign Classic中符合隱私權規範。<br /> </td> 
   <td> 全部</td> 
   <td> <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">進一步瞭解</a> </td> 
  </tr> 
  <tr> 
   <td> 轉移至中部採購 <br /> </td> 
   <td> 詳細說明中間採購伺服器的安裝與設定，以及實例的部署，讓第三方在中間採購模式中傳送訊息。<br /> </td> 
   <td> 行銷 </td> 
   <td> 選購，了 <a href="../../installation/using/mid-sourcing-server.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> 中端採購平台<br /> </td> 
   <td> 此配置是代管(ASP)配置和內部化之間的最佳中間解決方案。 對外執行元件是在Adobe Campaign所代管的「中部採購」伺服器上執行。<br /> </td> 
   <td> 中部採購 </td> 
   <td> 選購，了 <a href="../../installation/using/mid-sourcing-server.md">解詳情</a> </td> 
  </tr> 
  <tr> 
   <td> ACS連接器<br /> </td> 
   <td> 橋接Adobe Campaign v7和Adobe Campaign Standard。 它是Campaign v7中的整合功能，可自動將資料複製至Campaign Standard，將兩種應用程式的優點結合在一起。 <br /> </td> 
   <td> 行銷 </td> 
   <td> 選購，了 <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">解詳情</a> </td> 
  </tr> 
 </tbody> 
</table>

### 消息中心包 {#message-center-package}

若要新增傳送渠道（行動頻道、行動應用程式頻道等），您必須在安裝訊息中心套件之前先執行此動作。 如果您已在電子郵件頻道上啟動訊息中心專案，則在專案中間，您決定新增頻道，您必須依照下列步驟進行：

1. 使用套件匯入精靈( ******[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**)，安裝您想要的頻道，例如行動頻道。
1. 匯入檔案( **[!UICONTROL Tools > Advanced > Import package > File]**)，然後選取：

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. 在中， **[!UICONTROL XML data content to import]**&#x200B;僅保留與附加渠道對應的「消息中心」傳送模板。 例如，如果您已新增 **Mobile頻道********[!UICONTROL Mobile transactional message]** ，請僅保留與(smsTriggerMessage)範本對應的實體元素。 如果您已新增行動應 **用程式頻道**，請只保留 **iOS交易訊息範本(iosTriggerMessage)和** Android交易訊息 **** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)

### LINE包 {#line-package}

若要能透過Adobe Campaign使用LINE渠道傳送傳送，您必須安裝LINE套件。

安裝LINE包是標準安裝，詳見「導入包 [」部分](../../platform/using/working-with-data-packages.md#importing-packages) 。

![](assets/line_config_1.png)

>[!CAUTION]
>
>如果在LINE之前安裝了消息中心包，則LINE的消息中心交付模板將不可用。
