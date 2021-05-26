---
solution: Campaign Classic
product: campaign
title: 設定IMS
description: 了解如何透過Adobe ID連線
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---

# 配置IMS{#configuring-ims}

>[!IMPORTANT]
>
>AdobeIMS實作嚴格保留給Adobe技術管理員。 請連絡您的Adobe主管，以開始實作程式。

## 必要條件 {#prerequisites}

若要使用與IMS的整合：

* 您必須有Adobe Experience Cloud組織和IMS ID(在您首次連線至Adobe Experience Cloud時提供)。
* 您必須在Experience Cloud中新增使用者。 有關詳細資訊，請參見[此頁面](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html)。

>[!NOTE]
>
>請確定您的使用者已連結至將與Adobe Campaign同步的Adobe Experience Cloud群組。 請參閱[設定外部帳戶](#configuring-the-external-account)。

## 更新控制台{#updating-the-console}

若要使用此功能，您必須安裝最新版本的主控台。

## 安裝軟體包{#installing-the-package}

必須安裝&#x200B;**[!UICONTROL Integration with the Adobe Experience Cloud]**&#x200B;包。 安裝整合套件與安裝標準套件相同，有關詳情請參閱[本頁](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/ims_6.png)

## 配置外部帳戶{#configuring-the-external-account}

在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中配置&#x200B;**Adobe Experience Cloud**&#x200B;外部帳戶。

>[!CAUTION]
>
>此配置是為技術管理員保留的。

![](assets/ims_5.png)

輸入以下資訊：

* 使用的IMS伺服器連線資訊（ID和機密）。 此資訊由Adobe支援提供。 如需詳細資訊，請參閱Adobe Experience Cloud管理員](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html)的[常見問題集。

   必須在&#x200B;**https**&#x200B;中指定&#x200B;**[!UICONTROL Callback server]**&#x200B;地址。 此欄位對應至您Adobe Campaign執行個體的存取URL。

* IMS組織ID:此資訊可在Experience Cloud上取得（在&#x200B;**[!UICONTROL Administration > Experience Cloud Details]**&#x200B;中），並會在您首次連線至Adobe Experience Cloud時提供。
* 關聯掩碼：此欄位可讓您定義語法，以允許將Enterprise Dashboard中的設定名稱同步至Adobe Campaign中的群組。 如果您使用語法「Campaign - tenant_id -(.*)」，則在Adobe Campaign中建立的安全性群組將連結至Enterprise Dashboard中的設定名稱「Campaign - tenant_id - internal_name」。

   >[!CAUTION]
   >
   >關聯遮色片是透過Adobe ID連線才能正常運作的必要條件。

* Adobe Experience Cloud連線資訊，尤其是Adobe Experience Cloud租用戶的名稱。
