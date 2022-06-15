---
product: campaign
title: 發佈行銷活動套件
description: 發佈行銷活動套件
feature: Distributed Marketing
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
source-git-commit: d36e1881726af6238c4e0caecb7b299b594691f2
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 2%

---

# 發佈行銷活動套件{#publishing-the-campaign-package}

![](../../assets/common.svg)

中央實體運營商將發佈希望向中 **[!UICONTROL list of campaign packages]**。

在市場活動包清單中發佈它們之前，市場活動包必須經中央實體批准。 為此，可通過 **[!UICONTROL Approval parameters]** 連結。

## 分配審閱者 {#assigning-a-reviewer}

要選擇審閱者，請按一下 **[!UICONTROL Approval parameters]** 連結到市場活動包，然後從下拉清單中選擇相關的審閱者。

![](assets/s_advuser_mkg_dist_define_valid.png)

然後，您可以通過按一下 **[!UICONTROL Submit for approval]**。

![](assets/s_advuser_mkg_dist_valid_process.png)

然後，通知消息將發送到審閱者以確認此市場活動包的可用性。 該消息包含通過Web訪問接受或拒絕批准的連結。

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>在組織實體層，您還可以指定審核者以批准訂單。 有關此內容的詳細資訊，請參閱 [組織實體](about-distributed-marketing.md#organizational-entities)。

## 添加其他審閱者 {#adding-other-reviewers}

可以從 **[!UICONTROL Edit...]** 連結，在活動包中 **[!UICONTROL Approval parameters...]** 頁籤。

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## 審批期 {#approval-periods}

預設情況下，審核者將從提交日期起3天處理審批。

在「編輯審閱者」窗口中，您還可以設定提醒，以在市場活動包未獲批准時發送一個或多個消息。 要執行此操作，請按一下 **[!UICONTROL Add reminder]** 連結，然後 **[!UICONTROL Add]** 按鈕

可在給定日期和/或 **x** 日期後的幾天。 提醒類型可以在提醒表的第一列中配置。 在下面的示例中，審閱者將在29/01/2014上收到一條提醒消息，即在 **[!UICONTROL Date]** 的日期，即提交審批日期後的兩天。

![](assets/s_advuser_mkg_dist_reminder_planning.png)

一旦定義了該程式包並且已提交該程式包以供審批，則執行計畫將顯示在 **[!UICONTROL Audit]** 頁籤。 它顯示根據先前配置計算的處理截止時間以及所有已配置提醒的日期。

## 通過Adobe Campaign控制台批准 {#approving-via-the-adobe-campaign-console}

如果未指定審核者，或已通知的操作員未批准包，則 **[!UICONTROL Approve the package]** 按鈕，您可以直接從市場活動包中進行審批 **[!UICONTROL Dashboard]** 或從包概述中。

![](assets/s_advuser_mkg_dist_valid_button.png)

批准後，將發佈市場活動，將其添加到清單中，並在達到其可用日期後，本地實體可以使用該市場活動。 如果在建立市場活動時指定了本地實體，則會向通知組中的操作員發送一條消息，讓他們知道市場活動可用。 如果事先沒有指定實體，則預設情況下，市場活動可供所有本地實體使用。 有關此內容的詳細資訊，請參閱 [組織實體](about-distributed-marketing.md#organizational-entities)。
