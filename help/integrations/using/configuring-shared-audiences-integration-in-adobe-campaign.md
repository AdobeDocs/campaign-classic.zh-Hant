---
product: campaign
title: 在Adobe Campaign中設定共用受眾整合
description: 了解如何設定共用受眾整合
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: a3e26cff-9609-4d91-8976-9213a30c3fd2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 2%

---

# 在Adobe Campaign中設定共用受眾整合{#configuring-shared-audiences-integration-in-adobe-campaign}

![](../../assets/common.svg)

提交此請求後，Adobe將繼續為您布建整合，並聯繫您以提供詳細資訊和資訊，以便您完成配置：

1. [步驟1:在Adobe Campaign中設定或檢查外部帳戶](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [步驟2:設定資料來源](#step-2--configure-the-data-source)
1. [步驟3:設定促銷活動追蹤伺服器](#step-3--configure-campaign-tracking-server)
1. [步驟4:設定訪客ID服務](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>如果您使用Demdex網域，並針對匯入外部帳戶遵循語法&#x200B;**ftp-out.demdex.com**&#x200B;及針對匯出外部帳戶遵循&#x200B;**ftp-in.demdex.com**，則需據此調整實施，並移至Amazon Simple Storage Service(S3)連接器以匯入或匯出資料。 如需如何使用Amazon S3設定外部帳戶的詳細資訊，請參閱此[區段](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)。

## 步驟1:在Adobe Campaign中設定或檢查外部帳戶 {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

首先，我們需要設定或檢查Adobe Campaign中的外部帳戶，如下所示：

1. 按一下&#x200B;**[!UICONTROL Explorer]**&#x200B;圖示。
1. 前往&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。 上述SFTP帳戶應已透過Adobe設定，且必要資訊應已傳送給您。

   * **[!UICONTROL importSharedAudience]**:專用於匯入對象的帳戶。
   * **[!UICONTROL exportSharedAudience]**:專用於匯出對象的帳戶。

   ![](assets/aam_config_1.png)

1. 選擇&#x200B;**[!UICONTROL Export audiences to the Adobe Marketing Cloud]**&#x200B;外部帳戶。

1. 從&#x200B;**[!UICONTROL Type]**&#x200B;下拉式清單中，選取&#x200B;**[!UICONTROL AWS S3]**。

1. 提供下列詳細資訊：

   * **[!UICONTROL AWS S3 Account Server]**
伺服器的URL，應填入如下：

      ```
      <S3bucket name>.s3.amazonaws.com/<s3object path>
      ```

   * **[!UICONTROL AWS access key ID]**
要了解在何處查找您的AWS訪問密鑰ID，請參閱本 [頁](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) 。

   * **[!UICONTROL Secret access key to AWS]**
要了解在何處查找您對AWS的秘密訪問密鑰，請參閱本 [頁](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/)。

   * **[!UICONTROL AWS Region]**
要了解有關AWS地區的更多資訊，請參 [閱本頁](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)。
   ![](assets/aam_config_2.png)

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;並設定&#x200B;**[!UICONTROL Import audiences from the Adobe Marketing Cloud]**&#x200B;外部帳戶，如先前步驟所述。

您的外部帳戶現在已設定完畢。

## 步驟2:設定資料來源 {#step-2--configure-the-data-source}

**Recipient - Visitor ID**&#x200B;是在Audience Manager內建立。 這是預設為訪客ID設定的現成可用資料來源。 從Campaign建立的區段將屬於此資料來源。

配置&#x200B;**[!UICONTROL Recipient - Visitor ID]**&#x200B;資料源：

1. 從&#x200B;**[!UICONTROL Explorer]**&#x200B;節點中，選擇&#x200B;**[!UICONTROL Administration > Platform > AMC Data sources]**。
1. 選取 **[!UICONTROL Recipient - Visitor ID]**。
1. 輸入Adobe提供的&#x200B;**[!UICONTROL Data Source ID]**&#x200B;和&#x200B;**[!UICONTROL AAM Destination ID]**。

   ![](assets/aam_config_3.png)

## 步驟3:設定促銷活動追蹤伺服器 {#step-3--configure-campaign-tracking-server}

若要設定與People核心服務或Audience Manager的整合，我們也需要設定Campaign追蹤伺服器。

您必須確定已在網域(CNAME)上註冊促銷活動追蹤伺服器。 您可以在[本文](https://helpx.adobe.com/tw/campaign/kb/domain-name-delegation.html)中找到有關域名委派的更多資訊。

## 步驟4:設定訪客ID服務 {#step-4--configure-the-visitor-id-service}

如果您的訪客ID服務從未在您的Web屬性或網站上設定，請參閱下列[document](https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-aam-analytics.html)以了解如何設定您的服務或下列[video](https://helpx.adobe.com/tw/marketing-cloud/how-to/email-marketing.html#step-two) 。

您的設定和布建已完成，現在可以使用整合來匯入和匯出對象或區段。
