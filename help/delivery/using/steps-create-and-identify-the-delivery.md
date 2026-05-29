---
product: campaign
title: 建立並識別傳遞
description: 建立並識別傳遞
feature: Channel Configuration
role: User
hide: true
exl-id: 6e37bc14-b1a9-42af-8c28-ae4b5bcaa055
TQID: https://experienceleague.adobe.com/-Vr-ox-BTkhYDI3ccBGML5CCkPGz-rSakyXPhgz1Isg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 277
ht-degree: 35%

---

# 建立並識別傳遞 {#create-and-identify-the-delivery}

## 建立傳遞 {#creating-the-delivery}

您可以透過概觀或&#x200B;**[!UICONTROL Create > Delivery]**&#x200B;功能表建立傳遞。


若要建立傳遞，請按一下傳遞清單上方的&#x200B;**[!UICONTROL Create]**。 當您建立新傳送時，必須指出所使用的傳送通道。 若要這麼做，請從&#x200B;**[!UICONTROL Delivery template]**&#x200B;欄位的下拉式清單中選取適當的傳遞範本。

![](assets/s_ncs_user_wizard_email01_1.png)

系統會為您安裝的每個管道提供預設範本：直接郵件、電子郵件、傳真、電話、行動裝置管道（簡訊）、Facebook、X （先前稱為Twitter）等。

>[!NOTE]
>
>清單中提供的管道取決於您的授權合約。

您可以建立新的傳遞範本，以便預先設定特定參數來符合您的需求。 如需範本的詳細資訊，請參閱[本節](about-templates.md)。

## 識別傳遞 {#identifying-the-delivery}

您需要完成引數以識別傳遞。 操作步驟：

1. 在 **[!UICONTROL Label]** 欄位輸入傳遞的名稱。

   您也可以將傳遞代碼指派給傳遞。 傳遞的名稱及其程式碼會顯示在傳遞清單中，但收件者無法看見。

1. 在&#x200B;**[!UICONTROL Description]**&#x200B;欄位中新增說明。
1. 在相關欄位中選取傳遞性質。 此資訊對於傳遞追蹤很有用：您可以在傳遞清單根據此條件進行篩選，或使用此選擇條件建立查詢。

   ![](assets/s_ncs_user_email_del_nature.png)

1. 按一下&#x200B;**[!UICONTROL Continue]**&#x200B;以確認此資訊並顯示訊息設定視窗。

傳遞內容已就緒，可進行設定。 每個通道都有專屬的傳遞內容定義。 如需詳細資訊，請參閱專用區段。

* [定義電子郵件內容](defining-the-email-content.md)
* [定義簡訊內容](sms-create.md#defining-the-sms-content)
* [定義直接郵件內容](defining-the-direct-mail-content.md)
* [推播通知](about-mobile-app-channel.md)
