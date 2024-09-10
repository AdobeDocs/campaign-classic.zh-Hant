---
product: campaign
title: 異動訊息傳送架構
description: 本節說明Adobe Campaign Classic異動訊息傳送架構，以及傳送異動訊息的可用通道
feature: Transactional Messaging, Message Center, Architecture
exl-id: 0a059397-b037-405b-b9c1-94a4a072674d
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 1%

---

# 異動訊息傳送架構 {#transactional-messaging-architecture}



異動訊息需仰賴特定架構，而架構是由數個例項組成：

* 建立訊息範本的&#x200B;**控制例項**。

* 一或多個&#x200B;**執行個體**，接收事件並傳遞訊息。

![](assets/messagecenter_diagram.png)

| 控制例項 | 執行執行個體 |
|--- |--- |
| Adobe Campaign使用者登入控制執行個體以： <ul><li>建立異動訊息範本</li><li>使用種子清單產生訊息預覽</li><li>顯示報表</li><li>監視執行個體</li></ul> | 執行例項在此用於： <ul><li>接收事件</li><li>將其連結至異動訊息範本</li><li>傳送個人化訊息給每位收件者</li></ul> |

## 安裝執行個體 {#installing-instances}

安裝異動訊息套件時，有數個預防措施。 Adobe建議您先在測試環境中工作，然後再投入生產。 您也需要相容的Adobe Campaign授權。 如需詳細資訊，請聯絡您的Adobe客戶主管。

>[!IMPORTANT]
>
>控制例項和執行例項必須安裝在不同的電腦上。 他們無法共用相同的Campaign執行個體。

如果您需要使用數個通道，必須先安裝和設定相關套件，才能安裝異動訊息套件。 如需詳細資訊，請參閱[新增傳遞管道](#adding-a-delivery-channel)。

## 控制例項 {#control-instance}

若要在您的電腦上安裝控制項執行個體，請透過&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;功能表選取&#x200B;**[!UICONTROL Transactional message control]**&#x200B;套件。 如需詳細資訊，請參閱[安裝Campaign Classic標準套件](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/messagecenter_install_controlinstance_001.png)

設定控制執行個體的詳細步驟顯示在[本節](../../message-center/using/configuring-instances.md#control-instance)中。

### 支援數個控制例項 {#supporting-several-control-instances}

>[!IMPORTANT]
>
>僅內部部署環境支援與數個控制執行個體共用執行叢集。

可以在多個控制執行個體之間共用執行叢集。 例如，如果您管理數個專門商店，您可以為每個品牌設定一個控制執行個體，並將它們連結至相同的執行叢集。

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>如需必要組態的詳細資訊，請參閱[使用數個控制執行個體](../../message-center/using/configuring-instances.md#using-several-control-instances)。

## 執行執行個體 {#execution-instance}

若要在您的電腦上安裝執行個體，請透過&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;功能表選取&#x200B;**[!UICONTROL Transactional message execution]**&#x200B;套件。 如需詳細資訊，請參閱[安裝Campaign Classic標準套件](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/messagecenter_install_executioninstance_001.png)

設定執行執行個體的詳細步驟顯示在[本節](../../message-center/using/configuring-instances.md#execution-instance)中。

## 可用的傳送管道

電子郵件通道預設為可用。 若要在多個頻道上傳送交易式訊息，您可以新增其他頻道（行動頻道、行動應用程式頻道等）。

>[!IMPORTANT]
>
>新增傳送頻道（行動裝置頻道、行動應用程式頻道等） 必須先執行，才能安裝異動訊息套件。

### 新增傳遞管道 {#adding-a-delivery-channel}

Adobe建議您&#x200B;**在安裝Transactional訊息封裝**&#x200B;之前，一律新增傳遞通道封裝。

不過，如果您已在電子郵件通道上啟動交易式訊息專案，然後在專案期間決定新增通道，您可以依照下列步驟操作。

>[!NOTE]
>
>此程式僅適用於使用安裝在相同電腦上的Windows NLServer的客戶。

1. 使用套件匯入小幫手(**[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]**)安裝您需要的頻道，例如&#x200B;**行動頻道**。
1. 執行檔案匯入(**[!UICONTROL Tools > Advanced > Import package... > File]**)，並選取&#x200B;**datakitnms **`[Your language]`**packagemessageCenter.xml**&#x200B;檔案。
1. 在&#x200B;**[!UICONTROL XML content of the data to import]**&#x200B;中，僅保留對應至新增頻道的傳遞範本。 例如，如果您已新增&#x200B;**行動裝置頻道**，請僅保留與&#x200B;**[!UICONTROL Mobile transactional message]** (smsTriggerMessage)相對應的&#x200B;**entities**&#x200B;元素。 如果您已新增&#x200B;**行動應用程式頻道**，請僅保留&#x200B;**iOS交易式訊息** (iosTriggerMessage)和&#x200B;**Android交易式訊息** (androidTriggerMessage)。

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

與行動應用程式頻道模組結合時，交易式訊息可讓您透過行動裝置上的通知推送交易式訊息。

>[!NOTE]
>
>行動應用程式頻道在[此區段](../../delivery/using/about-mobile-app-channel.md)中有詳細說明。

若要搭配行動應用程式頻道使用異動訊息模組，您必須套用下列設定：

1. 將&#x200B;**行動應用程式通道**&#x200B;套件安裝至控制和執行執行個體。
1. 復寫&#x200B;**行動應用程式**&#x200B;型別Adobe Campaign服務及其包含在執行個體上的行動應用程式。

事件必須包含下列元素：

* 行動裝置ID (Android為&#x200B;**registrationId**，iOS為&#x200B;**deviceToken**)。 此ID代表將傳送通知的「地址」。
* 行動應用程式或整合金鑰的連結(**uuid**)，可讓您復原應用程式的特定連線資訊。
* 通知將傳送至的頻道(**wishedChannel**)： 41適用於iOS，42適用於Android
* 所有對個人化有用的資料

以下是包含此資訊的事件範例：

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation="none" uuid="com.adobe.NeoMiles"/>
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
>訊息範本的建立方式保持不變。

### 異動訊息和LINE {#transactional-messaging-and-line}

交易式訊息與LINE頻道結合，可讓您在消費者行動裝置上安裝的LINE應用程式上傳送即時訊息。 當LINE使用者新增品牌頁面時，此專案會用於傳送歡迎訊息。

若要搭配LINE使用異動訊息模組，您的&#x200B;**行銷**&#x200B;執行個體和&#x200B;**執行**&#x200B;執行個體上的設定需要下列元素：

* 在兩個執行個體上安裝&#x200B;**[!UICONTROL LINE Connect]**&#x200B;套件。
* 在行銷執行個體上安裝&#x200B;**[!UICONTROL Transactional message control]**&#x200B;套件，在執行執行個體上安裝&#x200B;**[!UICONTROL Transactional message execution]**&#x200B;套件。
* 在兩個執行個體上建立具有相同命名的LINE **外部帳戶**&#x200B;和&#x200B;**服務**，以便進行同步處理。 如需如何建立LINE外部帳戶和服務的詳細資訊，請參閱[本節](../../delivery/using/line-channel.md#setting-up-line-channel)。

然後，從&#x200B;**[!UICONTROL Explorer]**，在&#x200B;**[!UICONTROL Platform]** > **[!UICONTROL External account]**&#x200B;中，您需要在兩個執行個體上設定不同的外部帳戶：

1. 使用下列設定，在您的&#x200B;**執行**&#x200B;執行個體中建立&#x200B;**[!UICONTROL External database]**&#x200B;外部帳戶：

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]** ：視需要為外部帳戶命名。
   * **[!UICONTROL Type]** ：選取「**[!UICONTROL External database]**」。
   * 必須核取&#x200B;**[!UICONTROL Enabled]**&#x200B;方塊。

   從&#x200B;**[!UICONTROL Connection]**&#x200B;類別：

   * **[!UICONTROL Type]** ：選取您的資料庫伺服器，例如PostgresSQL。
   * **[!UICONTROL Server]** ：輸入您的資料庫伺服器URL。
   * **[!UICONTROL Account]** ：輸入您的資料庫帳戶。

     >[!NOTE]
     >
     >資料庫使用者需要擁有下列FDA連線表格的讀取許可權：XtkOption、NmsVisitor、NmsVisitorSub、NmsService、NmsBroadLogRtEvent、NmsBroadLogBatchEvent、NmsTrackingLogRtEvent、NmsTrackingLogBatchEvent、NmsRtEvent、NmsBroadLogMsg、 NmsDelivery、NmsWebTrackingLogXtkFolder。

   * **[!UICONTROL Password]** ：輸入資料庫帳戶的密碼。
   * **[!UICONTROL Database]** ：輸入執行個體的資料庫名稱。
   * 必須核取&#x200B;**[!UICONTROL Target of an HTTP relay to remote database's account]**&#x200B;方塊。

1. 使用下列設定，在您的&#x200B;**行銷**&#x200B;執行個體中建立&#x200B;**[!UICONTROL External Database]**&#x200B;帳戶。

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]** ：視需要為外部帳戶命名。
   * **[!UICONTROL Type]** ：選取「**[!UICONTROL External database]**」。
   * 必須勾選「已啟用」方塊。

   從&#x200B;**[!UICONTROL Connection]**&#x200B;類別：

   * **[!UICONTROL Type]** ：選取「**[!UICONTROL HTTP relay to remote Database]**」。
   * **[!UICONTROL Server]** ：輸入您行銷活動的執行例項伺服器URL。
   * **[!UICONTROL Account]** ：輸入用來存取執行個體的帳戶。
   * **[!UICONTROL Password]** ：輸入用來存取執行個體的帳戶密碼。
   * **[!UICONTROL Data Source]** ：在執行執行個體中輸入外部資料庫帳戶的下列語法&#x200B;**`nms:extAccount:ID`**。

1. 使用下列設定，在您的&#x200B;**行銷**&#x200B;執行個體中建立&#x200B;**[!UICONTROL Execution instance]**&#x200B;外部帳戶，以建立資料同步工作流程：

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]** ：視需要為外部帳戶命名。
   * **[!UICONTROL Type]** ：選取「**[!UICONTROL Execution instance]**」。
   * 必須勾選「已啟用」方塊。

   從&#x200B;**[!UICONTROL Connection]**&#x200B;類別：

   * **[!UICONTROL URL]** ：輸入執行個體的URL。
   * **[!UICONTROL Account]** ：輸入用來存取執行個體的帳戶。
   * **[!UICONTROL Password]** ：輸入用來存取執行個體的帳戶密碼。

   從&#x200B;**[!UICONTROL Account connection method]**&#x200B;類別：

   * **[!UICONTROL Method]** ：選取「**[!UICONTROL Federated Data Access (FDA)]**」。
   * **[!UICONTROL FDA account]** ：從下拉式清單中選取您的FDA帳戶。
   * 按一下 **[!UICONTROL Create the archiving workflow]** 按鈕。
   * 按一下&#x200B;**[!UICONTROL Create data synchronization workflow]**&#x200B;按鈕以建立LINE資料同步工作流程。

1. 您現在可以開始[建立交易式訊息](../../message-center/using/creating-the-message-template.md)。
