---
product: campaign
title: 測試
description: 進一步了解測試工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: 5d9e2f7d7cea9e6d1243b0e3a790f3990772e603
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# 測試{#test}

![](../../assets/common.svg)

A **測試** 類型活動會啟動滿足與其相關的條件的第一個轉變。 If no condition is satisfied and if the **[!UICONTROL Use the default fork]** option is activated, the default transition will be activated.

A condition is a JavaScript expression that must be evaluated to &#39;true&#39; or &#39;false&#39;. 若要輸入運算式，請按一下條件名稱右側的圖示，然後選取 **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

如需可透過工作流程JavaScript存取之應用程式伺服器的所有其他JavaScript函式和SOAP方法的詳細資訊，請參閱 [JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html).

您也可以直接從此編輯器插入變數。 如需如何使用變數的詳細資訊，請參閱 [本節](javascript-scripts-and-templates.md#variables).

Conditions can be added, deleted, or ordered from the activity property edit window, but can also be modified from the transition.

If the result of a calculation is to be reused by different conditions, it is possible to calculate it in the initialization script of the activity. 結果必須儲存在要由條件指令碼(task.vars.xxx)存取之任務的變數中。
