---
title: Adobe Campaign Classic交易式訊息架構
description: 本節說明Adobe Campaign Classic交易訊息架構。
page-status-flag: never-activated
uuid: a8fe7a37-6df7-49f4-838f-97a72e4a38f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: a910d5fe-cef4-47d8-b3bc-0055ef0d1afd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e8a9d8d63c01cc19380267fced45e180b4d7ccb4
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 0%

---


# 事務性消息傳遞體系結構{#transactional-messaging-architecture}

## 關於執行和控制實例 {#about-execution-and-control-instances}

在Adobe Campaign中，交易式訊息功能（又稱為訊息中心）旨在支援延展性並提供全年無休的服務。 它由幾個實例組成：

* 一個控制實例，消息模板是在中建立的，
* 接收事件並傳送訊息的一個或多個執行例項。

若要使用這些功能，Adobe Campaign使用者可登入控制例項以建立交易式訊息範本、使用種子清單產生訊息預覽、顯示報表及監控執行例項。

執行例項會接收事件、將其連結至交易訊息範本，並傳送個人化訊息給每個收件者。

![](assets/messagecenter_diagram.png)

## 支援數個控制例項 {#supporting-several-control-instances}

>[!CAUTION]
>
>只有內部部署環境才支援與多個控制實例共用執行群集。

可以在多個控制實例之間共用執行群集。 例如，如果您管理多個專業商店，則可以為每個品牌配置一個控制實例，並將它們全部連結到同一執行群集。

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>有關必要配置的詳細資訊，請參閱使 [用多個控制實例](../../message-center/using/creating-a-shared-connection.md#using-several-control-instances)。

## 安裝實例 {#installing-instances}

在安裝Transactional消息包時，需要採取幾種預防措施。 Adobe建議您在投入生產之前，先在測試環境中工作。 您也需要有相容的Adobe Campaign授權。 如需詳細資訊，請聯絡您的Adobe銷售代表。

>[!CAUTION]
>
>控制實例和執行實例必須安裝在不同的電腦上。 他們無法共用相同的促銷活動例項。

如果您需要使用多個渠道，則必須在安裝事務性消息包之前安裝並配置相關包。 請參閱 [新增傳送渠道](#adding-a-delivery-channel)。

* 要在電腦上安裝控制實例，請選擇模 **[!UICONTROL Transactional message control]** 塊。

   ![](assets/messagecenter_install_controlinstance_001.png)

* 要在電腦上安裝執行實例，請選擇模 **[!UICONTROL Transactional message execution]** 塊。

   ![](assets/messagecenter_install_executioninstance_001.png)

## 新增傳送渠道 {#adding-a-delivery-channel}

新增傳送渠道（行動通道、行動應用通道等） 必須在安裝Transactional消息包之前執行。 如果您已在電子郵件頻道上啟動交易式訊息專案，然後在專案期間決定新增新頻道，您必須遵循下列步驟：

1. 使用套件匯入精靈( ******[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]** )，安裝您需要的頻道，例如行動頻道。
1. 執行檔案匯入( **[!UICONTROL Tools > Advanced > Import package... > File]** )，並選取 ****`[Your language]`**** datakitnmspackagemessageCenter.xml檔案。
1. 在中， **[!UICONTROL XML content of the data to import]** 僅保留與新增渠道對應的傳送範本。 例如，如果您已新增 **Mobile頻道********[!UICONTROL Mobile transactional message]** ，請僅保留與(smsTriggerMessage)對應的實體元素。 如果您已新增 **行動應用程式頻道**，請只保留 **iOS交易訊息** (iosTriggerMessage)和 **Android交易訊息** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)

<!--## Transactional messages and inbound Interaction {#transactional-messages-and-inbound-interaction}

When combined with the Inbound Interaction module, transactional messaging enables you to insert a marketing offer dedicated to the recipient into the message.

>[!NOTE]
>
>The Interaction module is detailed in [Interaction](../../interaction/using/interaction-and-offer-management.md).

To use transactional messaging with Interaction, you need to apply the following configurations:

* Install the **Interaction** package onto the control instance and configure your offer catalog.

  >[!CAUTION]
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

## 交易式訊息和推播通知 {#transactional-messaging-and-push-notifications}

當與行動應用程式頻道模組結合時，交易訊息可讓您透過行動裝置上的通知來推播交易訊息。

>[!NOTE]
>
>「行動應用程式」頻道在本節中 [有詳細說明](../../delivery/using/about-mobile-app-channel.md)。

若要搭配行動應用程式頻道使用交易式訊息模組，您必須套用下列組態：

1. 將行動應 **** 用程式頻道套件安裝至控制項和執行例項。
1. 複製 **Mobile應用程式類型** Adobe Campaign服務，以及它在執行例項中包含的行動應用程式。

事件必須包含下列元素：

* 行動裝置ID(Android **的registrationId** ,iOS的 **deviceToken** )。 此ID代表通知要傳送至的「位址」。
* 行動應用程式的連結或整合金鑰(**uuid**)，可讓您復原應用程式的特定連線資訊。
* 將傳送通知的渠道(**whishedChannel**): iOS為41,Android為42
* 所有對個人化有用的資料

以下是包含此資訊之事件的範例：

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

## 交易式訊息與LINE {#transactional-messaging-and-line}

交易訊息與LINE Channel結合，可讓您在消費性行動裝置中安裝的LINE應用程式上傳送即時訊息。 當LINE使用者新增品牌頁面時，這會用來傳送歡迎訊息。

要將事務性消息模組與LINE一起使用，在您的 **marketing實例和執行實例上的配置需要以下** 元素 **** :

* 在兩個實 **[!UICONTROL LINE Connect]** 例上安裝軟體包。
* 在您的 **[!UICONTROL Transactional message control]** 行銷例項上安裝套件，並在執 **[!UICONTROL Transactional message execution]** 行例項上安裝套件。
* 在兩個實 **例上建立LINE外** 部帳戶 **** 和服務，其命名與要同步的實例相同。 有關如何建立LINE外部帳戶和服務的詳細資訊，請參閱本 [頁](../../delivery/using/line-channel.md#creating-a-line-account-and-an-external-account-)。

然後，從 **[!UICONTROL Explorer]** ，在 **[!UICONTROL Platform]** > **[!UICONTROL External account]** ，您需要在兩個例項上設定不同的外部帳戶：

1. 在您的 **[!UICONTROL External database]** 執行例項中建立 **外部帳戶** ，其設定如下：

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** : 視需要為您的外部帳戶命名。
   * **[!UICONTROL Type]** : 選擇 **[!UICONTROL External database]** 。
   * **[!UICONTROL Enabled]** 框。
   從類 **[!UICONTROL Connection]** 別：

   * **[!UICONTROL Type]** : 選擇資料庫伺服器，例如PostgresSQL。
   * **[!UICONTROL Server]** : 輸入資料庫伺服器URL。
   * **[!UICONTROL Account]** : 輸入您的資料庫帳戶。

      >[!NOTE]
      >
      >資料庫用戶需要對下清單具有讀取權限，以便FDA連接： XtkOption、NmsVisitor、NmsVisitorSub、NmsService、NmsBroadLogRtEvent、NmsBroadLogBatchEvent、NmsTrackingLogRtEvent、NmsTrackingLogBatchEvent、NmsRtEvent、NmsBatchEvent、NmsBroadLogMsg、NmsTrackingUrl、NmsDelivery、NmsWebTrackingLogXtkFolder。

   * **[!UICONTROL Password]** : 輸入資料庫帳戶的密碼。
   * **[!UICONTROL Database]** : 輸入執行實例的資料庫名。
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** 框。


1. 在您的 **[!UICONTROL External Database]** 行銷實例中 **使用** 下列設定建立帳戶。

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** : 視需要為您的外部帳戶命名。
   * **[!UICONTROL Type]** : 選擇 **[!UICONTROL External database]** 。
   * 必須勾選「啟用」方塊。
   從類 **[!UICONTROL Connection]** 別：

   * **[!UICONTROL Type]** : 選擇 **[!UICONTROL HTTP relay to remote Database]** 。
   * **[!UICONTROL Server]** : 輸入您促銷活動的執行例項伺服器URL。
   * **[!UICONTROL Account]** : 輸入用於訪問執行實例的帳戶。
   * **[!UICONTROL Password]** : 輸入用於訪問執行實例的帳戶的密碼。
   * **[!UICONTROL Data Source]** : 輸入下列語法 **[!UICONTROL nms:extAccount:ID of your external database account in the execution instance]** 。


1. 使用下 **[!UICONTROL Execution instance]** 列設定在您的行銷 **例項中建立外部帳戶** ，以建立資料同步工作流程：

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]** : 視需要為您的外部帳戶命名。
   * **[!UICONTROL Type]** : 選擇 **[!UICONTROL Execution instance]** 。
   * 必須勾選「啟用」方塊。
   從類 **[!UICONTROL Connection]** 別：

   * **[!UICONTROL URL]** : 輸入執行例項的URL。
   * **[!UICONTROL Account]** : 輸入用於訪問執行實例的帳戶。
   * **[!UICONTROL Password]** : 輸入用於訪問執行實例的帳戶的密碼。
   從類 **[!UICONTROL Account connection method]** 別：

   * **[!UICONTROL Method]** : 選擇 **[!UICONTROL Federated Data Access (FDA)]** 。
   * **[!UICONTROL FDA account]** : 從下拉式清單中選擇您的FDA帳戶。
   * Click the **[!UICONTROL Create the archiving workflow]** button.
   * 按一下該 **[!UICONTROL Create data synchronization workflow]** 按鈕可建立LINE資料同步工作流。



1. 您現在可以開始建立事務性消息。 For more on this, refer to this [page](../../message-center/using/introduction.md).
