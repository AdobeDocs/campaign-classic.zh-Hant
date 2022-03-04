---
product: campaign
title: 測試
description: 瞭解有關Test工作流活動的詳細資訊
feature: Workflows
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# 測試{#test}

![](../../assets/common.svg)

A **Test** type activity激活滿足與其關聯的條件的第一個過渡。 如果未滿足條件，並且 **[!UICONTROL Use the default fork]** 選項時，將激活預設過渡。

條件是必須計算為「true」或「false」的JavaScript表達式。 要輸入表達式，請按一下條件名稱右側的表徵圖，然後選擇 **[!UICONTROL Edit...]**。

![](assets/edit_test.png)

有關通過工作流JavaScript可訪問的應用程式伺服器的所有附加JavaScript函式和SOAP方法的詳細資訊，請參閱 [JSAPI文檔](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)。

也可以直接從此編輯器插入變數。 有關如何使用變數的詳細資訊，請參閱 [此部分](javascript-scripts-and-templates.md#variables)。

可以從活動屬性編輯窗口添加、刪除或排序條件，也可以從轉換中修改條件。

如果計算結果要被不同條件重用，則可以在活動的初始化指令碼中計算它。 結果必須儲存在條件指令碼(task.vars.xxx)要訪問的任務的變數中。
