---
product: campaign
title: 存取外部資料庫
description: 了解如何連接到外部資料庫
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 240d7e11-da3a-4d64-8986-1f1c8ebcea3c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# 連接到資料庫 {#connecting-to-the-database}

![](../../assets/v7-only.svg)

要啟用與外部資料庫的連接，必須指明連接參數，即目標資料源和表的名稱，以及需要載入的資料。

>[!CAUTION]
>
>Adobe Campaign使用者需要外部資料庫和Adobe Campaign應用程式伺服器的特定權限，才能處理來自外部資料庫的資料。 有關詳細資訊，請參閱[遠程資料庫訪問權限](../../installation/using/remote-database-access-rights.md)部分。
>
>為避免出現任何故障，訪問遠程共用資料的操作員必須從單獨的空間工作。

## 建立共用連線 {#creating-a-shared-connection}

若要啟用與共用外部資料庫的連線，只要此連線處於作用中狀態，即可透過Adobe Campaign存取資料庫。

1. 必須預先透過&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;節點定義設定。
1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;按鈕並選擇&#x200B;**[!UICONTROL External database]**&#x200B;類型。
1. 定義外部資料庫的&#x200B;**[!UICONTROL Connection]**&#x200B;參數。

   對於與&#x200B;**ODBC**&#x200B;的連接，**[!UICONTROL Server]**&#x200B;欄位必須包含ODBC資料源的名稱，而不是伺服器名稱。 此外，根據所使用的資料庫，可能需要某些額外配置。 請參閱[按資料庫類型列出的特定配置](../../installation/using/configure-fda.md)部分。

1. 輸入參數後，按一下&#x200B;**[!UICONTROL Test the connection]**&#x200B;按鈕以核准這些參數。

   ![](assets/wf-external-account-create.png)

1. 如有必要，請取消選中&#x200B;**[!UICONTROL Enabled]**&#x200B;選項，以禁用對此資料庫的訪問，而不刪除其配置。
1. 要允許Adobe Campaign訪問此資料庫，必須部署SQL函式。 按一下&#x200B;**[!UICONTROL Parameters]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Deploy functions]**&#x200B;按鈕。

   ![](assets/wf-external-account-functions.png)

您可以在&#x200B;**[!UICONTROL Parameters]**&#x200B;頁簽中為表和索引定義特定的工作表空間。

## 建立臨時連接 {#creating-a-temporary-connection}

您可以從工作流程活動直接定義外部資料庫的連線。 在此情況下，它將位於本地外部資料庫上，保留用於當前工作流中：不會儲存在外部帳戶上。 可以在工作流的不同活動上建立此類準時連接，特別是&#x200B;**[!UICONTROL Query]**、**[!UICONTROL Data loading (RDBMS)]**、**[!UICONTROL Enrichment]**&#x200B;活動或&#x200B;**[!UICONTROL Split]**&#x200B;活動。

>[!CAUTION]
>
>不建議使用此類型的配置，但可定期用於收集資料。 不過，您應建立外部帳戶，如[建立共用連線](#creating-a-shared-connection)區段所示。

例如，在查詢活動中，建立外部資料庫定期連接的步驟如下：

1. 按一下&#x200B;**[!UICONTROL Add data...]**&#x200B;並選取&#x200B;**[!UICONTROL External data]**&#x200B;選項。
1. 選擇&#x200B;**[!UICONTROL Locally defining the data source]**&#x200B;選項。

   ![](assets/wf_add_data_local_external_data.png)

1. 在下拉式清單中選取目標資料庫引擎。 輸入伺服器的名稱並提供驗證參數。

   也指定外部資料庫的名稱。

   ![](assets/wf_add_data_local_external_data_param.png)

   按一下 **[!UICONTROL Next]** 按鈕。

1. 選擇資料儲存所在的表。

   您可以直接在相應欄位中輸入表的名稱，或按一下編輯表徵圖以訪問資料庫表的清單。

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，在外部資料庫資料和Adobe Campaign資料庫中的資料之間定義一個或多個協調欄位。 **[!UICONTROL Remote field]**&#x200B;和&#x200B;**[!UICONTROL Local field]**&#x200B;的&#x200B;**[!UICONTROL Edit expression]**&#x200B;表徵圖允許您訪問每個表的欄位清單。

   ![](assets/wf_add_data_local_external_data_join.png)

1. 如有必要，請指定篩選條件和資料排序模式。
1. 選取要在外部資料庫中收集的其他資料。 要執行此操作，請連按兩下要新增的欄位，以在&#x200B;**[!UICONTROL Output columns]**&#x200B;中顯示這些欄位。

   ![](assets/wf_add_data_local_external_data_select.png)

   按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以確認此配置。

## 安全連接 {#secure-connection}

>[!NOTE]
>
>安全連接僅對PostgreSQL可用。

設定外部FDA帳戶時，您可以安全地存取外部資料庫。

要執行此操作，請在所用埠的伺服器地址和地址後面添加&quot;**:ssl**&quot;。 例如：**192.168.0.52:4501:ssl**。

然後，資料會透過安全SSL通訊協定傳送。

## 其他設定 {#additional-configurations}

如有必要，您可以建立用於處理外部資料庫中資料的架構。 同樣地，Adobe Campaign可讓您定義外部表格中資料的對應。 這些設定為一般設定，不專用於工作流程。

>[!NOTE]
>
>如需在Adobe Campaign中建立結構以及定義新資料對應的詳細資訊，請參閱本頁[。](../../configuration/using/about-schema-edition.md)
