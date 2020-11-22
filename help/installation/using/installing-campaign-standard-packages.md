---
solution: Campaign Classic
product: campaign
title: 安裝Campaign Classic內建套件
description: 瞭解如何安裝Campaign內建套件
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 5%

---


# Installing Campaign Classic built-in packages{#installing-campaign-standard-packages}

## 關於內建套件 {#campaign-standard-packages}

內建套件包含一組功能，可根據您的需求和合約進行安裝。 Campaign內建套件的完整清單可在下方取得。

>[!CAUTION]
>
>您只能安裝與授權合約中提及的選項相對應的套件。
>
>安裝新套件可能會影響您的所有平台：在最終部署之前，必須經過測試和驗證。
>
>安裝軟體包後，便無法卸載它。

要安裝內置軟體包，請執行以下操作：

1. 從Adobe Campaign用戶端主控台 **[!UICONTROL Tools > Advanced > Package import...]** 存取套件匯入精靈。
1. 選取 **[!UICONTROL Install a standard package]**。
1. 在包清單中，檢查要安裝的包。
   >[!NOTE]
   >
   >當套件呈灰色顯示時，表示已安裝或與您的例項不相容。 下表詳述了相容性。
1. 按一下 **[!UICONTROL Next]**，然 **[!UICONTROL Start]** 後啟動軟體包安裝。

   安裝軟體包後，進度欄顯示 **100%** ，您可以在安裝日誌中看到以下消息： **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** 安裝窗口。

現在已安裝軟體包。

### 現成包清單 {#list-of-standard-packages}

下表列出所有Campaign內建套件。

<table> 
 <thead> 
  <tr> 
   <th> 封裝 </th> 
   <th> 說明 </th> 
   <th> 實例類型 </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 傳送<br /> </td> 
   <td> 監控傳送的內容，以及傳送訊息時最終遇到的問題。 <a href="../../delivery/using/monitoring-a-delivery.md">進一步瞭解</a><br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 行銷促銷活動（促銷活動）<br /> </td> 
   <td> 定義、最佳化、執行和分析通訊和行銷宣傳。 <a href="../../campaign/using/designing-marketing-campaigns.md">進一步瞭解</a><br /> </td> 
   <td> 行銷</td>
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> 透過管理和追蹤工作、預算和行銷資源，以協作模式控制行銷動作。 <a href="../../campaign/using/about-marketing-resource-management.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> 選件引擎（互動）<br /> </td> 
   <td> 在與特定連絡人（客戶或目標）互動期間，透過將他們變成單一或數個適合的選件，即時回應。  選填。<a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">進一步瞭解</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用執行例項控制選件引擎。 選填。<br /> </td> 
   <td> 要安裝在選件引擎（互動）的控制例項上的套件。 <a href="../../interaction/using/distributed-architectures.md#packages-configuration">進一步瞭解</a> </td> 
   <td> 行銷<br /> </td>  
  </tr> 
  <tr> 
   <td> 執行例項的選件引擎。 選填。<br /> </td> 
   <td> 套件以安裝在選件引擎（互動）的執行例項上。 <a href="../../interaction/using/distributed-architectures.md">進一步瞭解</a> </td> 
   <td> Mid，執行 <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> 社交網路（Social行銷） <br /> </td> 
   <td> 將Adobe Campaign與Twitter和Facebook同步。 <a href="../../social/using/about-social-marketing.md">進一步瞭解</a> <br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 事務性消息控制（消息中心——控制）<br /> </td> 
   <td> 管理從資訊系統觸發的事件產生的觸發訊息。 選填。<a href="../../message-center/using/about-transactional-messaging.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 事務性消息執行（消息中心——執行） <br /> </td> 
   <td> 確保更高的可用性和更好的負載管理。 選填。<a href="../../message-center/using/about-transactional-messaging.md">進一步瞭解</a><br /> </td> 
   <td> 執行<br /> </td>
  </tr> 
  <tr> 
   <td> LINE 道<br /> </td> 
   <td> 使用LINE渠道與Adobe Campaign傳送傳送。 選填。交易式訊息（訊息中心套件）強制性。 <a href="../../delivery/using/line-channel.md">進一步瞭解</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 直效郵件通道<br /> </td> 
   <td> 使用Adobe Campaign的直效郵件通道傳送傳送。 選填。<a href="../../delivery/using/about-direct-mail-channel.md">進一步瞭解</a><br /> </td> 
   <td> 全部<br /> </td>
  </tr> 
  <tr> 
   <td> 行動通道(SMS) <br /> </td> 
   <td> 使用Adobe Campaign的行動／簡訊頻道傳送傳送。 選填。<a href="../../delivery/using/sms-channel.md">進一步瞭解</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 行動應用程式頻道<br /> </td> 
   <td> 使用Adobe Campaign平台透過應用程式將個人化通知傳送至iOS和Android終端機。 選填。<a href="../../delivery/using/about-mobile-app-channel.md">進一步瞭解</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 內容管理員<br /> </td> 
   <td> 建立定期電子報或網站，然後驗證並發佈訊息。 <a href="../../delivery/using/about-content-management.md">進一步瞭解</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> 線上調查（調查管理員）<br /> </td> 
   <td> 建立並管理線上表單，以新增或修改描述檔資訊、訂閱、取消訂閱或競爭參賽表單。 選填。<a href="../../web/using/about-surveys.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> 可讓您分析和測量資料、計算統計資料、簡化並最佳化報表建立和計算。 此外，您還可以建立報表並建立目標人口族群。 選填。<a href="../../reporting/using/about-cubes.md">進一步瞭解</a><br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 回應管理員<br /> </td> 
   <td> 衡量行銷宣傳的成功與獲利能力，或為所有通訊管道提供建議。  選填。<a href="../../campaign/using/about-response-manager.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 存取外部資料（同盟資料存取）<br /> </td> 
   <td> 提供同盟資料存取(FDA)選項，以處理儲存在一或多個外部資料庫中的資訊，讓您可以存取外部資料，而不需變更Adobe Campaign資料的結構。  選填。<a href="../../workflow/using/accessing-an-external-database--fda-.md">進一步瞭解</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 行銷活動最佳化<br /> </td> 
   <td> 控制、篩選和監控傳送的傳送，讓傳送的訊息最符合客戶的需求和期望，並符合公司通訊政策。 選填。<a href="../../campaign/using/about-campaign-typologies.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送能力監控（電子郵件傳送能力）<br /> </td> 
   <td> 測量促銷活動在到達收件者收件匣時是否成功，而不會反彈或標示為垃圾訊息。 選填。<a href="../../delivery/using/about-deliverability.md">進一步瞭解</a> <br /> </td> 
   <td> 全部 </td> 
  </tr> 
  <tr> 
   <td> 抵用券管理<br /> </td> 
   <td> 建立一組抵用券，以新增至即將推出的行銷優惠。 選填。<a href="../../delivery/using/personalized-coupons.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱呈現(IR)<br /> </td> 
   <td> 可讓您預覽在可能收到訊息的不同上下文中傳送的訊息，並檢查主要桌上型電腦和應用程式的相容性。 選填。<a href="../../delivery/using/inbox-rendering.md">進一步瞭解</a><br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 中央／本地行銷（分佈式行銷）<br /> </td> 
   <td> 在中央實體（總部、行銷部門等）之間實施合作宣傳 及當地實體（銷售點、地區代理等）。 選填。<a href="../../campaign/using/about-distributed-marketing.md">進一步瞭解</a><br /> </td> 
   <td> 行銷 </td> 
  </tr> 
  <tr> 
   <td> CRM 連接器<br /> </td> 
   <td> 提供多種CRM連接器，以連結您的Adobe Campaign平台與協力廠商系統。  <a href="../../platform/using/crm-connectors.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> 網頁分析連接器<br /> </td> 
   <td> 可讓Adobe Campaign和Adobe Analytics透過Web Analytics連接器套件進行互動。 與事務性消息傳遞（消息中心包）不相容。 <a href="../../platform/using/adobe-analytics-data-connector.md">進一步瞭解</a><br /> </td> 
   <td> 行銷 </td> 
  </tr> 
  <tr> 
   <td> AEM整合<br /> </td> 
   <td> 可讓您直接在Adobe Experience Manager中管理電子郵件傳送內容及表單，以利運用AEM的內容編輯功能以及Adobe Campaign的傳送能力。 <a href="../../integrations/using/about-adobe-experience-manager.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud共用觀眾整合<br /> </td> 
   <td> 可讓您使用Adobe Experience Cloud解決方案和核心服務來交換和分享受眾／細分。 需要IMS <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> Integration with Adobe Experience Cloud<br /> </td> 
   <td> 可讓您從不同的Adobe Experience Cloud解決方案匯入和匯出觀眾／區段至Adobe Campaign。 選填。<a href="../../integrations/using/configuring-ims.md#installing-the-package">進一步瞭解</a> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> 隱私權資料保護法規<br /> </td> 
   <td> 包含其他功能，可協助您在Campaign Classic中符合隱私權規範。 <a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html">進一步瞭解</a> <br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> 詳細說明中間採購伺服器的安裝與設定，以及實例的部署，讓第三方在中間採購模式中傳送訊息。 選填。<a href="../../installation/using/mid-sourcing-server.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷 </td> 
  </tr> 
  <tr> 
   <td> 中間來源平台<br /> </td> 
   <td> 此配置是代管(ASP)配置和內部化之間的最佳中間解決方案。 對外執行元件是在Adobe Campaign所代管的「中部採購」伺服器上執行。 選填。<a href="../../installation/using/mid-sourcing-server.md">進一步瞭解</a> <br /> </td> 
   <td> 中部採購 </td> 
  </tr> 
  <tr> 
   <td> AMP支援<br /> </td> 
   <td> 可讓您針對電子郵件格式使用全新的互動式AMP，並傳送動態電子郵件。 選填。<a href="../../delivery/using/defining-interactive-content.md">進一步瞭解</a> <br /> </td> 
   <td> 全部 </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> 橋接Adobe Campaign v7和Adobe Campaign Standard。 它是Campaign v7中的整合功能，可自動將資料複製至Campaign Standard，將兩種應用程式的優點結合在一起。 選填。<a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">進一步瞭解</a> <br /> </td> 
   <td> 行銷 </td> 
  </tr> 
 </tbody> 
</table>

### 消息中心包 {#message-center-package}

您必須安裝傳送渠道（電子郵件、行動通道、行動應用程式通道等） 安裝事務性消息傳遞（消息中心軟體包）之前。 如果您已啟動電子郵件專用的「訊息中心」專案，且日後需要新增渠道，您必須遵循下列步驟：

1. 使用套件匯入精靈( ******[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**)安裝新頻道，例如行動頻道。
1. 匯入檔案( **[!UICONTROL Tools > Advanced > Import package > File]**)，然後選取：

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. 在中， **[!UICONTROL XML data content to import]**&#x200B;僅保留與相關渠道對應的「消息中心」傳送模板。 例如，如果您已新增 **Mobile頻道********[!UICONTROL Mobile transactional message]** ，請僅保留與(smsTriggerMessage)範本對應的實體元素。 如果您已新增行動應 **用程式頻道**，請只保留 **iOS交易訊息範本(iosTriggerMessage)和** Android交易訊息 **** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>如果在LINE之前安裝了消息中心包，則LINE的消息中心交付模板將不可用

