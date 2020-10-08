---
title: Campaign 設定常見問題集
seo-title: 如何設定 Campaign
description: Campaign Classic 常見問題集
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 100%

---


# Campaign 設定常見問題集 {#settings-faq}

了解主要設定，以設定符合您需求的 Campaign 實例。

## 我可以變更 Campaign 介面的語言嗎？{#can-i-change-the-language-of-campaign-interface-}

在建立實例時可以選取 Campaign 語言。之後您將無法進行變更。如需詳細資訊，請參閱[本章節](../../installation/using/creating-an-instance-and-logging-on.md)。

Adobe Campaign 目前提供英文、法文、德文和日文供 4 種語言的使用者介面。請注意，用戶端主控台和伺服器必須設定相同的語言。每個 Campaign 實例只能選取一種語言。

如果是英文，在安裝 Campaign 時，您可以選取美式英文或英式英文：它們的日期和時間格式有所不同。如需這些差異的詳細資訊，請參閱[本小節](../../platform/using/adobe-campaign-workspace.md#date-and-time)。

## 我可以將 Campaign Classic 搭配其他 Adobe 解決方案結合使用嗎？{#can-i-use-campaign-classic-with-other-adobe-solutions-}

您可以將 Adobe Campaign 的傳遞功能和進階行銷活動管理功能與協助您個人化使用者體驗的解決方案結合使用。

按一下這裡了解[如何使用其他 Adobe 解決方案](../../integrations/using/about-campaign-integrations.md)以及[如何在 Campaign 中設定 IMS](../../integrations/using/about-adobe-id.md)。

## 如何在 Campaign 執行個體設定追蹤功能？{#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

身為資深使用者，您可以在 Campaign 實例上設定追蹤功能。

[按一下這裡以了解更多資訊](../../installation/using/deploying-an-instance.md#tracking-configuration)。

## 如何設定電子郵件傳遞機制? {#how-to-configure-email-deliverability-}

除了「[傳遞能力設定](../../delivery/using/about-deliverability.md#configuration)」章節，請閱讀傳遞能力技術建議，以瞭解如何設定執行個體，以充份發揮 Campaign 傳遞功能。

[按一下這裡以了解更多資訊](../../delivery/using/technical-recommendations.md)。

## 如何實作內容核准？{#how-can-i-implement-content-approval-}

Campaign 可以讓您以協作模式，針對行銷活動的主要步驟設定核准流程。您可以針對每個行銷活動，核准傳遞目標、內容和成本。可以以電子郵件的形式通知負責核准的 Adobe Campaign 操作者，然後他們可透過主控台或網路連線核准或拒絕核准。

[按一下這裡了解更多資訊](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)，並探索在 Campaign 中實作傳遞內容核准的步驟。

## 如何存取儲存在外部資料庫的資料？{#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign 提供同盟資料存取 (FDA) 選項，以處理儲存在一或多個外部資料庫中的資訊：您不需要變更 Adobe Campaign 資料的結構就可以存取外部資料。

[按一下這裡以了解更多資訊](../../platform/using/connecting-to-database.md)。

## 我可以將 Campaign 連線到哪些外部資料庫？{#which-external-databases-can-i-connect-campaign-to-}

[相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)中列有透過同盟資料存取 (FDA) 與 Campaign 相容的外部資料庫。

## Adobe Campaign 可以與輕型目錄存取協定 (LDAP) 整合嗎？{#can-adobe-campaign-integrate-with-ldap-}

身為內部部署/混合部署客戶，您可以將 Campaign Classic 與 LDAP 目錄整合。

[按一下這裡以了解如何操作](../../installation/using/connecting-through-ldap.md)。

## 如何在 Campaign 設定 CRM 連接器？{#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign 提供各種 CRM 連接器，用於將您的 Adobe Campaign 平台連結至您的第三方系統。透過這些 CRM 連接器，您可同步處理連絡人、帳戶、購買等。有了這些 CRM 連接器，您可以將您的應用程式與各協力廠商和商務應用程式輕鬆整合。

透過這些連接器，可快速且輕鬆地整合資料：Adobe Campaign 提供專用的精靈，用於從 CRM 中提供的表格進行收集和選取。並且可確保雙向同步處理，讓整個系統中的資料隨時保持最新。

閱讀[設定 CRM 連接器](../../platform/using/crm-connectors.md)以了解如何將 CRM 工具與 Adobe Campaign 同步。觀看有關 [Adobe Campaign 和 Microsoft Dynamics 365 整合](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html)的使用案例短片。

## 如果是特定於電腦的問題或特定於使用者的問題時，如何執行軟快取清除？{#perform-soft-cache-clear}

如果您有新商標正確反映的問題，需要成功匯出特定於電腦/使用者的資料，則可能需要運用 Windows (Windows 7、Windows XP、Windows 10) 執行軟快取清除。

登入後，請前往 **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**。接著，請登出並重新登入。

![](assets/faq_soft_cache.png)

如果仍沒有幫助效，請嘗試透過下列步驟來清除硬快取。

## 如果是特定於電腦的問題或特定於使用者的問題時，如何執行硬快取清除？{#perform-hard-cache-clear}

如果您有新商標正確反映的問題，需要成功匯出特定於電腦/使用者的資料，則可能需要運用 Windows (Windows 7、Windows XP、Windows 10) 執行硬快取清除。

1. 請在用戶端主控台，選擇 **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**。

1. 登出並關閉客戶端主控台 (rich client)。

1. 依據您的作業系統版本，前往下列位置：

   * Windows 7：C:\Users\&lt; Username >\AppData\Roaming\Neolane\NL_5\
   * Windows XP：C:\Documents and Settings\&lt; Username >\Application Data\Neolane\NL_5

   在這裡，您會看到許多名稱為 nlclient-config-&lt; alphanumerical value >.xml 的 xml 檔案。

1. 刪除這些 xml 檔案和關聯的資料夾。

   >[!IMPORTANT]
   >
   >請勿刪除 nlclient_cnx.xml 檔案。

1. 登入用戶端主控台。