---
product: campaign
title: 發佈行銷活動套件
description: 發佈行銷活動套件
feature: Distributed Marketing
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 2%

---

# 發佈行銷活動套件{#publishing-the-campaign-package}



中央實體運運算元發佈他們想要提供給&#x200B;**[!UICONTROL list of campaign packages]**&#x200B;中本機實體的行銷活動。

在行銷活動套件清單中發佈行銷活動套件之前，必須先由中央實體核准行銷活動套件。 若要這麼做，您可以透過行銷活動套件中的&#x200B;**[!UICONTROL Approval parameters]**&#x200B;連結來指定稽核者或稽核者群組。

## 指派檢閱者 {#assigning-a-reviewer}

若要選取稽核者，請按一下行銷活動套件中的&#x200B;**[!UICONTROL Approval parameters]**&#x200B;連結，然後從下拉式清單中選擇相關的稽核者。

![](assets/s_advuser_mkg_dist_define_valid.png)

接著，您可以按一下&#x200B;**[!UICONTROL Submit for approval]**&#x200B;開始核准程式。

![](assets/s_advuser_mkg_dist_valid_process.png)

然後會傳送通知訊息給檢閱者，以確認此行銷活動套件的可用性。 該訊息包含透過網頁存取接受或拒絕核准的連結。

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>在組織實體層級，您也可以指定稽核者來核准訂單。 如需詳細資訊，請參閱[組織實體](about-distributed-marketing.md#organizational-entities)。

## 新增其他檢閱者 {#adding-other-reviewers}

您可以從行銷活動套件&#x200B;**[!UICONTROL Approval parameters...]**&#x200B;索引標籤中的&#x200B;**[!UICONTROL Edit...]**&#x200B;連結新增其他稽核者。

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## 核准期間 {#approval-periods}

依預設，稽核者可在提交日期起的三天內處理核准。

在編輯稽核者視窗中，您也可以設定提醒，以在行銷活動套件未核準時傳送一或多個訊息。 若要這麼做，請按一下&#x200B;**[!UICONTROL Add reminder]**&#x200B;連結，然後按&#x200B;**[!UICONTROL Add]**&#x200B;按鈕。

可以在指定日期和/或在提交日期後&#x200B;**x**&#x200B;天寄出提醒。 可以在提醒表的第一欄中設定提醒型別。 在以下範例中，稽核者將在2014年1月29日（即&#x200B;**[!UICONTROL Date]**&#x200B;欄中選取的日期前兩天）收到提醒訊息，並在核准期結束前一天（即提交核准日期後兩天）收到第二次提醒。

![](assets/s_advuser_mkg_dist_reminder_planning.png)

定義封裝且封裝已提交核准後，執行排程會顯示在&#x200B;**[!UICONTROL Audit]**&#x200B;索引標籤中。 它會顯示根據先前設定計算出的處理截止日期，以及所有已設定提醒的日期。

## 透過Adobe Campaign主控台核准 {#approving-via-the-adobe-campaign-console}

如果未指定稽核者或通知的操作者皆未核准封裝，則&#x200B;**[!UICONTROL Approve the package]**&#x200B;按鈕可讓您直接從行銷活動封裝&#x200B;**[!UICONTROL Dashboard]**&#x200B;或封裝概述進行核准。

![](assets/s_advuser_mkg_dist_valid_button.png)

核准後，行銷活動會發佈、新增到清單中，並在達到可用日期後立即供本地實體使用。 如果在建立行銷活動時指定了本機實體，則會傳送訊息給通知群組中的操作員，讓他們知道行銷活動可用。 如果預先未指定實體，則所有本機實體預設都可使用促銷活動。 如需詳細資訊，請參閱[組織實體](about-distributed-marketing.md#organizational-entities)。
