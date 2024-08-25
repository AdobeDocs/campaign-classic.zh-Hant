---
product: campaign
title: 設定IMS
description: 瞭解如何透過Adobe ID連線
feature: Configuration
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---

# 設定IMS{#configuring-ims}

>[!IMPORTANT]
>
>作為Campaign託管或受管理的服務使用者，您的Adobe IMS實作屬於Adobe。 以下所述的步驟僅適用於內部部署和混合客戶。
> Adobe IMS實作只能由Adobe技術管理員執行。 請聯絡您的Adobe代表，以開始實作程式。

## 先決條件 {#prerequisites}

* 您必須有Adobe Experience Cloud組織名稱和ID。 若要尋找您的組織ID，請參閱[此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-hant){_blank}。
* 您必須在Experience Cloud中新增使用者。 如需詳細資訊，請參閱[此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}。

>[!NOTE]
>
>請確定您的使用者已連結至將與Adobe Campaign同步的Adobe Experience Cloud群組。 [了解更多](#configuring-the-external-account)。

## 更新主控台 {#updating-the-console}

若要使用此功能，您必須安裝最新版本的使用者端主控台。

## 安裝套件 {#installing-the-package}

您必須安裝內建&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;套件。 安裝整合套件和安裝標準套件相同，在[此頁面](../../installation/using/installing-campaign-standard-packages.md)中有詳細說明。

![](assets/ims_6.png)

## 設定外部帳戶 {#configuring-the-external-account}

在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中設定&#x200B;**Adobe Experience Cloud**&#x200B;外部帳戶。

![](assets/ims_5.png)

輸入下列資訊：

* 使用的IMS伺服器的連線資訊（識別碼和密碼）。 此資訊由Adobe客戶服務團隊提供。 如需詳細資訊，請參閱[Adobe Experience Cloud管理員常見問題集](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html)。

  必須在&#x200B;**https**&#x200B;中指定&#x200B;**[!UICONTROL Callback server]**&#x200B;位址。 此欄位對應至Adobe Campaign執行個體的存取URL。

* 組織識別碼：若要尋找您的組織識別碼，請參閱[此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-hant){_blank}。

* 關聯遮罩：此欄位可讓您定義語法，讓Enterprise Dashboard中的組態名稱與Adobe Campaign中的群組同步。 如果您使用語法「Campaign - tenant_id - (.&#42;)」，則在Adobe Campaign中建立的安全性群組將會連結至Enterprise Dashboard中的設定名稱「Campaign - tenant_id - internal_name」。

* Adobe Experience Cloud連線資訊，即Adobe Experience Cloud租使用者的名稱。
