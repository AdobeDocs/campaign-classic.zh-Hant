---
solution: Campaign Classic
product: campaign
title: 載入傳遞內容
description: 載入傳遞內容
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 3%

---


# 載入傳遞內容{#loading-delivery-content}

如果您的傳送內容位於Amazon S3、FTP或SFTP伺服器上的HTML檔案中，您就可輕鬆將此內容載入Adobe Campaign傳送。

操作步驟：

1. 如果您尚未定義Adobe Campaign與代管內容檔案的(S)FTP伺服器之間的連線，請在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**&#x200B;中建立新的S3、FTP或SFTP外部帳戶。 在此外部帳戶中指定用於建立與S3或(S)FTP伺服器連線的位址和憑證。

   以下是S3外部帳戶的範例：

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. 建立新的工作流程，例如從&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**&#x200B;建立。
1. 將&#x200B;**[!UICONTROL File transfer]**&#x200B;活動新增至您的工作流程，並透過指定

   * 用來連線至S3或(S)FTP伺服器的外部帳戶。
   * S3或(S)FTP伺服器上檔案的路徑。

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. 添加&#x200B;**[!UICONTROL Delivery]**&#x200B;活動，並將其連接到&#x200B;**[!UICONTROL File transfer]**&#x200B;活動的出站轉換。 按如下方式配置：

   * 傳送：根據您的需求，它可以是系統中已建立的特定傳送，或是以現有範本為基礎的新傳送。
   * 收件者：在此範例中，會將目標視為在傳送本身中指定。
   * 內容：即使內容已匯入上一個活動，請選取&#x200B;**[!UICONTROL Specified in the delivery]**。 由於內容直接從位於遠程伺服器上的檔案導入，因此在工作流處理時它沒有標識符，不能標識為來自入站事件。
   * 要執行的動作：選擇&#x200B;**[!UICONTROL Save]**&#x200B;以儲存傳送，並在工作流程執行後，從&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**&#x200B;存取傳送。

   ![](assets/delivery_loadcontent_activityexample.png)

1. 在&#x200B;**[!UICONTROL Delivery]**&#x200B;活動的&#x200B;**[!UICONTROL Script]**&#x200B;標籤中，添加以下命令以載入傳送中導入檔案的內容：

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. 儲存並執行工作流程。 在&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**&#x200B;下會建立包含載入內容的新傳送。

>[!NOTE]
>
>有關SFTP伺服器使用情況的最佳實踐和故障排除，請參見本頁](../../platform/using/sftp-server-usage.md)。[
