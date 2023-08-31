---
product: campaign
title: 定義直接郵件內容
description: 瞭解如何定義直接郵件內容
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Direct Mail
role: User
exl-id: 585b2017-9408-4953-8505-2f6d9db8032f
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 11%

---

# 定義直接郵件內容{#defining-the-direct-mail-content}

## 擷取檔案 {#extraction-file}

包含已擷取資料的檔案名稱會定義於 **[!UICONTROL File]** 欄位。 欄位右側的按鈕可讓您使用個人化欄位來建立檔案名稱。

依照預設，擷取檔案會建立並儲存在伺服器上。 您可以將它儲存在電腦上。 要執行此操作，請核取 **[!UICONTROL Download the generated file after the analysis of the delivery]**. 在此情況下，您需要指出本機儲存目錄的存取路徑以及檔案名稱。

![](assets/s_ncs_user_mail_delivery_local_file.png)

對於直接郵件傳送，擷取的內容定義於 **[!UICONTROL Edit the extraction file format...]** 連結。

![](assets/s_ncs_user_mail_delivery_format_link.png)

此連結可讓您存取擷取精靈，並定義要匯出至輸出檔案的資訊（欄）。

![](assets/s_ncs_user_mail_delivery_format_wz.png)

您可以將個人化URL插入解壓縮檔案中。 如需詳細資訊，請參閱[本章節](../../web/using/publishing-a-web-form.md)。

>[!NOTE]
>
>此精靈包含匯出精靈的步驟，詳見 [快速入門](../../platform/using/executing-export-jobs.md) 區段。
