---
solution: Campaign Classic
product: campaign
title: 測試
description: 進一步瞭解測試工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 5%

---


# 測試 {#test}

**Test**&#x200B;類型活動激活滿足與其相關聯的條件的第一過渡。 如果未滿足任何條件，且&#x200B;**[!UICONTROL Use the default fork]**&#x200B;選項已激活，則將激活預設過渡。

條件是必須評估為&#39;true&#39;或&#39;false&#39;的JavaScript運算式。 要輸入表達式，請按一下條件名稱右側的表徵圖，然後選擇&#x200B;**[!UICONTROL Edit...]**。

![](assets/edit_test.png)

有關可通過工作流JavaScript訪問的應用程式伺服器的所有附加JavaScript函式和SOAP方法的詳細資訊，請參閱[JSAPI文檔](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

您也可以直接從此編輯器插入變數。 有關如何使用變數的詳細資訊，請參閱[本節](../../workflow/using/javascript-scripts-and-templates.md#variables)。

條件可以從活動屬性編輯窗口中添加、刪除或排序，也可以從轉換中修改。

如果計算結果要被不同的條件重複使用，則可以在活動的初始化指令碼中計算該結果。 結果必須儲存在要由條件指令碼(task.vars.xxx)訪問的任務的變數中。
