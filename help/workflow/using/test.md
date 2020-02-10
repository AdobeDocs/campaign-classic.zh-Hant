---
title: 測試
seo-title: 測試
description: 測試
seo-description: null
page-status-flag: never-activated
uuid: 3522f4ac-3a72-4ff1-b3aa-1b4c283ef2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 78c70ef4-807d-45d4-ac87-2b741c0ef5cb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 測試{#test}

「測 **試類型** 」活動激活滿足與其相關聯的條件的第一個轉變。 如果未滿足任何條件且已啟 **[!UICONTROL Use the default fork]** 用選項，則會啟用預設轉場。

條件是必須評估為&#39;true&#39;或&#39;false&#39;的JavaScript運算式。 要輸入表達式，請按一下條件名稱右側的表徵圖，然後選擇 **[!UICONTROL Edit...]**。

![](assets/edit_test.png)

如需可透過工作流程JavaScript存取之應用程式伺服器的所有其他JavaScript函式和SOAP方法的詳細資訊，請參閱 [JSAPI檔案](http://docs.campaign.adobe.com/doc/AC/en/jsapi/p-1.html)。

您也可以直接從此編輯器插入變數。

條件可以從活動屬性編輯窗口中添加、刪除或排序，也可以從轉換中修改。

如果計算結果要被不同的條件重複使用，則可以在活動的初始化指令碼中計算該結果。 結果必須儲存在要由條件指令碼(task.vars.xxx)訪問的任務的變數中。
