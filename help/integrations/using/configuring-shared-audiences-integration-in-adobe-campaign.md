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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6ae45cbd87fc0152fc654202e03501fc8d2abd06

---


# 在Adobe Campaign中設定共用觀眾整合{#configuring-shared-audiences-integration-in-adobe-campaign}

在您提交此要求後，Adobe會繼續為您提供整合，並聯絡您以提供您必須完成設定的詳細資訊：

1. [步驟1:設定或檢查Adobe Campaign中的外部帳戶](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [步驟2:設定資料來源](#step-2--configure-the-data-source)
1. [步驟3:設定促銷活動追蹤伺服器](#step-3--configure-campaign-tracking-server)
1. [步驟4:設定訪客ID服務](#step-4--configure-the-visitor-id-service)

## 步驟1:設定或檢查Adobe Campaign中的外部帳戶 {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

首先，我們需要設定或檢查Adobe Campaign中的外部帳戶，如下所示：

1. 按一下 **[!UICONTROL Explorer]** 圖示。
1. 前往 **[!UICONTROL Administration > Platform > External accounts]**。 上述SFTP帳戶應由Adobe設定，且必要的資訊應已傳達給您。

   * **[!UICONTROL importSharedAudience]** :專用於匯入觀眾的SFTP帳戶。
   * **[!UICONTROL exportSharedAudience]** :專用於匯出觀眾的SFTP帳戶。
   ![](assets/aam_config_1.png)

1. 填寫欄 **[!UICONTROL Server]** 位：匯 **入外部帳戶的FTP-out.demdex.com網域和****** 匯出外部帳戶的FTP-in.demdex.com網域。

   請記住，從Campaign匯出是Audience manager或People核心服務的匯入。

   >[!NOTE]
   >
   >如果您使用S3，請輸入以 **[!UICONTROL AWS S3 Account Server]** 下語法：\
   `<S3bucket name>.s3.amazonaws.com/<s3object path>`\
   如需如何設定S3帳戶的詳細資訊，請參閱本 [頁](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account)。

   ![](assets/aam_config_2.png)

1. 新增Adobe **[!UICONTROL Account]** 提 **[!UICONTROL Password]** 供的和。

您的外部帳戶現在已設定。

## 步驟2:設定資料來源 {#step-2--configure-the-data-source}

「收 **件者——訪客ID** 」是在Audience manager中建立。 這是預設為訪客ID設定的現成可用資料來源。 從「促銷活動」建立的區段將是此資料來源的一部分。

要配置數 **[!UICONTROL Recipient - Visitor ID]** 據源：

1. 從節 **[!UICONTROL Explorer]** 點中選擇 **[!UICONTROL Administration > Platform > AMC Data sources]**。
1. Select **[!UICONTROL Recipient - Visitor ID]**.
1. 輸入Adobe **[!UICONTROL Data Source ID]** 提供 **[!UICONTROL AAM Destination ID]** 的和Adobe。

   ![](assets/aam_config_3.png)

## 步驟3:設定促銷活動追蹤伺服器 {#step-3--configure-campaign-tracking-server}

若要設定與People Core服務或Audience Manager的整合，我們還需要設定促銷活動追蹤伺服器。

您必須確定「促銷活動追蹤伺服器」已註冊在網域(CNAME)上。 您可在本文中找到有關網域名稱委派的 [詳細資訊](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)。

## 步驟4:設定訪客ID服務 {#step-4--configure-the-visitor-id-service}

如果您的訪客ID服務從未在您的網站屬性或網站上設定，請參閱下列檔案 [](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-aam-analytics.html) ，以瞭解如何設定您的服務或下列視 [訊](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) 。

您的設定和布建已完成，整合現在可用來匯入和匯出觀眾或區段。
