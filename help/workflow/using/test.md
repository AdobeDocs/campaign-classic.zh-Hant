---
product: campaign
title: 測試
description: 進一步了解測試工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 5%

---

# 測試{#test}

**Test**&#x200B;類型活動激活滿足與其相關的條件的第一轉變。 如果未滿足任何條件，並且激活了&#x200B;**[!UICONTROL Use the default fork]**&#x200B;選項，則將激活預設轉變。

條件是必須評估為「true」或「false」的JavaScript運算式。 若要輸入運算式，請按一下條件名稱右側的圖示，然後選取&#x200B;**[!UICONTROL Edit...]**。

![](assets/edit_test.png)

有關可通過工作流JavaScript訪問的應用程式伺服器的所有其他JavaScript函式和SOAP方法的詳細資訊，請參閱[JSAPI文檔](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

您也可以直接從此編輯器插入變數。 有關如何使用變數的詳細資訊，請參閱[此區段](../../workflow/using/javascript-scripts-and-templates.md#variables)。

您可以從活動屬性編輯視窗新增、刪除或排序條件，也可以從轉變中修改條件。

如果計算結果要被不同條件重複使用，則可以在活動的初始化指令碼中計算它。 結果必須儲存在要由條件指令碼(task.vars.xxx)存取之任務的變數中。
