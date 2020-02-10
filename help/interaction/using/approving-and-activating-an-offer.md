---
title: 核准和啟用選件
seo-title: 核准和啟用選件
description: 核准和啟用選件
seo-description: null
page-status-flag: never-activated
uuid: 1be96bb4-ef17-4b4d-b872-05e1c6b1412d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: 7b1c58a0-6fd6-4c9d-b1c4-f3dffda42523
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# 核准和啟用選件{#approving-and-activating-an-offer}

選件內容完成後，您需要核准，才能將它複製至即時環境並傳遞。 核准涉及選件內容及其資格。

選件控制面板上的橫幅會告訴您選件是否需要經過核准週期。

![](assets/offer_validate_001.png)

## 核准選件內容 {#approving-offer-content}

核准選件內容意味著選取您要在即時環境中提供的呈現方式。

選件的內容每個空間有一個表示法。 由於每個選件空間都有其自己的結構和自己的轉換功能，因此選件表示法可能會有所不同。

您可以選擇在特定可用空間上核准選件內容，並在其他空間上拒絕選件內容。

>[!CAUTION]
>
>在核准選件的內容和資格後，出版工作流程（選件通知）就會自動執行，而且選件會上線，並可在所有啟用的空間中使用。

若要核准選件內容，請套用下列步驟：

1. 按一下按 **[!UICONTROL Approval]** 鈕並在快顯 **[!UICONTROL Approve content]** 視窗中選取。

   ![](assets/offer_validate_002.png)

1. 使用下拉式清單，選取您要繼續編輯的表示法或您要發佈至即時環境的表示法，然後按一下 **[!UICONTROL Content approval]**。

   ![](assets/offer_validate_003.png)

   一旦選件內容獲得核准，資訊就會在選件控制面板表格上更新。

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >提 **[!UICONTROL Content approved]** 及並不表示所有選件說明皆已啟用並核准。 它表示內容核准程式已經完成，不論所有選件皆已啟用／核准。

## 核准優惠資格 {#approving-offer-eligibility}

核准選件資格是指接受或拒絕選件權重，以及選件中設定或繼承自父類別中建立之規則的資格規則。

>[!CAUTION]
>
>在核准選件的內容和資格後，出版工作流程（選件通知）就會自動執行，而且選件會上線，並可在所有啟用的空間中使用。

* 按一下即可檢視規則的完整清單 **[!UICONTROL Schedule and eligibility rules]**。

   ![](assets/offer_validate_005.png)

* 若要變更資格規則，請按一 **[!UICONTROL Reject]**&#x200B;下，然後按一下 **[!UICONTROL Eligibility approval]**。

   ![](assets/offer_validate_007.png)

   選件控制面板會更新各種狀態。

   ![](assets/offer_validate_006.png)

* 若要接受選件資格，請按一下 **[!UICONTROL Approve eligibility]**。

   ![](assets/offer_validate_008.png)

   核准資格、視需要新增意見，然後按一下 **[!UICONTROL Eligibility approval]**。

   ![](assets/offer_validate_009.png)

   選件控制面板會更新各種狀態。

   ![](assets/offer_validate_010.png)

## 核准追蹤 {#approval-tracking}

選件控制面板上提供核准追蹤。 按一 **[!UICONTROL Hide/display logs]** 下以存取它。

![](assets/offer_validate_012.png)

>[!NOTE]
>
>您也可以在選件的標籤 **[!UICONTROL Audit]** 中使用追蹤功能，並提供審核者意見的詳細資訊。

## 重新開始核准 {#restart-the-approval}

一旦啟動核准後，就可以重新啟動。 若要這麼做，請依照下列指示：

1. 按一 **[!UICONTROL Content approved]** 下選件控制面板。
1. 在顯示 **[!UICONTROL Edit]** 的視窗中，選取要重新啟動的核准，然後按一下 **[!UICONTROL Re-initialize approval to submit it again]**。
1. 按一下確認 **[!UICONTROL Ok]**。

![](assets/offer_validate_013.png)

## 發佈選件 {#publishing-the-offer}

一旦某個選件的內容和資格都獲得核准後，該選件就會由工作流程發佈，此工作流程會自動執行每個已完成核准週期的選件。 工作 **[!UICONTROL Offer notification]** 流程也會每小時執行一次，以同步（如有必要）選件目錄中包含的空間和類別，從設計環境到即時環境。

設計環境中可用選件的控制面板包含發佈相關資訊，包括即時環境中相符選件的名稱。

![](assets/offer_golive_001.png)

若要顯示即時環境中可用的選件，請按一下選件標籤：即時選件有一個控制面板，其中包含其所有相關資訊。

![](assets/offer_golive_002.png)

## 停用選件 {#disabling-an-offer}

一旦選件獲得核准，您就可以停用它。

若要這麼做，請前往儀表板取得線上選件或等候上線的選件，然後按一下 **[!UICONTROL Disable offer]**。

您也可以直接停用類別，方法是前往標 **[!UICONTROL Eligibility]** 簽並勾選方 **[!UICONTROL Enabled]** 塊。

>[!NOTE]
>
>當選件在設計環境中刪除時，會在連結的線上環境中自動停用選件。 在提案保留期後，停用的選件會從線上環境中刪除。

![](assets/offer_preview_deactivate.png)

