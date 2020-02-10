---
title: 載入傳送內容
seo-title: 載入傳送內容
description: 載入傳送內容
seo-description: null
page-status-flag: never-activated
uuid: f2004fb0-9beb-463f-9903-10f291b3663e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 3667da3d-4940-4128-8878-f1ee67216f56
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 載入傳送內容{#loading-delivery-content}

如果您的傳送內容位於Amazon S3、FTP或SFTP伺服器上的HTML檔案中，您就可輕鬆將此內容載入Adobe Campaign傳送。

操作步驟：

1. 如果您尚未定義Adobe Campaign與(S)FTP伺服器之間的連線，請在 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** >中建立新的S3、FTP或SFTP外部帳戶 **[!UICONTROL External Accounts]**。 在此外部帳戶中指定用於建立與S3或(S)FTP伺服器連線的位址和憑證。

   以下是S3外部帳戶的範例：

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. 建立新的工作流程，例如從 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** >建立 **[!UICONTROL Targeting workflows]**。
1. 將活動 **[!UICONTROL File transfer]** 新增至工作流程，並透過指定

   * 用來連線至S3或(S)FTP伺服器的外部帳戶。
   * S3或(S)FTP伺服器上檔案的路徑。
   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. 新增活 **[!UICONTROL Delivery]** 動，並將其連接至活動的出站轉 **[!UICONTROL File transfer]** 換。 按如下方式配置：

   * 傳送：根據您的需求，它可以是系統中已建立的特定傳送，或是以現有範本為基礎的新傳送。
   * 收件者：在此範例中，會將目標視為在傳送本身中指定。
   * 內容：即使內容已匯入上一個活動，請選取 **[!UICONTROL Specified in the delivery]**。 由於內容直接從位於遠程伺服器上的檔案導入，因此在工作流處理時它沒有標識符，不能標識為來自入站事件。
   * 要執行的動作：選 **[!UICONTROL Save]** 擇以儲存傳送，並在執行工作流程後 **[!UICONTROL Campaign management]** , **[!UICONTROL Deliveries]** 即可從>存取。
   ![](assets/delivery_loadcontent_activityexample.png)

1. 在活動 **[!UICONTROL Script]** 的標籤中， **[!UICONTROL Delivery]** 新增下列命令，以載入傳送中匯入檔案的內容：

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. 儲存並執行工作流程。 載入內容的新傳送會建立在 **[!UICONTROL Campaign management]** >下 **[!UICONTROL Deliveries]**。

>[!NOTE]
>
>有關SFTP伺服器使用的最佳實務和疑難排 [解，請參閱本頁](../../platform/using/sftp-server-usage.md)。

