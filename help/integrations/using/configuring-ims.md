---
title: 設定IMS
seo-title: 設定IMS
description: 設定IMS
seo-description: null
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 設定IMS{#configuring-ims}

## 必要條件 {#prerequisites}

若要使用與IMS的整合：

* 您必須擁有Adobe Marketing cloud組織和IMS ID（在您首次連線至Adobe Marketing cloud時提供）。
* 您必須在Marketing cloud中新增使用者。 有關此內容的詳細資訊，請參閱本頁： [https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html)。

>[!NOTE]
>
>請確定您的使用者已連結至將與Adobe Campaign同步的Adobe Marketing cloud群組。 請參閱 [設定外部帳戶](#configuring-the-external-account)。

## 更新控制台 {#updating-the-console}

若要使用此功能，您必須安裝最新版本的主控台。

## 安裝軟體包 {#installing-the-package}

您必須安裝此 **[!UICONTROL Integration with the Adobe Experience Cloud]** 套件。 安裝整合套件與安裝標準套件相同，本頁將詳述 [此點](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/ims_6.png)

## 設定外部帳戶 {#configuring-the-external-account}

在中設 **定Adobe Experience cloud外部** 帳戶 **[!UICONTROL Administration > Platform > External accounts]**。

>[!CAUTION]
>
>此配置將保留給技術管理員。

![](assets/ims_5.png)

輸入以下資訊：

* 使用之IMS伺服器的連線資訊（ID和機密）。 這項資訊由Adobe支援提供。 如需詳細資訊，請參閱Adobe Experience cloud管 [理員的常見問答集](https://marketing.adobe.com/resources/help/en_US/mcloud/faq.html)。

   必須 **[!UICONTROL Callback server]** 在https中指定 **地址**。 此欄位對應您Adobe Campaign例項的存取URL。

* IMS組織ID:此資訊可在Experience Cloud(在 **[!UICONTROL Administration > Experience Cloud Details]** )上取得，並在您首次連線至Adobe Experience cloud時提供。
* 關聯遮色片：此欄位可讓您定義語法，讓Enterprise Dashboard中的設定名稱與Adobe Campaign中的群組同步。 如果您使用語法「Campaign - tenant_id -(.*)」，則在Adobe Campaign中建立的安全性群組將會連結至Enterprise Dashboard中的設定名稱「Campaign - tenant_id - internal_name」。

   >[!CAUTION]
   >
   >關聯遮色片是透過Adobe ID進行連線以正確運作的必備工具。

* Adobe Experience cloud連線資訊，尤其是Adobe Experience cloud租用戶的名稱。

