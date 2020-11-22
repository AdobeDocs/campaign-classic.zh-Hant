---
solution: Campaign Classic
product: campaign
title: 關於設定檔
description: 關於設定檔
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 63%

---


# 關於設定檔{#about-profiles}

用戶檔案 (客戶、潛在客戶、新聞訂閱者等) 將匯集於 Adobe Campaign 資料庫中。要獲取用戶檔案，並建立此資料庫，有許多可行的機制：透過網路表單線上收集、手動或自動匯入文字檔、透過公司資料庫或其他資訊系統進行複寫。有了Adobe Campaign，您可以將行銷記錄、購買資訊、偏好設定、CRM資料和任何相關PI資料整合在整合的檢視中，以進行分析並採取行動。

在 Adobe　Campaign 中，收件者是用於傳送內容 (電子郵件、SMS 等) 的預設用戶檔案。有了資料庫中儲存的收件者資料，您能夠對接收任何給定內容的收件者進行篩選，並在交付內容中新增個人化資料。資料庫中還存在其他類型的用戶檔案。這些用戶檔案是針對不同用途設計的。例如，種子用戶檔案用於在內容傳送給最終目標前測試內容。

![](assets/do-not-localize/how-to-video.png) [瞭解視訊中描述檔的概念](#create-profiles-video)

## 用戶檔案類型 {#profile-types}

使用 Adobe Campaign，您可在用戶檔案的整個生命週期對其進行管理，即建立、匯入、鎖定、活動追蹤、更新等等。

每個用戶檔案都對應一個資料庫條目。其中包含鎖定、限定和追蹤個人所需的所有必要資訊。

用戶檔案可以根據儲存空間來識別。這表示用戶檔案可以分為收件者、訪客、操作者、訂閱者以及潛在客戶用戶檔案等。

## 收件者用戶檔案 {#recipient-profiles}

傳遞的收件者會以用戶檔案形式儲存在資料庫中，並包含其所連結的資訊，如姓氏、名字、地址、訂閱、傳遞內容等。當您建立行銷活動時，您可以根據簡易或進階準則從資料庫中選定傳遞的目標客戶。

您也可以針對用戶檔案儲存於資料庫以外的其他檔案中的收件者建立行銷活動。這些被稱為「外部」傳遞。如需此傳遞類型的詳細資訊，請參閱[本頁面](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)。

建立收件者用戶檔案的主要方法如下：

* 在圖形介面畫面中直接輸入，
* 匯入收件者清單，
* 透過網路表單線上收集。

>[!NOTE]
>
>To find out how files and web forms are imported, refer to [Generic imports and exports](../../platform/using/generic-imports-and-exports.md).

## 用戶檔案和目標 {#profiles-and-targets}

The **[!UICONTROL Profiles and targets]** link lets you display recipients stored in Adobe Campaign database. 您可以新建收件者、編輯現有的收件者以及存取其用戶檔案。有關詳細資訊，請參見[此頁面](../../platform/using/editing-a-profile.md)。

![](assets/d_ncs_user_interface_target_link.png)

它也可讓您存取：

* 清單；請參 [閱建立和管理清單](../../platform/using/creating-and-managing-lists.md),
* 訂閱服務，請參閱[本頁面](../../delivery/using/managing-subscriptions.md)
* 網路應用程式，請參閱[本頁面](../../web/using/about-web-applications.md)
* 進出口（就業）;請參閱 [一般匯入和匯出](../../platform/using/generic-imports-and-exports.md),
* 鎖定工作流程，請參閱[本頁面](../../workflow/using/building-a-workflow.md#implementation-steps-)

使用收件者頁面，您可以對用戶檔案執行常見的作業，如編輯、更新、新增、刪除、排序。

如需更多用戶檔案進階操作，您需要編輯 Adobe Campaign 樹狀結構清單。若要執行此項操作，請按一下 Adobe Campaign 首頁上的 **[!UICONTROL Explorer]** 連結。

By default, recipients are stored in the **[!UICONTROL Profiles and Targets > Recipients]** node of the tree. 由此畫面，您可以建立收件者以及以下各項：

* sort and filter the profiles of the database; see [Filtering options](../../platform/using/filtering-options.md),
* move, copy or delete profiles from the database; see [Managing profiles](../../platform/using/managing-profiles.md),
* 更新設定檔；請參閱 [更新資料](../../platform/using/updating-data.md),
* 匯出收件者；請參 [閱導出和導入配置檔案](../../platform/using/exporting-and-importing-profiles.md),
* 建立收件者群組；請參 [閱建立和管理清單](../../platform/using/creating-and-managing-lists.md)。

若要存取進階功能和設定，您必須按一下 **[!UICONTROL Explorer]** 圖示。

![](assets/d_ncs_user_interface01.png)

「使用Adobe Campaign檔案總管」中會顯示Adobe Campaign檔案總 [管的一般版面](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer)。

>[!NOTE]
>
>您也可以按一下 **[!UICONTROL Profiles and targets > Recipients]** 連結，從 Adobe Campaign 樹狀結構清單中顯示這份清單的進階檢視。您可根據您的需求設定清單的顯示。您可以新增或刪除欄、定義欄順序、排序資料等。 「使用Adobe Campaign檔案總管」中 [說明清單顯示設定](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer)。
>
>您也可以定義收件者畫面。有關此功能的詳細資訊，請參 [閱資料夾和視圖](../../platform/using/access-management.md#folders-and-views)。

## 使用中的設定檔案 {#active-profiles}

有效用戶檔案指的是可計費開立帳單的用戶檔案。

>[!NOTE]
>
>如果您是在AWS上代管，並使用Campaign Classic建置8931，您也可以直接從控制面板監控實例上使用的活動配置檔案數。 For more on this, refer to the [Control Panel documentation](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/active-profiles-monitoring.html).
>
>請注意，「作用中」描述檔計數僅適 **用於Marketing例項** 。 它不適用於執行實例，即MID（中間採購）和RT（消息中心／即時消息）實例。

**Profile** 是指一筆代表終端客戶或潛在客戶之資訊的紀錄 (例如：nmsRecipient 表格或外部表格中的記錄，包含 cookie 識別碼、客戶識別碼、行動識別碼或特定通路相關的其他資訊)。

計費帳單僅會考慮&#x200B;**有效** 的用戶檔案。如果在過去 12 個月透過任何通路鎖定過用戶檔案或與其進行過通訊，那麼則該用戶檔案被視為有效。

在傳遞準備期間 (類型規則，隔離) 被排除的用戶檔案不包含在內。被多個傳遞項目鎖定的用戶檔案將只計算一次。

>[!NOTE]
>
>Facebook 和 Twitter 通路不包含在內。

您可從「促銷活動標準」功 **[!UICONTROL Number of active profiles]** 能表取得 **[!UICONTROL Administration > Campaign Management > Customer metrics]** 概觀。 The actual count is performed by the **[!UICONTROL Number of active billing profiles]** (**[!UICONTROL billingActiveContactCount]**) [technical workflow](../../workflow/using/deliveries.md), which runs every day and adds the new data to the existing report for the current period in the **[!UICONTROL Customer metrics]** menu. 每個期間均為 12 個月。

## 如何建立和管理個人檔案 {#create-profiles-video}

了解如何存取設定檔資料、排序和篩選設定檔，以及手動建立和管理設定檔。

此影片也說明Adobe Campaign Classic與一般資料保護法規的相容性。

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

**另請參閱**

* [Campaign中的隱私權管理](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)

* [定義目標人口](../../delivery/using/define-the-right-audience.md)

* [在工作流程中建立查詢和區段資料](../../workflow/using/targeting-data.md)

* [選擇目標映射](../../delivery/using/selecting-a-target-mapping.md)

* [定義受眾——最佳實務](../../delivery/using/define-the-right-audience.md)
