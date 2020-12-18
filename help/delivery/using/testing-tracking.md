---
solution: Campaign Classic
product: campaign
title: 測試追蹤
description: 測試追蹤
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 3%

---


# 測試追蹤{#testing-tracking}

您可以在鏡像頁面、電子郵件記錄檔和連結上測試追蹤。 操作步驟：

1. 建立新的電子郵件傳送，以用於測試。
1. 指定將接收電子郵件的使用者。 由於此使用者必須開啟電子郵件並按一下其所包含的連結，請務必選取您控制的測試收件者位址。
1. 在電子郵件內容中添加鏡像頁面(MirrorPage)個性化塊。
1. 傳送包含鏡像頁面連結的傳送。
1. 收到電子郵件後，請將其開啟，然後按一下鏡像頁連結。
1. 將您正確重新導向至鏡像頁面後，請存取「**管理>技術工作流程**」資料夾並開啟「追蹤&#x200B;**」工作流程。**
1. 啟動工作流，按一下右鍵&#x200B;**調度程式**&#x200B;活動，然後選擇&#x200B;**立即執行暫掛任務**。
1. 等待約30秒，然後選擇&#x200B;**Audit**&#x200B;標籤。 請確定至少找到一個追蹤記錄。

   如果您未看到任何新日誌，請按一下&#x200B;**刷新**。

1. 前往您用於測試的收件者的描述檔頁面，並選取「追蹤」標籤。 ****&#x200B;某些記錄應與&#x200B;**Type**&#x200B;列中的&#x200B;**Mirror Page**&#x200B;值一起顯示。

   >[!NOTE]
   >
   >依預設，收件者的描述檔頁面位於&#x200B;**描述檔與目標>收件者**&#x200B;資料夾中。

   若要檢查電子郵件記錄追蹤，請在&#x200B;**Type**&#x200B;欄中尋找&#x200B;**Open**&#x200B;和&#x200B;**[!UICONTROL Email click]**&#x200B;值。

   如果未顯示開啟的記錄檔，請前往傳送並存取其&#x200B;**屬性**，以確認已勾選&#x200B;**啟動追蹤**&#x200B;和&#x200B;**[!UICONTROL Opens tracking]**&#x200B;選項。

