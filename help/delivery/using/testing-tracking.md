---
product: campaign
title: 測試訊息追蹤
description: 瞭解如何測試訊息追蹤
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 1%

---

# 測試訊息追蹤{#testing-tracking}



您可以在映象頁面、電子郵件記錄檔和連結上測試追蹤。 操作步驟：

1. 建立用於測試的新電子郵件傳遞。
1. 指定將接收電子郵件的使用者。 由於此使用者必須開啟電子郵件並按一下其中包含的連結，請務必選取您控制的測試收件者地址。
1. 在電子郵件內容中新增映象頁面(MirrorPage)個人化區塊。
1. 傳送包含映象頁面連結的傳遞。
1. 收到電子郵件後，請開啟該電子郵件，然後按一下映象頁面連結。
1. 在您正確重新導向至映象頁面後，請存取 **管理>技術工作流程** 資料夾並開啟 **追蹤** 工作流程。
1. 啟動工作流程，用滑鼠右鍵按一下 **排程器** 活動並選取 **立即執行擱置中的任務**.
1. 等候約30秒，然後選取 **稽核** 標籤。 請確定至少找到一個追蹤記錄記錄。

   按一下 **重新整理** 如果您沒有看到任何新記錄。

1. 前往您用於測試之收件者的設定檔頁面，然後選取 **追蹤** 標籤。 有些記錄應與 **映象頁面** 中的值 **型別** 欄。

   >[!NOTE]
   >
   >收件者的設定檔頁面位於 **設定檔與目標>收件者** 資料夾預設為。

   若要檢查電子郵件記錄追蹤，請尋找值 **開啟** 和 **[!UICONTROL Email click]** 在 **型別** 欄。

   如果未顯示開啟的記錄，請前往傳送並存取其 **屬性** 以確保兩者 **啟用追蹤** 和 **[!UICONTROL Opens tracking]** 勾選選項。
