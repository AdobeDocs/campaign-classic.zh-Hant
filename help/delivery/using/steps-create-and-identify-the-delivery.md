---
product: campaign
title: 建立並識別傳遞
description: 建立並識別傳遞
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Channel Configuration
role: User
exl-id: 6e37bc14-b1a9-42af-8c28-ae4b5bcaa055
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 5%

---

# 建立並識別傳遞 {#create-and-identify-the-delivery}

## 建立傳遞 {#creating-the-delivery}

您可以透過概覽或透過以下方式建立傳遞： **[!UICONTROL Create > Delivery]** 功能表。


若要建立傳遞，請按一下 **[!UICONTROL Create]** 在傳遞清單上方。 當您建立新傳送時，必須指出所使用的傳送通道。 若要這麼做，請從的下拉式清單中選取適當的傳遞範本 **[!UICONTROL Delivery template]** 欄位。

![](assets/s_ncs_user_wizard_email01_1.png)

系統會為您安裝的每個管道提供預設範本：直接郵件、電子郵件、傳真、電話、行動管道（簡訊）、Facebook、Twitter等。

>[!NOTE]
>
>清單中提供的管道取決於您的授權合約。

您可以建立新的傳遞範本，以預先設定特定引數以符合您的需求。 有關範本的詳細資訊，請參閱 [本節](about-templates.md).

## 識別傳遞 {#identifying-the-delivery}

您需要完成引數以識別傳遞。 操作步驟：

1. 在中輸入傳遞的名稱 **[!UICONTROL Label]** 欄位。

   您也可以將傳遞代碼指派給傳遞。 傳遞的名稱及其程式碼會顯示在傳遞清單中，但收件者無法看見。

1. 在中新增說明 **[!UICONTROL Description]** 欄位。
1. 在相關欄位中選取傳遞性質。 此資訊對於傳送追蹤很有用：您可以在傳送清單中根據此條件進行篩選，或使用此選擇條件建立查詢。

   ![](assets/s_ncs_user_email_del_nature.png)

1. 按一下 **[!UICONTROL Continue]** 以確認此資訊並顯示訊息組態視窗。

傳遞內容已準備好進行設定。 每個管道都有專屬的傳遞內容定義。 如需詳細資訊，請參閱專屬區段：

* [定義電子郵件內容](defining-the-email-content.md)
* [定義簡訊內容](sms-create.md#defining-the-sms-content)
* [定義直接郵件內容](defining-the-direct-mail-content.md)
* [推播通知](about-mobile-app-channel.md)
