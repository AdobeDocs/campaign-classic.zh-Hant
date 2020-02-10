---
title: 發佈促銷活動套件
seo-title: 發佈促銷活動套件
description: 發佈促銷活動套件
seo-description: null
page-status-flag: never-activated
uuid: f2d35a8d-191f-4c53-8682-7ccce2a94257
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 8653d4fc-e47f-451a-95f2-c9209a252664
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# 發佈促銷活動套件{#publishing-the-campaign-package}

中央實體運算子會將想要提供的促銷活動發佈至中的本機實體 **[!UICONTROL list of campaign packages]**。

在促銷活動套件清單中發佈之前，促銷活動套件必須經過中央實體的核准。 若要這麼做，您可以透過促銷活動套件中的連結，指定審核者 **[!UICONTROL Approval parameters]** 或審核者群組。

## 指派審核者 {#assigning-a-reviewer}

若要選擇審核者，請按一 **[!UICONTROL Approval parameters]** 下促銷活動套件中的連結，然後從下拉式清單中選擇相關的審核者。

![](assets/s_advuser_mkg_dist_define_valid.png)

然後，您可以按一下，開始核准程式 **[!UICONTROL Submit for approval]**。

![](assets/s_advuser_mkg_dist_valid_process.png)

然後會傳送通知訊息給審核者，以確認此促銷活動套件的可用性。 訊息包含透過Web存取接受或拒絕核准的連結。

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>在組織實體層級，您也可以指定審核者來核准訂單。 For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## 新增其他審核者 {#adding-other-reviewers}

您可以從促銷活動套件 **[!UICONTROL Edit...]** 標籤中的連結新增其他審核 **[!UICONTROL Approval parameters...]** 者。

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## 核准期間 {#approval-periods}

依預設，審核者會在提交日期起3天內接受審核，以處理核准。

在「編輯審核者」視窗中，您也可以設定提醒，在未核准促銷活動套件時傳送一或多則訊息。 若要這麼做，請按一下 **[!UICONTROL Add reminder]** 連結，然後按一 **[!UICONTROL Add]** 下按鈕。

提醒可在提交日期後的指定日期和／或 **x天** ，發出。 提醒類型可在提醒表的第一欄中設定。 在以下範例中，審核者將在2014年29月1日收到提醒訊息，即在欄中選取日期的前兩天，以及在核准期間結束前的一天（即提交核准日期後的兩天）收到第二個提醒。 **[!UICONTROL Date]**

![](assets/s_advuser_mkg_dist_reminder_planning.png)

在定義包並提交包以供批准後，執行調度將顯示在頁籤 **[!UICONTROL Audit]** 中。 它會顯示根據先前設定計算的處理期限，以及所有已設定提醒的日期。

## 透過Adobe Campaign主控台核准 {#approving-via-the-adobe-campaign-console}

如果未指定審核者，或通知的運算子未核准套件，則按 **[!UICONTROL Approve the package]** 鈕可讓您直接從促銷活動套件或套件 **[!UICONTROL Dashboard]** 概觀進行核准。

![](assets/s_advuser_mkg_dist_valid_button.png)

核准後，促銷活動會發佈、新增至清單，當達到可用日期時，本機實體即可使用。 如果在建立促銷活動時指定了本機實體，則會傳送訊息給通知群組中的運算子，讓他們知道促銷活動可用。 如果事先未指定實體，則依預設，促銷活動可供所有本機實體使用。 For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).
