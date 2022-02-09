---
product: campaign
title: 異動訊息傳送架構
description: 本節介紹Adobe Campaign Classic事務性消息傳遞體系結構和提供事務性消息的可用渠道
exl-id: 0a059397-b037-405b-b9c1-94a4a072674d
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 1%

---

# 異動訊息傳送架構 {#transactional-messaging-architecture}

![](../../assets/v7-only.svg)

事務性消息傳遞依賴於由以下幾個實例組成的特定體系結構：

* A **控制實例**，在其中建立消息模板。

* 一個或多個 **執行實例**，接收事件並傳遞消息。

![](assets/messagecenter_diagram.png)

| 控制實例 | 執行實例 |
|--- |--- |
| Adobe Campaign用戶登錄到控制實例： <ul><li>建立事務性消息模板</li><li>使用種子清單生成消息預覽</li><li>顯示報告</li><li>監視執行實例</li></ul> | 執行實例的目的是： <ul><li>接收事件</li><li>將它們連結到事務性消息模板</li><li>向每個收件人發送個性化消息</li></ul> |

## 安裝實例 {#installing-instances}

在安裝事務性消息包時需要採取幾種預防措施。 Adobe建議您在投入生產前在test環境中工作。 您還需要有相容的Adobe Campaign許可證。 有關詳細資訊，請與您的Adobe帳戶主管聯繫。

>[!IMPORTANT]
>
>控制實例和執行實例必須安裝在不同的電腦上。 他們不能共用同一Campaign實例。

如果需要使用多個通道，則必須在安裝事務性消息包之前安裝和配置相關包。 有關此的詳細資訊，請參閱 [添加傳遞渠道](#adding-a-delivery-channel)。

## 控制實例 {#control-instance}

要在電腦上安裝控制實例，請選擇 **[!UICONTROL Transactional message control]** 通過 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 的子菜單。 有關此的詳細資訊，請參閱 [安裝Campaign Classic標準包](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/messagecenter_install_controlinstance_001.png)

中介紹了配置控制實例的詳細步驟 [此部分](../../message-center/using/configuring-instances.md#control-instance)。

### 支援多個控制實例 {#supporting-several-control-instances}

>[!IMPORTANT]
>
>只有內部環境才支援與多個控制實例共用執行群集。

可以在多個控制實例之間共用執行群集。 例如，如果您管理多個專用儲存，則可以為每個品牌配置一個控制實例，並將它們連結到同一執行群集。

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>有關必要配置的詳細資訊，請參閱 [使用多個控制項實例](../../message-center/using/configuring-instances.md#using-several-control-instances)。

## 執行實例 {#execution-instance}

要在電腦上安裝執行實例，請選擇 **[!UICONTROL Transactional message execution]** 通過 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 的子菜單。 有關此的詳細資訊，請參閱 [安裝Campaign Classic標準包](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/messagecenter_install_executioninstance_001.png)

有關配置執行實例的詳細步驟，請參見 [此部分](../../message-center/using/configuring-instances.md#execution-instance)。

## 可用的傳遞渠道

預設情況下，電子郵件通道可用。 要在多個頻道上傳遞事務性消息，您可以添加其他頻道（移動頻道、移動應用頻道等）。

>[!IMPORTANT]
>
>添加傳遞渠道（移動渠道、移動應用渠道等） 必須在安裝事務性消息包之前執行。

### 添加傳遞渠道 {#adding-a-delivery-channel}

Adobe建議您 **在安裝事務性消息包之前，始終添加傳遞渠道包**。

但是，如果您已在電子郵件通道上啟動事務性消息傳遞項目，則在項目期間決定添加新通道，您可以執行以下步驟。

>[!NOTE]
>
>此過程僅適用於使用安裝在與他們工作在同一台電腦上的Windows NLServer的客戶。

1. 安裝所需的通道，例如 **移動頻道**，使用包導入嚮導(**[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]**)。
1. 執行檔案導入(**[!UICONTROL Tools > Advanced > Import package... > File]**)，然後選擇 **資料&#x200B;**`[Your language]`**packagemessageCenter.xml** 的子菜單。
1. 在 **[!UICONTROL XML content of the data to import]**，僅保留與添加的渠道對應的傳遞模板。 例如，如果已添加 **移動頻道**，僅保留 **實體** 與 **[!UICONTROL Mobile transactional message]** (smsTriggerMessage)。 如果已添加 **移動應用頻道**，僅保留 **iOS事務消息** (iosTriggerMessage)和 **Android事務消息** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)

<!--## Transactional messages and inbound Interaction {#transactional-messages-and-inbound-interaction}

When combined with the Inbound Interaction module, transactional messaging enables you to insert a marketing offer dedicated to the recipient into the message.

>[!NOTE]
>
>The Interaction module is detailed in [Interaction](../../interaction/using/interaction-and-offer-management.md).

To use transactional messaging with Interaction, you need to apply the following configurations:

* Install the **Interaction** package onto the control instance and configure your offer catalog.

  >[!IMPORTANT]
  >
  >Do not replicate the offers onto the execution instances.

* The event must include an identifier linked to the recipients, for personalizing offers. The **@externalId** attribute must contain the value of this identifier. **Interaction** is configured by default to identify the recipient of the primary key:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
  ```

  You can configure **Interaction** so that identification takes place in the field of your choice, for example on the email address:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
  ```

Create your delivery templates the way you would for an email campaign:

* Add the offer to your transactional message template.
* Check the preview, send a proof and publish the template.

You also have to enable the unitary mode on your offer spaces. For more on this, refer to [this section](../../interaction/using/creating-offer-spaces.md).-->

### 異動推送通知 {#transactional-messaging-and-push-notifications}

與Mobile App通道模組結合使用時，事務性消息傳遞使您能夠通過移動設備上的通知推送事務性消息。

>[!NOTE]
>
>Mobile App頻道詳情請參閱 [此部分](../../delivery/using/about-mobile-app-channel.md)。

要將事務性消息模組與Mobile App Channel一起使用，需要應用以下配置：

1. 安裝 **移動應用頻道** 包到控制項和執行實例上。
1. 複製 **移動應用** 鍵入Adobe Campaign服務以及它在執行實例中包含的移動應用程式。

事件必須包含以下元素：

* 移動設備ID(**註冊ID** 適用於Android和 **設備令牌** iOS)。 此ID表示通知將發送到的「地址」。
* 到移動應用程式或整合密鑰的連結(**UU**)，用於恢復特定於應用程式的連接資訊。
* 將通知發送到的通道(**希望頻道**):iOS41支，安卓42支
* 用於個性化的所有資料

下面是包含此資訊的事件的示例：

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation=”none” uuid="com.adobe.NeoMiles"/>
                <ctx>
                    <deliveryTime>1:30 PM</deliveryTime>
                    <url>http://www.adobe.com</url>
                </ctx>
              </rtEvent>

         </urn:domEvent>
     </urn:PushEvent>           
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

>[!NOTE]
>
>消息模板的建立保持不變。

### 事務性消息傳遞和LINE {#transactional-messaging-and-line}

與LINE Channel結合使用，事務性消息允許您在安裝在消費者移動設備上的LINE應用上發送即時消息。 當LINE用戶添加品牌頁面時，此消息用於發送歡迎消息。

要將事務性消息模組與LINE一起使用，您的配置需要以下元素 **營銷** 實例 **執行** 實例：

* 安裝 **[!UICONTROL LINE Connect]** 包。
* 安裝 **[!UICONTROL Transactional message control]** 打包，以及 **[!UICONTROL Transactional message execution]** 執行實例上的包。
* 建立LINE **外部帳戶** 和 **服務** 在兩個實例上，它們的命名相同，以便同步。 有關如何建立LINE外部帳戶和服務的詳細資訊，請參閱 [此部分](../../delivery/using/line-channel.md#setting-up-line-channel)。

然後，從 **[!UICONTROL Explorer]** , **[!UICONTROL Platform]** > **[!UICONTROL External account]** ，您需要在兩個實例上配置不同的外部帳戶：

1. 建立 **[!UICONTROL External database]** 外部帳戶 **執行** 具有以下配置的實例：

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** :根據需要將外部帳戶命名為。
   * **[!UICONTROL Type]** :選擇 **[!UICONTROL External database]** 。
   * **[!UICONTROL Enabled]** 的子菜單。

   從 **[!UICONTROL Connection]** 類別：

   * **[!UICONTROL Type]** :選擇資料庫伺服器，例如PostgresSQL。
   * **[!UICONTROL Server]** :輸入資料庫伺服器URL。
   * **[!UICONTROL Account]** :輸入資料庫帳戶。

      >[!NOTE]
      >
      >資料庫用戶需要對以下表具有FDA連接的讀取權限：XtkOption、NmsVisitor、NmsVisitorSub、NmsService、NmsBroadLogRtEvent、NmsBroadLogBatchEvent、NmsTrackingLogRtEvent、NmsTrackingLogBatchEvent、NmsRtEvent、NmsBatchEvent、NmsBroadLogMsg、NmsTrackingUrl、NmsDelivery、NmsWebTrackingLogXtkFolder。

   * **[!UICONTROL Password]** :輸入資料庫帳戶的密碼。
   * **[!UICONTROL Database]** :輸入執行實例的資料庫名稱。
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** 的子菜單。


1. 建立 **[!UICONTROL External Database]** 帳戶 **營銷** 實例。

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** :根據需要將外部帳戶命名為。
   * **[!UICONTROL Type]** :選擇 **[!UICONTROL External database]** 。
   * 必須選中「已啟用」框。

   從 **[!UICONTROL Connection]** 類別：

   * **[!UICONTROL Type]** :選擇 **[!UICONTROL HTTP relay to remote Database]** 。
   * **[!UICONTROL Server]** :輸入執行實例的市場活動伺服器URL。
   * **[!UICONTROL Account]** :輸入用於訪問執行實例的帳戶。
   * **[!UICONTROL Password]** :輸入用於訪問執行實例的帳戶的密碼。
   * **[!UICONTROL Data Source]** :輸入以下語法 **[!UICONTROL nms:extAccount:ID of your external database account in the execution instance]** 。


1. 建立 **[!UICONTROL Execution instance]** 外部帳戶 **營銷** 實例，使用以下配置建立資料同步工作流：

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** :根據需要將外部帳戶命名為。
   * **[!UICONTROL Type]** :選擇 **[!UICONTROL Execution instance]** 。
   * 必須選中「已啟用」框。

   從 **[!UICONTROL Connection]** 類別：

   * **[!UICONTROL URL]** :輸入執行實例的URL。
   * **[!UICONTROL Account]** :輸入用於訪問執行實例的帳戶。
   * **[!UICONTROL Password]** :輸入用於訪問執行實例的帳戶的密碼。

   從 **[!UICONTROL Account connection method]** 類別：

   * **[!UICONTROL Method]** :選擇 **[!UICONTROL Federated Data Access (FDA)]** 。
   * **[!UICONTROL FDA account]** :從下拉清單中選擇FDA帳戶。
   * 按一下 **[!UICONTROL Create the archiving workflow]** 按鈕。
   * 按一下 **[!UICONTROL Create data synchronization workflow]** 按鈕建立LINE資料同步工作流。



1. 現在可以開始 [建立事務消息](../../message-center/using/creating-the-message-template.md)。
