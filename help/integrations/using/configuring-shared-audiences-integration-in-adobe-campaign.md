---
title: 在Adobe Campaign中設定共用觀眾整合
seo-title: 在Adobe Campaign中設定共用觀眾整合
description: 在Adobe Campaign中設定共用觀眾整合
seo-description: null
page-status-flag: never-activated
uuid: 6ed137e4-027f-4eb0-a0b5-4beb7deef51f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 4443b0ca-80c6-467d-a4df-50864aae8496
translation-type: tm+mt
source-git-commit: d567cb7dbc55d9c124d1cc83b7a5a9e2dfb5ab61
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 2%

---


# Configuring shared audiences integration in Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

在您提交此要求後，Adobe會繼續為您提供整合，並聯絡您以提供您必須完成設定的詳細資訊：

1. [步驟1:設定或檢查Adobe Campaign中的外部帳戶](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [步驟2:設定資料來源](#step-2--configure-the-data-source)
1. [步驟3:設定促銷活動追蹤伺服器](#step-3--configure-campaign-tracking-server)
1. [步驟4:設定訪客ID服務](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>如果您使用demdex網域，並遵循 **ftp-out.demdex.com語法來匯入外部帳戶，以及** ftp-in.demdex.com **** 來匯出外部帳戶，則需相應調整實施，並移至Amazon Simple Storage Service(S3)連接器以匯入或匯出資料。 有關如何使用Amazon S3配置外部帳戶的詳細資訊，請參閱本 [節](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)。

## 步驟1:設定或檢查Adobe Campaign中的外部帳戶 {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

首先，我們需要設定或檢查Adobe Campaign中的外部帳戶，如下所示：

1. 按一下 **[!UICONTROL Explorer]** 圖示。
1. 前往 **[!UICONTROL Administration > Platform > External accounts]**。 上述SFTP帳戶應由Adobe設定，且必要的資訊應已傳達給您。

   * **[!UICONTROL importSharedAudience]**:專用於匯入觀眾的帳戶。
   * **[!UICONTROL exportSharedAudience]**:專用於匯出觀眾的帳戶。

   ![](assets/aam_config_1.png)

1. Select the **[!UICONTROL Export audiences to the Adobe Marketing Cloud]** external account.

1. From the **[!UICONTROL Type]** drop-down, select **[!UICONTROL AWS S3]**.

1. 提供下列詳細資訊：

   * **[!UICONTROL AWS S3 Account Server]**
伺服器的URL，應填入如下：

      ```
      <S3bucket name>.s3.amazonaws.com/<s3object path>
      ```

   * **[!UICONTROL AWS access key ID]**
要瞭解在何處查找您的AWS訪問密鑰ID，請參閱本 [頁](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) 。

   * **[!UICONTROL Secret access key to AWS]**
要瞭解在何處找到AWS的秘密訪問密鑰，請參閱本 [頁](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/)。

   * **[!UICONTROL AWS Region]**
要瞭解有關AWS地區的更多資訊，請參閱本 [頁](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)。
   ![](assets/aam_config_2.png)

1. 按一 **[!UICONTROL Save]** 下並設定 **[!UICONTROL Import audiences from the Adobe Marketing Cloud]** 外部帳戶，如上述步驟所述。

您的外部帳戶現在已設定。

## Step 2: Configure the Data Source {#step-2--configure-the-data-source}

「收 **件者——訪客ID** 」是在Audience Manager中建立。 這是預設為訪客ID設定的現成可用資料來源。 從「促銷活動」建立的區段將是此資料來源的一部分。

要配置數 **[!UICONTROL Recipient - Visitor ID]** 據源：

1. From the **[!UICONTROL Explorer]** node, select **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. 選取 **[!UICONTROL Recipient - Visitor ID]**。
1. 輸入Adobe **[!UICONTROL Data Source ID]** 提供 **[!UICONTROL AAM Destination ID]** 的和Adobe。

   ![](assets/aam_config_3.png)

## 步驟3:設定促銷活動追蹤伺服器 {#step-3--configure-campaign-tracking-server}

若要設定與People Core服務或Audience Manager的整合，我們還需要設定促銷活動追蹤伺服器。

您必須確定「促銷活動追蹤伺服器」已註冊在網域(CNAME)上。 您可在本文中找到有關網域名稱委派的 [詳細資訊](https://helpx.adobe.com/tw/campaign/kb/domain-name-delegation.html)。

## 步驟4:設定訪客ID服務 {#step-4--configure-the-visitor-id-service}

如果您的訪客ID服務從未在您的網站屬性或網站上設定，請參閱下列檔案 [](https://docs.adobe.com/content/help/en/id-service/using/implementation/setup-aam-analytics.html) ，以瞭解如何設定您的服務或下列視 [訊](https://helpx.adobe.com/tw/marketing-cloud/how-to/email-marketing.html#step-two) 。

您的設定和布建已完成，整合現在可用來匯入和匯出觀眾或區段。
