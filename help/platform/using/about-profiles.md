---
product: campaign
title: 開始使用輪廓
description: 在Adobe Campaign中使用設定檔
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 34%

---

# 開始使用輪廓{#about-profiles}



設定檔會集中於Adobe Campaign資料庫中。 要獲取輪廓，並建立此資料庫，有許多可行的機制：透過網路表單線上收集、手動或自動匯入文字檔、透過公司資料庫或其他資訊系統進行複寫。透過Adobe Campaign，您可以將行銷記錄、購買資訊、偏好設定、CRM資料以及任何相關的PI資料整合在整合檢視中，以進行分析並採取行動。

**設定檔**」是指代表最終客戶、潛在客戶或潛在客戶的資訊記錄（例如：nmsRecipient表格或外部表格中的記錄，包含cookie識別碼、客戶識別碼、行動識別碼或其他與特定管道相關的資訊）。

在 Adobe　Campaign 中，收件者是用於傳送內容 (電子郵件、簡訊等) 的預設輪廓。儲存在資料庫中的收件者資料可讓您篩選將接收任何指定傳遞的目標，並在傳遞內容中新增個人化資料。 資料庫中還存在其他類型的輪廓。這些用戶檔案是針對不同用途設計的。例如，種子輪廓用於在內容傳送給最終目標前測試內容。

![](assets/do-not-localize/how-to-video.png) [瞭解視訊中的設定檔概念](#create-profiles-video)

## 用戶檔案類型 {#profile-types}

使用 Adobe Campaign，您可在用戶檔案的整個生命週期對其進行管理，即建立、匯入、鎖定、活動追蹤、更新等等。

每個設定檔都符合一個資料庫專案。 其中包含鎖定、限定和追蹤個人所需的所有必要資訊。

可以根據儲存空間識別設定檔。 這表示設定檔可以比對：收件者、訪客、運運算元、訂閱者、潛在客戶等。

## 收件者用戶檔案 {#recipient-profiles}

傳遞的收件者會以用戶檔案形式儲存在資料庫中，並包含其所連結的資訊，如姓氏、名字、地址、訂閱、傳遞內容等。當您建立行銷活動時，您可以根據簡易或進階準則從資料庫中選定傳遞的目標客戶。

您也可以針對其設定檔並非儲存在資料庫中，而是儲存在檔案中的收件者，建立行銷活動。 這些稱為「外部」傳遞。 如需此傳遞類型的詳細資訊，請參閱[本頁面](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)。

建立收件者用戶檔案的主要方法如下：

* 在圖形介面畫面中直接輸入，
* 匯入收件者清單，
* 透過網路表單線上收集。

>[!NOTE]
>
>若要瞭解檔案和網頁表單如何匯入，請參閱[一般匯入和匯出](../../platform/using/get-started-data-import-export.md)。

## 用戶檔案和目標 {#profiles-and-targets}

**[!UICONTROL Profiles and targets]**&#x200B;連結可讓您顯示儲存在Adobe Campaign資料庫中的收件者。 您可以建立新收件者、編輯現有收件者並存取其設定檔。 如需詳細資訊，請參閱[此頁面](../../platform/using/editing-a-profile.md)。

![](assets/d_ncs_user_interface_target_link.png)

它也可讓您存取：

* 清單 — [深入瞭解](../../platform/using/creating-and-managing-lists.md)
* 訂閱服務 — [深入瞭解](../../delivery/using/managing-subscriptions.md)
* 網頁應用程式 — [深入瞭解](../../web/using/about-web-applications.md)
* 匯入和匯出（工作） - [瞭解更多](../../platform/using/about-generic-imports-exports.md)
* 目標工作流程 — [瞭解更多](../../workflow/using/building-a-workflow.md#implementation-steps-)

使用收件者頁面，您可以對用戶檔案執行常見的作業，如編輯、更新、新增、刪除、排序。

如需更進階的設定檔操作，您需要編輯Adobe Campaign樹狀結構。 若要這麼做，請按一下Adobe Campaign首頁上的&#x200B;**[!UICONTROL Explorer]**&#x200B;連結。

依預設，收件者會儲存在樹狀結構的&#x200B;**[!UICONTROL Profiles and Targets > Recipients]**&#x200B;節點中。 由此畫面，您可以建立收件者以及以下各項：

* 排序及篩選資料庫的設定檔 — [深入瞭解](../../platform/using/filtering-options.md)
* 從資料庫移動、複製或刪除設定檔 — [深入瞭解](../../platform/using/managing-profiles.md)，
* 更新設定檔 — [深入瞭解](../../platform/using/updating-data.md)
* 匯出收件者 — [深入瞭解](../../platform/using/exporting-and-importing-profiles.md)
* 建立收件者群組 — [深入瞭解](../../platform/using/creating-and-managing-lists.md)

若要存取進階功能與設定，您必須按一下&#x200B;**[!UICONTROL Explorer]**&#x200B;圖示。

![](assets/d_ncs_user_interface01.png)

Adobe Campaign Explorer的一般配置顯示在[此頁面](../../platform/using/adobe-campaign-explorer.md)中。

>[!NOTE]
>
>您也可以按一下&#x200B;**[!UICONTROL Profiles and targets > Recipients]**&#x200B;連結，從Adobe Campaign樹狀結構顯示此清單的進階檢視。 清單顯示可依您的需求進行設定。 您可以新增或刪除欄、定義欄順序、排序資料等。 清單顯示設定在[此頁面](../../platform/using/adobe-campaign-ui-lists.md)中說明。
>
>您也可以定義收件者檢視。 如需有關此功能的進一步資訊，請參閱[此章節](../../platform/using/access-management-folders.md)。

## 活躍輪廓 {#active-profiles}

作用中設定檔是客戶在過去12個月嘗試透過任何通道與之通訊的設定檔。

根據您的合約，您的每個 Campaign 執行個體都已佈建特定數量的活躍輪廓，而且會計算這些輪廓數量以結算費用。請參閱您的最新合約，以參考已購買作用中設定檔數目。 深入瞭解[Adobe Campaign產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}。

您可以直接從Campaign「控制面板」監視執行個體上的作用中設定檔數目。 如需詳細資訊，請參閱[控制面板檔案](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html?lang=zh-Hant){target="_blank"}。

以下護欄和限制在此適用：

* 數個傳送所定位的設定檔只會計算一次。
* 在X (Twitter)或Facebook的社交行銷內容中鎖定的設定檔，不會視為作用中設定檔。
* 作用中設定檔的計數僅適用於&#x200B;**行銷執行個體**。 它不適用於執行例項，亦即MID (mid sourcing)和RT （Message Center/即時傳訊）例項。
* 計數是以收件者主索引鍵為基礎。 因此，如果設定檔存在於兩個不同的收件者表格中，則可將其計算為作用中設定檔兩次。


## 教學課程影片 {#create-profiles-video}

瞭解如何存取輪廓資料、排序和篩選輪廓，以及手動建立和管理輪廓。

此影片也會說明Adobe Campaign Classic是否符合一般資料保護規範。

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

其他 Campaign Classic 作法影片可在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。

**另請參閱**

* 行銷活動中的[隱私權管理](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)

* [在工作流程中建立查詢和區段資料](../../workflow/using/targeting-data.md)

* [選取目標對應](../../delivery/using/steps-defining-the-target-population.md#select-a-target-mapping)
