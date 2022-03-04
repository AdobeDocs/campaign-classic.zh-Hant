---
product: campaign
title: 載入傳遞內容
description: 載入傳遞內容
feature: Workflows
exl-id: a52baffd-402b-4b33-ab72-ac954e4dee85
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 3%

---

# 載入傳遞內容{#loading-delivery-content}

![](../../assets/common.svg)

如果您的傳送內容位於AmazonS3、FTP或SFTP伺服器上的HTML檔案中，則您可以輕鬆地將此內容載入到Adobe Campaign傳送中。

操作步驟：

1. 如果尚未定義Adobe Campaign與承載內容檔案的(S)FTP伺服器之間的連接，請在 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**。 在此外部帳戶中指定用於建立與S3或(S)FTP伺服器的連接的地址和憑據。

   下面是S3外部帳戶的示例：

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. 建立新工作流，例如 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**。
1. 添加 **[!UICONTROL File transfer]** 活動並通過指定

   * 用於連接到S3或(S)FTP伺服器的外部帳戶。
   * S3或(S)FTP伺服器上檔案的路徑。

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. 添加 **[!UICONTROL Delivery]** 活動並將其連接到 **[!UICONTROL File transfer]** 的子菜單。 按如下方式配置：

   * 交貨：根據您的需要，它可以是系統中已建立的特定交貨，也可以是基於現有模板的新交貨。
   * 收件人：在本示例中，將目標視為在傳遞本身中指定。
   * 內容：即使內容在上一活動中導入，請選擇 **[!UICONTROL Specified in the delivery]**。 由於內容直接從位於遠程伺服器上的檔案導入，因此當工作流處理時它沒有標識符，因此無法標識為來自入站事件。
   * 要執行的操作：選擇 **[!UICONTROL Save]** 保存交貨，並能夠從 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** 執行工作流後。

   ![](assets/delivery_loadcontent_activityexample.png)

1. 在 **[!UICONTROL Script]** 頁籤 **[!UICONTROL Delivery]** 活動，添加以下命令以在傳遞中載入導入檔案的內容：

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. 保存並執行工作流。 將在下面建立包含已載入內容的新傳遞 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

>[!NOTE]
>
>詳細介紹了SFTP伺服器使用的最佳做法和故障排除 [此頁](../../platform/using/sftp-server-usage.md)。
