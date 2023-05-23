---
product: campaign
title: 安裝Campaign Classic內置軟體包
description: 瞭解如何安裝活動內置軟體包
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 13%

---

# 安裝Campaign Classic內置軟體包{#installing-campaign-standard-packages}



## 關於內置包 {#campaign-standard-packages}

內置軟體包包含一組功能，這些功能可根據您的需要並根據您的合同進行安裝。 下面提供了「活動」內置包的完整清單。

>[!CAUTION]
>
>您只能安裝與許可協定中提到的選項對應的軟體包。
>
>安裝新軟體包可能會影響您的所有平台：在最終部署之前，必須對它進行測試和驗證。
>
>安裝軟體包後，無法卸載它。
>
>作為托管或混合型客戶，請與Adobe聯繫以部署新的內置軟體包。

要安裝內置軟體包，請執行以下操作：

1. 從訪問包導入嚮導 **[!UICONTROL Tools > Advanced > Import package]** 在Adobe Campaign客戶端控制台中。
1. 選取 **[!UICONTROL Install a standard package]**。
1. 在包清單中，檢查要安裝的包。
   >[!NOTE]
   >
   >當軟體包灰顯時，它表示已安裝或與實例不相容。 下表詳述了相容性。
1. 按一下 **[!UICONTROL Next]**，則 **[!UICONTROL Start]** 啟動軟體包安裝。

   安裝軟體包後，進度欄將顯示 **100%** 您可以在安裝日誌中看到以下消息： **[!UICONTROL Installation of packages successful]**。

1. **[!UICONTROL Close]** 安裝窗口。

現在已安裝軟體包。

### 現成包清單 {#list-of-standard-packages}

下表列出了所有市場活動內置包。

<table> 
 <thead> 
  <tr> 
   <th> 套件 </th> 
   <th> 說明 </th> 
   <th> 實例類型 </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 傳遞<br /> </td> 
   <td> 監視發送消息時遇到的交貨和最終問題。 <a href="../../delivery/using/about-delivery-monitoring.md">了解更多</a><br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 市場營銷活動（市場活動）<br /> </td> 
   <td> 定義、優化、執行和分析通信和市場營銷活動。 <a href="../../campaign/using/designing-marketing-campaigns.md">了解更多</a><br /> </td> 
   <td> 行銷</td>
  </tr> 
  <tr> 
   <td> 市場營銷資源(MRM)<br /> </td> 
   <td> 通過提供對任務、預算和市場營銷資源的管理和跟蹤，以協作模式控制市場營銷活動。 <a href="../../mrm/using/about-marketing-resource-management.md">了解更多</a> <br /> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> 提供引擎（交互）<br /> </td> 
   <td> 在與給定聯繫人（客戶或目標）的交互過程中，通過使他們成為單個或多個適應的優惠而即時響應。  選填。<a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">了解更多</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 具有執行實例的提供引擎的控制。 選填。<br /> </td> 
   <td> 要在提供引擎（交互）的控制實例上安裝的包。 <a href="../../interaction/using/distributed-architectures.md#packages-configuration">了解更多</a> </td> 
   <td> 行銷<br /> </td>  
  </tr> 
  <tr> 
   <td> 為執行實例提供引擎。 選填。<br /> </td> 
   <td> 要在服務引擎（交互）的執行實例上安裝的包。 <a href="../../interaction/using/distributed-architectures.md">了解更多</a> </td> 
   <td> 中，執行 <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> 社交網路（社會營銷） <br /> </td> 
   <td> 使Adobe Campaign與Twitter和Facebook同步。 <a href="../../social/using/about-social-marketing.md">了解更多</a> <br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 事務性消息控制項（消息中心 — 控制項）<br /> </td> 
   <td> 管理從資訊系統觸發的事件生成的觸發消息。 選填。<a href="../../message-center/using/about-transactional-messaging.md">了解更多</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 事務性消息執行（消息中心 — 執行） <br /> </td> 
   <td> 確保更高的可用性和更好的負載管理。 選填。<a href="../../message-center/using/about-transactional-messaging.md">了解更多</a><br /> </td> 
   <td> 執行<br /> </td>
  </tr> 
  <tr> 
   <td> LINE 頻道<br /> </td> 
   <td> 使用LINE渠道和Adobe Campaign發送交貨。 選填。事務性消息傳遞（消息中心包）是必需的。 <a href="../../delivery/using/line-channel.md">了解更多</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 直郵渠道<br /> </td> 
   <td> 使用直接郵寄渠道與Adobe Campaign發送遞送。 選填。<a href="../../delivery/using/about-direct-mail-channel.md">了解更多</a><br /> </td> 
   <td> 全部<br /> </td>
  </tr> 
  <tr> 
   <td> 行動裝置管道 (簡訊) <br /> </td> 
   <td> 使用移動/SMS頻道與Adobe Campaign發送交付。 選填。<a href="../../delivery/using/sms-channel.md">了解更多</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
   <tr> 
   <td> 電話管道<br /> </td> 
   <td> 使用與Adobe Campaign的電話頻道發送交貨。 用於呼叫中心。 選填。<a href="../../delivery/using/communication-channels.md">了解更多</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 行動應用程式頻道<br /> </td> 
   <td> 使用Adobe Campaign平台通過應用向iOS和安卓終端發送個性化通知。 選填。<a href="../../delivery/using/about-mobile-app-channel.md">了解更多</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 內容管理器<br /> </td> 
   <td> 建立經常性新聞稿或網站，然後驗證和發佈您的郵件。 <a href="../../delivery/using/about-content-management.md">了解更多</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> 線上調查（調查經理）<br /> </td> 
   <td> 建立並管理聯機表單以添加或修改配置檔案資訊、訂閱、取消訂閱或競爭條目表單。 選填。<a href="../../surveys/using/about-surveys.md">了解更多</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 營銷分析<br /> </td> 
   <td> 使您能夠分析和測量資料、計算統計資訊、簡化和優化報表建立和計算。 此外，您還可以建立報告並構建目標群體。 選填。<a href="../../reporting/using/ac-cubes.md">了解更多</a><br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 回應管理員<br /> </td> 
   <td> 衡量營銷活動的成功和盈利能力，或為所有溝通渠道提供建議。  選填。<a href="../../response/using/about-response-manager.md">了解更多</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 訪問外部資料（聯合資料存取）<br /> </td> 
   <td> 提供聯合資料存取(FDA)選項，以便處理儲存在一個或多個外部資料庫中的資訊，以便您可以訪問外部資料而不更改Adobe Campaign資料的結構。  選填。<a href="../../workflow/using/accessing-an-external-database--fda-.md">了解更多</a> <br /> </td> 
   <td> 全部<br /> </td> 
  </tr> 
  <tr> 
   <td> 行銷活動最佳化<br /> </td> 
   <td> 控制、過濾和監控交貨的發送，以便按照公司通信策略發送的消息能夠最好地滿足客戶的需求和期望。 選填。<a href="../../campaign-opt/using/about-campaign-typologies.md">了解更多</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 可交付性監視（電子郵件可交付性）<br /> </td> 
   <td> 衡量您的活動在到達收件人收件箱時的成功程度，而不會彈跳或標籤為垃圾郵件。 選填。<a href="../../delivery/using/about-deliverability.md">了解更多</a> <br /> </td> 
   <td> 全部 </td> 
  </tr> 
  <tr> 
   <td> 優惠券管理<br /> </td> 
   <td> 建立一組優惠券，以添加到即將到來的營銷優惠。 選填。<a href="../../delivery/using/personalized-coupons.md">了解更多</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱呈現(IR)<br /> </td> 
   <td> 使您能夠預覽在不同上下文中發送的消息，並檢查主要台式機和應用程式的相容性。 選填。<a href="../../delivery/using/inbox-rendering.md">了解更多</a><br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 中央/本地市場（分佈式市場）<br /> </td> 
   <td> 在中央實體（總部、營銷部門等）之間實施合作活動 本地實體 (銷售地點、地區代理等)。 選填。<a href="../../distributed/using/about-distributed-marketing.md">了解更多</a><br /> </td> 
   <td> 行銷 </td> 
  </tr> 
  <tr> 
   <td> CRM 連接器<br /> </td> 
   <td> 提供各種CRM連接器，用於將您的Adobe Campaign平台連結到您的第三方系統。  <a href="../../platform/using/crm-connectors.md">了解更多</a> <br /> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> Web Analytics連接器<br /> </td> 
   <td> 允許Adobe Campaign和Adobe Analytics通過Web Analytics連接器包進行交互。 與事務性消息傳遞（消息中心包）不相容。 <a href="../../platform/using/adobe-analytics-connector.md">了解更多</a><br /> </td> 
   <td> 行銷 </td> 
  </tr> 
  <tr> 
   <td> AEM整合<br /> </td> 
   <td> 允許您直接在Adobe Experience Manager管理電子郵件遞送的內容和表單，以便從內容編輯功能AEM和Adobe Campaign的遞送能力中獲益。 <a href="../../integrations/using/about-adobe-experience-manager.md">了解更多</a> <br /> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud共用受眾整合<br /> </td> 
   <td> 允許您與Adobe Experience Cloud解決方案和核心服務交流和分享受眾/群。 需要IMS <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">了解更多</a> <br /> </td> 
   <td> 行銷<br /> </td> 
  </tr> 
  <tr> 
   <td> 與Adobe Experience Cloud<br /> </td> 
   <td> 使您能夠將不同Adobe Experience Cloud解決方案的受眾/分區導入和導出到Adobe Campaign。 選填。<a href="../../integrations/using/configuring-ims.md#installing-the-package">了解更多</a> </td> 
   <td> 行銷</td> 
  </tr> 
  <tr> 
   <td> 隱私權資料保護法規<br /> </td> 
   <td> 包含其他功能，可幫助您在Campaign Classic中實現隱私合規性。 <a href="https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html">了解更多</a> <br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 轉移到中間採購 <br /> </td> 
   <td> 詳細說明中間採購伺服器的安裝和配置，以及使第三方能夠在中間採購模式下發送消息的實例的部署。 選填。<a href="../../installation/using/mid-sourcing-server.md">了解更多</a> <br /> </td> 
   <td> 行銷 </td> 
  </tr> 
  <tr> 
   <td> 中間來源平台<br /> </td> 
   <td> 此配置是托管(ASP)配置和內部化之間的最佳中間解決方案。 面向外的執行元件在Adobe Campaign托管的「中間採購」伺服器上執行。 選填。<a href="../../installation/using/mid-sourcing-server.md">了解更多</a> <br /> </td> 
   <td> 中間來源 </td> 
  </tr> 
  <tr> 
   <td> AMP支援<br /> </td> 
   <td> 使您能夠使用新的互動式AMP進行電子郵件格式，併發送動態電子郵件。 選填。<a href="../../delivery/using/defining-interactive-content.md">了解更多</a> <br /> </td> 
   <td> 全部 </td> 
  </tr> 
  <tr> 
   <td> ACS連接器（不建議使用）<br /> </td> 
   <td> 橋Adobe Campaign七號和Adobe Campaign Standard。 它是Campaign v7中的一個整合功能，可自動將資料複製到Campaign Standard中，將兩個應用程式中的最佳組合在一起。 選填。<br /> </td> 
   <td> 行銷 </td> 
  </tr> 
 </tbody> 
</table>

### 消息中心包 {#message-center-package}

您必須安裝傳遞通道（電子郵件、移動通道、移動應用通道、LINE等） 安裝事務性消息（消息中心包）之前。 如果您已啟動僅通過電子郵件發送的郵件中心項目，並且以後需要添加新渠道，則必須執行以下步驟：

1. 安裝新通道，例如 **移動頻道**，使用包導入嚮導( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**)。
1. 導入檔案( **[!UICONTROL Tools > Advanced > Import package > File]**)，然後選擇：

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. 在 **[!UICONTROL XML data content to import]**，僅保留與相關渠道對應的消息中心傳遞模板。 例如，如果已添加 **移動頻道**，僅保留 **實體** 與 **[!UICONTROL Mobile transactional message]** (smsTriggerMessage)模板。 如果已添加 **移動應用頻道**，僅保留 **iOS事務消息** 模板(iosTriggerMessage)和 **Android事務消息** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)


### [!DNL LINE] 通道設定{#line-package}

設定 [!DNL LINE] 通道，必須先安裝 [!DNL LINE] 檔案。

在中間採購配置的上下文中，您需要：

* 安裝 [!DNL LINE] 營銷和MID實例上的軟體包

* 設定 [!DNL LINE] mkt實例上的外部帳戶通過更改傳遞模式指向中間實例。 [了解更多](../../delivery/using/line-channel.md#configure-line-external)

* 設定 [!DNL LINE] MID實例上的外部帳戶中的憑據。

>[!CAUTION]
>
>消息中心傳遞模板 [!DNL LINE] 如果在之前安裝了Message Center軟體包，則通道將不可用 [!DNL LINE]。