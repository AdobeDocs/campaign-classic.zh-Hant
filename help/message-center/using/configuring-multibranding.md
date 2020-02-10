---
title: 設定多品牌
seo-title: 設定多品牌
description: 設定多品牌
seo-description: null
page-status-flag: never-activated
uuid: 61b4235c-da03-4da8-b14b-7ffb12c8d4c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 907d82c8-9262-4952-b8df-21144dd55824
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5eac80743d4cc82cdf55aa9287e8bb4fcc84356

---


# 設定多品牌{#configuring-multibranding}

本節說明一個解決方案，可針對Adobe Campaign中的交易訊息，設定每個品牌的追蹤和鏡像頁面URL。

## 必要條件 {#prerequisites}

* 所有主機都必須添加到實例(`config-<instance>.xml`)的配置檔案中。
* 每個品牌都必須指派一個子網域。
* 如果在HTTPS頁面上進行網頁追蹤，您必須擁有所有品牌的HTTPS憑證。

## 典型過程 {#typical-process}

若要設定多品牌，您必須同時設定執行例項和控制例項。 在執行例項中，請遵循下列步驟：

1. 為每個品牌建立一個外部帳戶。

   >[!NOTE]
   >
   >建立執行實例類型外部帳戶顯示在「控制實例 [」部分](../../message-center/using/creating-a-shared-connection.md#control-instance) 。

1. 擴充nms:extAccount架構以新增追蹤URL:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >擴展現有模式在擴展模式部 [分中顯示](../../configuration/using/extending-a-schema.md) 。

1. 修改nms:extAccount表單：

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. 修改NmsTracking_OpenFormula和NmsTracking_ClickFormula選項，以使用外部帳戶，而非全域選項。

   若要這麼做，請取代：

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   with:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!CAUTION]
   >
   >這些變更在升級時可能會產生衝突。 您可能需要手動合併這些公式及其新版本。

在控制例項上，您需要連結傳送範本和外部帳戶。 若要這麼做，您必須：

1. 使用步驟1中定義的相同內部名稱，為每個品牌建立一個外部帳戶。
1. 為每個品牌建立一個預設傳送範本。
1. 在交貨模板的 **[!UICONTROL Properties]** 中，將工藝路線設定為品牌的外部帳戶。

