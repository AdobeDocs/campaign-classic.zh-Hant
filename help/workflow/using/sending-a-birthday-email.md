---
product: campaign
title: 傳送生日電子郵件
description: 瞭解如何使用工作流發送生日電子郵件
feature: Workflows
exl-id: 38006cca-e945-4b9d-8e2d-ed537b8541d9
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 1%

---

# 傳送生日電子郵件{#sending-a-birthday-email}

![](../../assets/common.svg)

## 簡介 {#introduction}

此使用案例介紹如何計畫在收件人生日當天向其清單發送定期電子郵件。

要設定此用例，我們建立了以下目標工作流：

![](assets/birthday-workflow_usecase_1.png)

此（每日運行）工作流選擇在當前日期具有其生日的所有收件人。

![](assets/do-not-localize/how-to-video.png) 此用例也可以以視頻的形式找到。 有關詳細資訊，請參閱 [建立工作流](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html) 視頻。

要執行此操作，請建立市場活動，然後按一下 **[!UICONTROL Targeting and workflows]** 頁籤。 有關詳細資訊，請參閱 [在工作流中構建主目標](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow) 的子菜單。

然後執行以下步驟：

## 計畫發送 {#configuring-the-scheduler}

1. 首先，添加 **調度程式** 觸發每天的送貨。 在下面的示例中，每天早上6點建立交貨。

   ![](assets/recur_delivery2.png)


## 標識生日的收件人 {#identifying-recipients-whose-birthday-it-is}

配置 **[!UICONTROL Scheduler]** 活動，以便工作流每天啟動，確定其出生日期等於當前日期的所有收件人。

若要這麼做，請套用下列步驟：

1. 拖放 **[!UICONTROL Query]** 並按兩下它。
1. 按一下 **編輯查詢** 連結和選擇 **[!UICONTROL Filtering conditions]**。

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. 按一下 **[!UICONTROL Expression]** 列，按一下 **[!UICONTROL Edit expression]** 開啟表達式編輯器。

   ![](assets/s_ncs_user_create_exp_exple.png)

1. 按一下 **[!UICONTROL Advanced selection]** 的子菜單。

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. 選擇 **[!UICONTROL Edit the formula using an expression]** 按一下 **[!UICONTROL Next]** 顯示表達式編輯器。
1. 在函式清單中，按兩下 **[!UICONTROL Day]**，可通過 **[!UICONTROL Date]** 的下界。 此函式返回表示與作為參數傳遞的日期相對應的日期的數字。

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. 在可用欄位清單中，按兩下 **[!UICONTROL Birth date]**。 然後，編輯器的上部分顯示以下公式：

   ```
   Day(@birthDate)
   ```

   按一下 **[!UICONTROL Finish]** 確認。

1. 在查詢編輯器中，在 **[!UICONTROL Operator]** 列，選擇 **[!UICONTROL equal to]**。

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. 接下來，按一下第二列的第一個單元格(**[!UICONTROL Value]**)，然後按一下 **[!UICONTROL Edit expression]** 開啟表達式編輯器。
1. 在函式清單中，按兩下 **[!UICONTROL Day]**，可通過 **[!UICONTROL Date]** 的下界。
1. 按兩下 **[!UICONTROL GetDate]** 函式。

   ![](assets/s_ncs_user_create_exp_exple04.png)

   編輯器的上部分顯示以下公式：

   ```
   Day(GetDate())
   ```

   按一下 **[!UICONTROL Finish]** 確認。

1. 重複此步驟以檢索與當前月份對應的出生月份。 要執行此操作，請按一下 **[!UICONTROL Add]** 按鈕並重複步驟3到10，替換 **[!UICONTROL Day]** 與 **[!UICONTROL Month]**。

   完整查詢如下所示：

   ![](assets/s_ncs_user_create_exp_exple03.png)

連結 **[!UICONTROL Query]** 活動 **[!UICONTROL Email delivery]** 的子菜單。

## 包括2月29日出生的受助者（可選） {#including-recipients-born-on-february-29th--optional-}

如果要包括2月29日出生的所有收件人，此使用案例將介紹如何計畫將定期電子郵件發送到其生日收件人清單 — 無論這是否是閏年。

此使用案例的主要實施步驟是：

* 選擇收件人
* 選擇它是否是閏年
* 選擇2月29日出生的任何收件人

要設定此用例，我們建立了以下目標工作流：



如果當前年份 **不是閏年** 工作流在3月1日運行，我們需要選擇昨天（2月29日）已過生日的所有收件人，並將它們添加到收件人清單中。 在任何其他情況下，都不需要採取其他行動。

### 步驟1:選擇收件人 {#step-1--selecting-the-recipients}

配置 **[!UICONTROL Scheduler]** 活動，以便工作流每天啟動，確定其週年日為當天的所有收件人。

>[!NOTE]
>
>如果本年是閏年，則所有2月29日出生的受贈人都將自動包括在內。

![](assets/birthday-workflow_usecase_2.png)

選擇其生日與當前日期對應的收件人 [標識生日的收件人](#identifying-recipients-whose-birthday-it-is) 的子菜單。

### 步驟2:選擇它是否是閏年 {#step-2--select-whether-or-not-it-is-a-leap-year}

的 **[!UICONTROL Test]** 活動允許您檢查它是否是閏年以及當前日期是否為3月1日。

如果test被證實（年不是閏年 — 沒有2月29日 — 而當前日期的確是3月1日）, **[!UICONTROL True]** 過渡已啟用，2月29日出生的收件人將添加到3月1日的遞送。 否則， **[!UICONTROL False]** 轉換已啟用，並且只有在當前日期出生的收件人才會收到遞送。

將下面的代碼複製並貼上到 **[!UICONTROL Initialization script]** 的下界 **[!UICONTROL Advanced]** 頁籤。

```
function isLeapYear(iYear)
{
    if(iYear/4 == Math.floor(iYear/4))
    {
        if(iYear/100 != Math.floor(iYear/100))
        {
            // Divisible by 4 only -> Leap Year
            return 1;
        }
        else
        {
            if(iYear/400 == Math.floor(iYear/400))
            {
                // Divisible by 4, 100 and 400 -> Leap year
                return 1;
            }
        }
    }
    // all others: no leap year
    return 0;
}

// Return today's date and time
var currentTime = new Date()
// returns the month (from 0 to 11)
var month = currentTime.getMonth() + 1
// returns the day of the month (from 1 to 31)
var day = currentTime.getDate()
// returns the year (four digits)
var year = currentTime.getFullYear()

// is current year a leap year?
vars.currentIsALeapYear = isLeapYear(year);

// is current date the first of march?
if(month == 3 && day == 1) {
  // today is 1st of march
vars.firstOfMarch = 1;
}
```

![](assets/birthday-workflow_usecase_3.png)

在 **[!UICONTROL Conditional forks]** 部分：

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### 第3步：選擇2月29日出生的所有收件人 {#step-3--select-any-recipients-born-on-february-29th}

建立 **[!UICONTROL Fork]** 活動並將其中一個出站轉換連結到 **[!UICONTROL Query]** 的子菜單。

在此查詢中，選擇出生日期為2月29日的所有收件人。

![](assets/birthday-workflow_usecase_5.png)

將結果與 **[!UICONTROL Union]** 的子菜單。

連結兩者的結果 **[!UICONTROL Test]** 活動分支到 **[!UICONTROL Email delivery]** 活動，在所有收件人的生日當天向清單發送電子郵件，甚至是在2月29日出生的那些人。

## 建立循環交貨 {#creating-a-recurring-delivery-in-a-targeting-workflow}

添加 **循環交付** 基於要發送的生日電子郵件模板的活動。

>[!CAUTION]
>
>要執行工作流，必須啟動與市場活動包相關的技術工作流。 有關詳細資訊，請參閱 [技術工作流清單](about-technical-workflows.md) 的子菜單。
>
>如果為市場活動啟用了審批步驟，則只有在確認這些步驟後才會發送交貨。 有關詳細資訊，請參閱 [選擇要批准的進程](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved) 的子菜單。

![](assets/birthday-workflow_usecase_1.png)
