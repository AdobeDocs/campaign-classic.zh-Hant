---
product: campaign
title: 載入傳遞內容
description: 正在載入傳遞內容
feature: Workflows
exl-id: a52baffd-402b-4b33-ab72-ac954e4dee85
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 2%

---

# 載入傳遞內容{#loading-delivery-content}



如果您的傳送內容位於Amazon S3、FTP或SFTP伺服器上的HTML檔案中，則可輕鬆將此內容載入到Adobe Campaign傳送中。

操作步驟：

1. 如果您尚未定義Adobe Campaign與託管內容檔案的(S) FTP伺服器之間的連線，請在中建立新的S3、FTP或SFTP外部帳戶 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. 在此外部帳戶中指定用來建立與S3或(S) FTP伺服器連線的位址和認證。

   以下是S3外部帳戶的範例：

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. 建立新的工作流程，例如從 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. 新增 **[!UICONTROL File transfer]** 活動放入工作流程中，並透過指定進行設定

   * 用來連線至S3或(S) FTP伺服器的外部帳戶。
   * S3或(S) FTP伺服器上的檔案路徑。

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. 新增 **[!UICONTROL Delivery]** 活動，並將其連線到以下專案的出站轉變： **[!UICONTROL File transfer]** 活動。 請依照以下步驟設定：

   * 傳送：根據您的需求，可以是系統中已建立的特定傳送，或根據現有範本的新傳送。
   * 收件者：在此範例中，將視為在傳送本身中指定目標。
   * 內容：即使內容是在前一個活動中匯入，請選取 **[!UICONTROL Specified in the delivery]**. 由於內容是從遠端伺服器上的檔案直接匯入，因此在工作流程處理時不會有任何識別碼，且無法識別為來自入站事件。
   * 要執行的動作：選取 **[!UICONTROL Save]** 以儲存傳遞，並從中存取傳遞 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** 執行工作流程後。

   ![](assets/delivery_loadcontent_activityexample.png)

1. 在 **[!UICONTROL Script]** 的標籤 **[!UICONTROL Delivery]** 活動，新增下列命令以載入傳送中匯入檔案的內容：

   ```
   delivery.content.html.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. 儲存並執行工作流程。 已載入內容的新傳遞會建立在 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

>[!NOTE]
>
>詳細說明有關SFTP伺服器使用的最佳實務及疑難排解 [在此頁面中](../../platform/using/sftp-server-usage.md).
