---
product: campaign
title: 安裝 Campaign Classic 內建套件
description: 了解如何安裝Campaign內建套件
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 6%

---

# 安裝 Campaign Classic 內建套件{#installing-campaign-standard-packages}

## 關於內建套件 {#campaign-standard-packages}

內建套件包含一組功能，可根據您的需求並根據您的合約進行安裝。 下方提供Campaign內建套件的完整清單。

>[!CAUTION]
>
>您只能安裝與許可協定中提及的選項相對應的軟體包。
>
>安裝新套件可能會影響您的所有平台：在最終部署之前，必須先測試並驗證。
>
>安裝軟體包後，您無法卸載它。

要安裝內置軟體包：

1. 從Adobe Campaign用戶端主控台的&#x200B;**[!UICONTROL Tools > Advanced > Package import...]**&#x200B;存取套件匯入精靈。
1. 選取 **[!UICONTROL Install a standard package]**。
1. 在包清單中，檢查要安裝的包。
   >[!NOTE]
   >
   >當套件呈現灰色時，表示已安裝或與您的執行個體不相容。 下表詳細說明相容性。
1. 按一下&#x200B;**[!UICONTROL Next]**，然後按一下&#x200B;**[!UICONTROL Start]**&#x200B;以啟動軟體包安裝。

   安裝軟體包後，進度欄顯示&#x200B;**100%**，您可以在安裝日誌中看到以下消息：**[!UICONTROL Installation of packages successful]**。

1. **[!UICONTROL Close]** 安裝窗口。

現在已安裝套件。

### 現成套件清單 {#list-of-standard-packages}

下表列出所有Campaign內建套件。

<table> 
 <thead> 
  <tr> 
   <th> 套件 </th> 
   <th> 說明 </th> 
   <th> 例項類型 </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 傳遞<br /> </td> 
   <td> 監視傳送訊息時遇到的傳送及最終問題。 <a href="../../delivery/using/about-delivery-monitoring.md">深入瞭解</a><br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 行銷活動（行銷活動）<br /> </td> 
   <td> 定義、最佳化、執行和分析通訊和行銷活動。 <a href="../../campaign/using/designing-marketing-campaigns.md">更多詳情</a><br /> </td> 
   <td> 行銷</td>
  </tr> 
  <tr> 
   <td> 行銷資源(MRM)<br /> </td> 
   <td> 透過提供任務、預算和行銷資源的管理和追蹤，以協作模式控制行銷動作。 <a href="../../mrm/using/about-marketing-resource-management.md">更多詳情</a> <br /> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> 優惠方案引擎（互動）<br /> </td> 
   <td> 在與指定連絡人（客戶或目標）互動期間，透過讓他們成為單一或數個已調整的選件，即時回應。  選填。<a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">更多詳情</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用執行例項控制優惠方案引擎。 選填。<br /> </td> 
   <td> 要安裝在優惠方案引擎的控制執行個體（互動）上的套件。 <a href="../../interaction/using/distributed-architectures.md#packages-configuration">更多詳情</a> </td> 
   <td> 行銷<br /> </td>  
  </tr> 
  <tr> 
   <td> 執行例項的選件引擎。 選填。<br /> </td> 
   <td> 要安裝在優惠方案引擎執行例項（互動）上的套件。 <a href="../../interaction/using/distributed-architectures.md">更多詳情</a> </td> 
   <td> Mid，執行<br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> 社交網路（社交行銷）<br /> </td> 
   <td> 將Adobe Campaign與Twitter和Facebook同步。 <a href="../../social/using/about-social-marketing.md">更多詳情</a> <br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 交易式訊息控制(Message Center - Control)<br /> </td> 
   <td> 管理從資訊系統觸發的事件產生的觸發訊息。 選填。<a href="../../message-center/using/about-transactional-messaging.md">更多詳情</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易式訊息執行（Message Center — 執行）<br /> </td> 
   <td> 確保更高的可用性和更好的負載管理。 選填。<a href="../../message-center/using/about-transactional-messaging.md">更多詳情</a><br /> </td> 
   <td> 執行<br /> </td>
  </tr> 
  <tr> 
   <td> LINE 頻道<br /> </td> 
   <td> 使用LINE通道與Adobe Campaign傳送。 選填。交易式傳訊（訊息中心套件）必要。 <a href="../../delivery/using/line-channel.md">更多詳情</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 直接郵件通道<br /> </td> 
   <td> 使用直接郵件通道與Adobe Campaign傳送。 選填。<a href="../../delivery/using/about-direct-mail-channel.md">更多詳情</a><br /> </td> 
   <td> 全部<br /> </td>
  </tr> 
  <tr> 
   <td> 行動通道(SMS)<br /> </td> 
   <td> 使用行動/簡訊通道搭配Adobe Campaign傳送。 選填。<a href="../../delivery/using/sms-channel.md">更多詳情</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
   <tr> 
   <td> 電話通道<br /> </td> 
   <td> 使用電話通道與Adobe Campaign傳送傳遞。 用於客服中心。 選填。<a href="../../delivery/using/communication-channels.md">更多詳情</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 行動應用程式頻道<br /> </td> 
   <td> 使用Adobe Campaign平台，透過應用程式將個人化通知傳送至iOS和Android終端機。 選填。<a href="../../delivery/using/about-mobile-app-channel.md">更多詳情</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 內容管理員<br /> </td> 
   <td> 建立經常性電子報或網站，然後驗證並發佈您的訊息。 <a href="../../delivery/using/about-content-management.md">更多詳情</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> 線上調查（調查管理員）<br /> </td> 
   <td> 建立並管理線上表單，以添加或修改配置檔案資訊、訂閱、取消訂閱或競爭項目表單。 選填。<a href="../../surveys/using/about-surveys.md">更多詳情</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 行銷分析<br /> </td> 
   <td> 可讓您分析和測量資料、計算統計資料、簡化並最佳化報表建立和計算。 此外，您也可以建立報表並建立目標母體。 選填。<a href="../../reporting/using/about-cubes.md">更多詳情</a><br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 回應管理員<br /> </td> 
   <td> 衡量營銷活動的成功和盈利能力，或為所有通信渠道提供建議。  選填。<a href="../../campaign/using/about-response-manager.md">更多詳情</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 存取外部資料（同盟資料存取）<br /> </td> 
   <td> 提供同盟資料存取(FDA)選項，以處理儲存在一或多個外部資料庫中的資訊，讓您不需變更Adobe Campaign資料的結構即可存取外部資料。  選填。<a href="../../workflow/using/accessing-an-external-database--fda-.md">更多詳情</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 行銷活動最佳化<br /> </td> 
   <td> 控制、篩選及監控傳送的傳送，讓傳送的訊息最符合客戶的需求和期望，並符合公司通訊原則。 選填。<a href="../../campaign/using/about-campaign-typologies.md">更多詳情</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳遞能力監控（電子郵件傳遞能力）<br /> </td> 
   <td> 測量行銷活動到達收件者收件匣的成功程度，而不會反彈或標示為垃圾訊息。 選填。<a href="../../delivery/using/about-deliverability.md">更多詳情</a> <br /> </td> 
   <td> 全部 </td> 
  </tr> 
  <tr> 
   <td> 抵用券管理<br /> </td> 
   <td> 建立一組抵用券，以新增至即將推出的行銷活動。 選填。<a href="../../delivery/using/personalized-coupons.md">更多詳情</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱呈現(IR)<br /> </td> 
   <td> 使您能夠預覽在不同上下文中發送的郵件，並檢查主要案頭和應用程式的相容性。 選填。<a href="../../delivery/using/inbox-rendering.md">更多詳情</a><br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 中央/地方行銷（分散式行銷）<br /> </td> 
   <td> 在中央實體（總部、行銷部門等）之間實施合作行銷活動 和地方實體（銷售點、地區代理等）。 選填。<a href="../../campaign/using/about-distributed-marketing.md">更多詳情</a><br /> </td> 
   <td> 行銷 </td> 
  </tr> 
  <tr> 
   <td> CRM 連接器<br /> </td> 
   <td> 提供多種CRM連接器，用於將您的Adobe Campaign平台連結至您的協力廠商系統。  <a href="../../platform/using/crm-connectors.md">更多詳情</a> <br /> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> Web Analytics連接器<br /> </td> 
   <td> 可讓Adobe Campaign和Adobe Analytics透過Web Analytics連接器套件互動。 與交易式訊息（訊息中心套件）不相容。 <a href="../../platform/using/adobe-analytics-connector.md">更多詳情</a><br /> </td> 
   <td> 行銷 </td> 
  </tr> 
  <tr> 
   <td> AEM整合<br /> </td> 
   <td> 可讓您直接在Adobe Experience Manager中管理電子郵件傳送的內容和表單，以受益於AEM內容編輯功能以及Adobe Campaign的傳送能力。 <a href="../../integrations/using/about-adobe-experience-manager.md">更多詳情</a> <br /> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud共用受眾整合<br /> </td> 
   <td> 可讓您與Adobe Experience Cloud解決方案和核心服務交換和共用受眾/區段。 需要IMS <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">更多詳情</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 與Adobe Experience Cloud的整合<br /> </td> 
   <td> 可讓您從不同的Adobe Experience Cloud解決方案匯入和匯出受眾/區段至Adobe Campaign。 選填。<a href="../../integrations/using/configuring-ims.md#installing-the-package">更多詳情</a> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> 隱私權資料保護法規<br /> </td> 
   <td> 包含其他功能，可協助您遵循Campaign Classic的隱私權。 <a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html">更多詳情</a> <br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 轉移至中間來源<br /> </td> 
   <td> 詳細說明中間來源補充伺服器的安裝和設定，以及執行個體的部署，該執行個體可讓第三方以中間來源補充模式傳送訊息。 選填。<a href="../../installation/using/mid-sourcing-server.md">更多詳情</a> <br /> </td> 
   <td> 行銷 </td> 
  </tr> 
  <tr> 
   <td> 中間來源平台<br /> </td> 
   <td> 此配置是托管(ASP)配置和內部化之間的最佳中間解決方案。 對外執行元件會在Adobe Campaign托管的「中間來源」伺服器上執行。 選填。<a href="../../installation/using/mid-sourcing-server.md">更多詳情</a> <br /> </td> 
   <td> 中間來源 </td> 
  </tr> 
  <tr> 
   <td> AMP支援<br /> </td> 
   <td> 可讓您使用新的互動式AMP，以處理電子郵件格式，並傳送動態電子郵件。 選填。<a href="../../delivery/using/defining-interactive-content.md">更多詳情</a> <br /> </td> 
   <td> 全部 </td> 
  </tr> 
  <tr> 
   <td> ACS 連結器<br /> </td> 
   <td> 橋梁Adobe Campaign v7和Adobe Campaign Standard。 這是Campaign v7中的整合功能，可自動將資料複製到Campaign Standard，將兩個應用程式的最佳功能結合在一起。 選填。<a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">更多詳情</a> <br /> </td> 
   <td> 行銷 </td> 
  </tr> 
 </tbody> 
</table>

### 訊息中心套件 {#message-center-package}

您必須安裝傳送通道（電子郵件、行動裝置通道、行動應用程式通道等） 安裝交易式訊息（訊息中心套件）之前。 如果您已啟動僅通過電子郵件發送的郵件中心項目，並且之後需要添加新通道，則必須執行以下步驟：

1. 使用套件匯入精靈(**[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**)安裝新通道，例如&#x200B;**行動通道**。
1. 匯入檔案(**[!UICONTROL Tools > Advanced > Import package > File]**)，然後選取：

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. 在&#x200B;**[!UICONTROL XML data content to import]**&#x200B;中，僅保留與相關通道對應的「消息中心」傳遞模板。 例如，如果您已新增&#x200B;**行動頻道**，請僅保留與&#x200B;**[!UICONTROL Mobile transactional message]**(smsTriggerMessage)範本對應的&#x200B;**entities**&#x200B;元素。 如果您已新增&#x200B;**行動應用程式頻道**，請僅保留&#x200B;**iOS交易式訊息**&#x200B;範本(iosTriggerMessage)和&#x200B;**Android交易式訊息**(androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>如果在LINE之前安裝了郵件中心包，則LINE的郵件中心傳送模板將不可用
