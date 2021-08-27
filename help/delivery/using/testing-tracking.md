---
product: campaign
title: 測試追蹤
description: 測試追蹤
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 3%

---

# 測試追蹤{#testing-tracking}

![](../../assets/common.svg)

您可以測試鏡像頁面、電子郵件記錄和連結上的追蹤。 操作步驟：

1. 建立要用於測試的新電子郵件傳送。
1. 指定將接收電子郵件的使用者。 由於此使用者必須開啟電子郵件並按一下其包含的連結，請務必選取您控制的測試收件者地址。
1. 在電子郵件內容中新增鏡像頁面(MirrorPage)個人化區塊。
1. 傳送包含鏡像頁面連結的傳送。
1. 收到電子郵件後，請開啟它，然後按一下鏡像頁面連結。
1. 將您正確重新導向至鏡像頁面後，請存取&#x200B;**管理>技術工作流程**&#x200B;資料夾，並開啟&#x200B;**追蹤**&#x200B;工作流程。
1. 啟動工作流，按一下右鍵&#x200B;**Scheduler**&#x200B;活動並選擇&#x200B;**Execute pending task now**。
1. 等待約30秒，然後選擇&#x200B;**Audit**&#x200B;頁簽。 請確定至少找到一個追蹤記錄。

   如果您沒有看到任何新記錄，請按一下「**重新整理**」。

1. 前往您用於測試的收件者的設定檔頁面，然後選取&#x200B;**Tracking**&#x200B;標籤。 有些記錄應以&#x200B;**Type**&#x200B;欄中的&#x200B;**鏡像頁面**&#x200B;值顯示。

   >[!NOTE]
   >
   >收件者的設定檔頁面依預設位於&#x200B;**設定檔與目標>收件者**&#x200B;資料夾中。

   若要檢查電子郵件記錄追蹤，請尋找&#x200B;**Type**&#x200B;欄中的&#x200B;**Open**&#x200B;和&#x200B;**[!UICONTROL Email click]**&#x200B;值。

   如果未顯示開啟的記錄檔，請前往傳送並存取其&#x200B;**屬性**，以確定已勾選&#x200B;**啟用追蹤**&#x200B;和&#x200B;**[!UICONTROL Opens tracking]**&#x200B;選項。
