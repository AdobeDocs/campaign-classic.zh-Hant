---
product: campaign
title: 設定IMS
description: 瞭解如何透過Adobe ID連線
feature: Configuration
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 1%

---

# 設定IMS{#configuring-ims}

>[!IMPORTANT]
>
>作為Campaign託管或受管理的服務使用者，您的Adobe IMS實作屬於Adobe。 以下所述的步驟僅適用於內部部署和混合客戶。
> Adobe IMS實作只能由Adobe技術管理員執行。 請聯絡您的Adobe代表，以開始實作程式。

## 先決條件 {#prerequisites}

* 您必須有Adobe Experience Cloud組織名稱和ID。 若要尋找您的組織ID，請參閱 [此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}.
* 您必須在Experience Cloud中新增使用者。 有關詳細資訊，請參閱 [此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>請確定您的使用者已連結至將與Adobe Campaign同步的Adobe Experience Cloud群組。 [了解更多](#configuring-the-external-account)。

## 更新主控台 {#updating-the-console}

若要使用此功能，您必須安裝最新版本的使用者端主控台。

## 安裝套件 {#installing-the-package}

您必須安裝內建的 **[!UICONTROL Integration with the Adobe Experience Cloud]** 封裝。 安裝整合套件和安裝標準套件相同，詳細資訊請參閱 [此頁面](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## 設定外部帳戶 {#configuring-the-external-account}

設定 **Adobe Experience Cloud** 外部帳戶於 **[!UICONTROL Administration > Platform > External accounts]**.

![](assets/ims_5.png)

輸入下列資訊：

* 使用的IMS伺服器的連線資訊（識別碼和密碼）。 此資訊由Adobe客戶服務團隊提供。 如需詳細資訊，請參閱 [Adobe Experience Cloud管理員常見問題集](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

  此 **[!UICONTROL Callback server]** 地址必須指定於 **https**. 此欄位對應至Adobe Campaign執行個體的存取URL。

* 組織ID：若要尋找您的組織ID，請參閱 [此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}.

* 關聯遮罩：此欄位可讓您定義語法，讓Enterprise Dashboard中的組態名稱與Adobe Campaign中的群組同步。 如果您使用語法「Campaign - tenant_id - (.&#42;)」，則在Adobe Campaign中建立的安全性群組將會連結至Enterprise Dashboard中的設定名稱「Campaign - tenant_id - internal_name」。

* Adobe Experience Cloud連線資訊，即Adobe Experience Cloud租使用者的名稱。
