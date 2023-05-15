---
product: campaign
title: 發佈行銷活動套件
description: 發佈行銷活動套件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Distributed Marketing
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 2%

---

# 發佈行銷活動套件{#publishing-the-campaign-package}



中央實體運算子會將想要提供的促銷活動發佈至 **[!UICONTROL list of campaign packages]**.

促銷活動套件必須先由中央實體核准，才能在促銷活動套件清單中發佈。 要執行此操作，您可以透過 **[!UICONTROL Approval parameters]** 行銷活動套件中的連結。

## 指派審核者 {#assigning-a-reviewer}

若要選取審核者，請按一下 **[!UICONTROL Approval parameters]** 從促銷活動套件中連結，並從下拉式清單中選擇相關的審核者。

![](assets/s_advuser_mkg_dist_define_valid.png)

然後，您可以按一下 **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

然後會傳送通知訊息給審核者，以確認此促銷活動套件的可用性。 該消息包含通過Web訪問接受或拒絕批准的連結。

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>在組織實體級別，您也可以指定審核者以批准訂單。 有關詳細資訊，請參閱 [組織實體](about-distributed-marketing.md#organizational-entities).

## 添加其他審閱者 {#adding-other-reviewers}

您可以從 **[!UICONTROL Edit...]** 連結，可在促銷活動套件中找到 **[!UICONTROL Approval parameters...]** 標籤。

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## 核准期間 {#approval-periods}

預設情況下，審核者從提交日期起3天即可處理批准。

在「編輯審核者」視窗中，您也可以設定提醒，以便在未核准促銷活動套件時傳送一或多則訊息。 若要這麼做，請按一下 **[!UICONTROL Add reminder]** 連結，然後 **[!UICONTROL Add]** 按鈕。

可在指定日期和/或 **x** 提交日期後的數天。 提醒類型可在提醒表的第一列中配置。 在以下範例中，審核者會在29/01/2014收到上的提醒訊息，亦即在 **[!UICONTROL Date]** 欄，並在核准期結束前（即提交以供核准日期後的兩天）提供第二個提醒。

![](assets/s_advuser_mkg_dist_reminder_planning.png)

定義套件並提交套件以供核准後，執行排程會顯示在 **[!UICONTROL Audit]** 標籤。 它會顯示根據先前設定計算的處理期限，以及所有已設定提醒的日期。

## 透過Adobe Campaign主控台核准 {#approving-via-the-adobe-campaign-console}

如果未指定審核者，或者通知的操作員未批准該包，則 **[!UICONTROL Approve the package]** 按鈕可讓您直接從促銷活動套件進行核准 **[!UICONTROL Dashboard]** 或從套件概觀中取得。

![](assets/s_advuser_mkg_dist_valid_button.png)

核准後，促銷活動會發佈、新增至清單，一旦達到可用日期，當地實體便可使用。 如果在建立促銷活動時指定了本機實體，則會傳送訊息給通知群組中的運算子，讓他們知道促銷活動可用。 如果事先未指定實體，則預設情況下，所有本機實體都可使用促銷活動。 有關詳細資訊，請參閱 [組織實體](about-distributed-marketing.md#organizational-entities).
