---
product: campaign
title: 配置IMS
description: 瞭解如何通過Adobe ID連接
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 4%

---

# 配置IMS{#configuring-ims}

![](../../assets/common.svg)

>[!IMPORTANT]
>
>Adobe IMS實施嚴格保留給Adobe技術管理員。 請與Adobe主管聯繫以啟動實施過程。

## 必要條件 {#prerequisites}

使用與IMS的整合：

* 您必須具有Adobe Experience Cloud組織名稱和ID。 要查找組織ID，請參閱 [此頁](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}。
* 您必須在Experience Cloud中添加用戶。 有關此內容的詳細資訊，請參閱 [此頁](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}。

>[!NOTE]
>
>確保您的用戶已連結到將與Adobe Campaign同步的Adobe Experience Cloud組。 [了解更多資訊](#configuring-the-external-account)。

## 更新控制台 {#updating-the-console}

要使用此功能，必須安裝最新版本的控制台。

## 安裝軟體包 {#installing-the-package}

必須安裝內置 **[!UICONTROL Integration with the Adobe Experience Cloud]** 檔案。 安裝整合軟體包與安裝標準軟體包相同，詳見 [此頁](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/ims_6.png)

## 配置外部帳戶 {#configuring-the-external-account}

配置 **Adobe Experience Cloud** 外部帳戶 **[!UICONTROL Administration > Platform > External accounts]**。

>[!CAUTION]
>
>此配置是為技術管理員保留的。

![](assets/ims_5.png)

輸入以下資訊：

* 使用的IMS伺服器的連接資訊（ID和機密）。 此資訊由Adobe支援提供。 有關詳細資訊，請參閱 [Adobe Experience Cloud管理員常見問題](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html)。

   的 **[!UICONTROL Callback server]** 必須在中指定地址 **htps**。 此欄位與您的Adobe Campaign實例的訪問URL相對應。

* 組織ID:要查找組織ID，請參閱 [此頁](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html){_blank}。
* 關聯掩碼：此欄位允許您定義語法，該語法將允許企業儀表板中的配置名稱與Adobe Campaign的組同步。 如果使用語法「Campaign - tenant_id -(.&#42;)」，在Adobe Campaign建立的安全組將連結到企業控制板中的配置名稱「Campaging - tenant_id - internal_name」。

   >[!CAUTION]
   >
   >關聯掩碼對於通過Adobe ID的連接才能正常工作至關重要。

* Adobe Experience Cloud連接資訊，特別是Adobe Experience Cloud租戶的名稱。
