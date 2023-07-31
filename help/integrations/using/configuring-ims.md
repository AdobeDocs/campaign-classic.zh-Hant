---
product: campaign
title: 設定IMS
description: 瞭解如何透過Adobe ID連線
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 5%

---

# 設定IMS{#configuring-ims}



>[!IMPORTANT]
>
>Adobe IMS實施作業必須嚴格保留給Adobe技術管理員。 請聯絡您的Adobe主管，以開始實作程式。

## 必要條件 {#prerequisites}

若要使用與IMS的整合：

* 您必須有Adobe Experience Cloud組織名稱和ID。 若要尋找您的組織ID，請參閱 [此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}.
* 您必須在Experience Cloud中新增使用者。 有關詳細資訊，請參閱 [此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>請確定您的使用者已連結至將與Adobe Campaign同步的Adobe Experience Cloud群組。 [了解更多](#configuring-the-external-account)。

## 更新主控台 {#updating-the-console}

若要使用此功能，您必須安裝最新版本的主控台。

## 安裝套件 {#installing-the-package}

您必須安裝內建的 **[!UICONTROL Integration with the Adobe Experience Cloud]** 封裝。 安裝整合套件和安裝標準套件相同，詳細資訊請參閱 [此頁面](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## 設定外部帳戶 {#configuring-the-external-account}

設定 **Adobe Experience Cloud** 外部帳戶於 **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>此設定已保留給技術管理員。

![](assets/ims_5.png)

輸入下列資訊：

* 使用的IMS伺服器的連線資訊（識別碼和密碼）。 此資訊由Adobe支援提供。 如需詳細資訊，請參閱 [Adobe Experience Cloud管理員常見問題集](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

  此 **[!UICONTROL Callback server]** 地址必須指定於 **https**. 此欄位對應至Adobe Campaign執行個體的存取URL。

* 組織ID：若要尋找您的組織ID，請參閱 [此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}.
* 關聯遮罩：此欄位可讓您定義語法，讓Enterprise Dashboard中的組態名稱與Adobe Campaign中的群組同步。 如果您使用語法「Campaign - tenant_id - (.&#42;)」，則在Adobe Campaign中建立的安全性群組將會連結至Enterprise Dashboard中的設定名稱「Campaign - tenant_id - internal_name」。

  >[!CAUTION]
  >
  >關聯遮罩是透過Adobe ID連線正常運作的關鍵。

* Adobe Experience Cloud連線資訊，尤其是Adobe Experience Cloud租使用者的名稱。
