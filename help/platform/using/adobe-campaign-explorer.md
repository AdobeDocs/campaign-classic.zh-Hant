---
product: campaign
title: 使用Adobe Campaign Explorer
description: 瞭解如何使用Campaign Explorer
feature: Overview
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f91d69a4-b794-40f0-b450-de862d7333e2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 14%

---

# 使用Adobe Campaign Explorer {#using-adobe-campaign-explorer}



Adobe Campaign檔案總管可透過工具列圖示存取。 使用工具列圖示，您可以存取 Adobe Campaign、所有 Adobe Campaign 功能、設定畫面以及部分平台元素的更詳細視圖。

**[!UICONTROL Explorer]**&#x200B;工作區分為三個區域：

![](assets/s_ncs_user_navigation.png)

**1 — 樹狀結構**：您可以個人化樹狀結構的內容（新增、移動或刪除節點）。 此程式僅供專家使用者使用。 如需詳細資訊，請參閱[本節](#about-navigation-hierarchy)。

**2 — 清單**：您可以篩選此清單、執行搜尋、新增資訊或排序資料。 [了解更多](adobe-campaign-ui-lists.md)。

**3 — 詳細資料**：您可以顯示所選元素的詳細資料。 透過右上角的圖示，您可以全螢幕顯示這項資訊。

## 資料夾和導覽樹狀結構{#about-navigation-hierarchy}

導覽樹狀結構的運作方式與檔案瀏覽器類似（例如Windows檔案總管）。 資料夾可能包含子資料夾。 選取節點會顯示與節點對應的檢視。

顯示的檢視是與結構描述關聯的清單，以及用來編輯所選行的輸入表單。

![](assets/d_ncs_integration_navigation.png)

若要將新資料夾新增至樹狀結構，請在您要插入資料夾的分支中以滑鼠右鍵按一下該資料夾，然後選取「**[!UICONTROL Add new folder]**」。 在快捷選單中，選取要建立的檔案型別。

![](assets/d_ncs_integration_navigation_create.png)

在本節](../../configuration/using/configuration.md)中瞭解如何設定Campaign導覽樹狀結構[。

在本節](access-management-folders.md)中瞭解如何設定資料夾[的許可權。

## 資料夾設定最佳實務

* **使用內建資料夾**

  使用內建資料夾讓未參與專案的人更易於使用、維護及疑難排解應用程式。 您不應該為收件者、清單、傳遞等建立自訂資料夾結構，而是使用標準資料夾，例如管理、設定檔和目標、行銷活動管理。

* **建立子資料夾**

  將技術工作流程放置在標準資料夾：管理/生產/技術工作流程下，並根據工作流程型別建立子目錄。

* **設定命名慣例**

  例如，您可以按字母順序命名工作流程，好讓工作流程按執行順序排序。

  例如：

   * A1 — 匯入收件者，從10:00開始；
   * A2 — 匯入票證，11:00開始。

* **建立範本讓使用者開始使用**

  建立使用者專用的傳遞範本、工作流程範本、行銷活動範本。 此結構可節省時間，並確保為每個使用者使用正確的傳遞對應和型別。

## 螢幕解析度 {#screen-resolution}

為了獲得最佳導覽和可用性，Adobe 建議最少使用像素 1600x900 的螢幕解析度。

>[!CAUTION]
>
>Adobe Campaign不支援1600x900畫素以下的解析度。

在&#x200B;**[!UICONTROL Explorer]**&#x200B;工作區中，如果&#x200B;**[!UICONTROL Details]**&#x200B;區域的某些部分似乎遭到截斷，請使用區域頂端的箭頭將其展開，或按一下&#x200B;**[!UICONTROL Enlarge]**&#x200B;按鈕。

![](assets/s_ncs_user_resolution.png)

## 瀏覽及自訂清單 {#browsing-lists}

在本節](adobe-campaign-ui-lists.md)中瞭解如何瀏覽、管理及自訂清單[。
