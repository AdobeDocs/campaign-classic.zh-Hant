---
title: 測試追蹤
seo-title: 測試追蹤
description: 測試追蹤
seo-description: null
page-status-flag: never-activated
uuid: 76d84ab4-b632-4498-96a1-ce9c773ec125
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 4ed23249-4ecf-4e57-91b3-6fae1387bd6a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 測試追蹤{#testing-tracking}

您可以在鏡像頁面、電子郵件記錄檔和連結上測試追蹤。 操作步驟：

1. 建立新的電子郵件傳送，以用於測試。
1. 指定將接收電子郵件的使用者。 由於此使用者必須開啟電子郵件並按一下其所包含的連結，請務必選取您控制的測試收件者位址。
1. 在電子郵件內容中添加鏡像頁面(MirrorPage)個性化塊。
1. 傳送包含鏡像頁面連結的傳送。
1. 收到電子郵件後，請將其開啟，然後按一下鏡像頁連結。
1. 將您正確重新導向至鏡像頁面後，請存取「管理> **技術工作流程** 」檔案夾並開啟「追 **蹤** 」工作流程。
1. 啟動工作流，按一下右鍵 **Scheduler活動** ，然後選擇 **立即執行暫掛任務**。
1. 等待約30秒，然後選取「 **Audit** 」標籤。 請確定至少找到一個追蹤記錄。

   如果 **未看到任何新日誌** ，請按一下刷新。

1. 前往您用於測試的收件者的描述檔頁面，並選取「追 **蹤** 」標籤。 某些記錄應與「類型」 **列中的** 「鏡像頁 **面」值一起顯示** 。

   >[!NOTE]
   >
   >依預設，收件者的描述檔頁面位於「描述檔 **與目標>收件者** 」檔案夾中。

   若要檢查電子郵件記錄追蹤，請尋找「 **Open** 」 **[!UICONTROL Email click]** 和「 **Type** 」欄中的值。

   如果未顯示開啟的記錄檔，請前往傳送並存取其 **屬性** ，以確認已勾選「啟 **用追蹤** 」 **[!UICONTROL Opens tracking]** 和選項。

