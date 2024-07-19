---
product: campaign
title: 連線到外部資料庫
description: 瞭解如何連線至外部資料庫
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 240d7e11-da3a-4d64-8986-1f1c8ebcea3c
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# 連線到資料庫 {#connecting-to-the-database}



若要啟用外部資料庫的連線，您必須指定連線引數，即目標資料來源和需要載入資料的表格名稱。

>[!CAUTION]
>
>Adobe Campaign使用者需要外部資料庫和Adobe Campaign應用程式伺服器的特定許可權，才能處理來自外部資料庫的資料。 如需詳細資訊，請參閱[遠端資料庫存取權](../../installation/using/remote-database-access-rights.md)區段。
>
>為避免任何故障，存取遠端共用資料的操作員必須從不同的空間工作。

## 建立共用連線 {#creating-a-shared-connection}

若要啟用共用外部資料庫的連線，只要此連線作用中，就可以透過Adobe Campaign存取資料庫。

1. 必須透過&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;節點預先定義組態。
1. 按一下&#x200B;**[!UICONTROL New]**&#x200B;按鈕並選取&#x200B;**[!UICONTROL External database]**&#x200B;型別。
1. 定義外部資料庫的&#x200B;**[!UICONTROL Connection]**&#x200B;引數。

   對於與&#x200B;**ODBC**&#x200B;型別資料庫的連線，**[!UICONTROL Server]**&#x200B;欄位必須包含ODBC資料來源的名稱，而非伺服器名稱。 此外，視使用的資料庫而定，可能需要進行某些額外的設定。 請參閱[依資料庫型別](../../installation/using/configure-fda.md)的特定組態區段。

1. 輸入引數後，按一下&#x200B;**[!UICONTROL Test the connection]**&#x200B;按鈕以核准它們。

   ![](assets/wf-external-account-create.png)

1. 如有必要，請取消核取&#x200B;**[!UICONTROL Enabled]**&#x200B;選項以停用對此資料庫的存取而不刪除其組態。
1. 若要允許Adobe Campaign存取此資料庫，您必須部署SQL函式。 按一下「**[!UICONTROL Parameters]**」標籤，然後按一下「**[!UICONTROL Deploy functions]**」按鈕。

   ![](assets/wf-external-account-functions.png)

您可以在&#x200B;**[!UICONTROL Parameters]**&#x200B;索引標籤中定義表格和索引的特定工作表格空間。

## 建立暫時連線 {#creating-a-temporary-connection}

您可以從工作流程活動直接定義外部資料庫的連線。 在這種情況下，它會儲存在本機外部資料庫上，並保留供目前工作流程使用：不會儲存在外部帳戶上。 可以在工作流程的不同活動，特別是&#x200B;**[!UICONTROL Query]**、**[!UICONTROL Data loading (RDBMS)]**、**[!UICONTROL Enrichment]**&#x200B;活動或&#x200B;**[!UICONTROL Split]**&#x200B;活動上建立這種型別的準時連線。

>[!CAUTION]
>
>不建議使用此型別的設定，但可定期用來收集資料。 不過，您應該建立外部帳戶，如[建立共用連線](#creating-a-shared-connection)區段中所示。

例如，在查詢活動中，建立與外部資料庫的定期連線的步驟如下：

1. 按一下&#x200B;**[!UICONTROL Add data...]**&#x200B;並選取&#x200B;**[!UICONTROL External data]**&#x200B;選項。
1. 選取&#x200B;**[!UICONTROL Locally defining the data source]**&#x200B;選項。

   ![](assets/wf_add_data_local_external_data.png)

1. 在下拉式清單中選取目標資料庫引擎。 輸入伺服器的名稱並提供驗證引數。

   同時指定外部資料庫的名稱。

   ![](assets/wf_add_data_local_external_data_param.png)

   按一下 **[!UICONTROL Next]** 按鈕。

1. 選取儲存資料的表格。

   您可以直接在對應欄位中輸入表格的名稱，或按一下編輯圖示來存取資料庫表格的清單。

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，以定義外部資料庫資料與Adobe Campaign資料庫資料之間的一或多個調解欄位。 **[!UICONTROL Remote field]**&#x200B;和&#x200B;**[!UICONTROL Local field]**&#x200B;的&#x200B;**[!UICONTROL Edit expression]**&#x200B;圖示可讓您存取每個表格的欄位清單。

   ![](assets/wf_add_data_local_external_data_join.png)

1. 如有需要，請指定篩選條件和資料排序模式。
1. 選取要在外部資料庫中收集的其他資料。 若要這麼做，請連按兩下要新增的欄位，以便在&#x200B;**[!UICONTROL Output columns]**&#x200B;中顯示。

   ![](assets/wf_add_data_local_external_data_select.png)

   按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以確認此組態。

## 安全連線 {#secure-connection}

>[!NOTE]
>
>安全連線僅適用於PostgreSQL。

設定外部FDA帳戶時，您可以保護對外部資料庫的存取權。

若要這麼做，請在所用連線埠的伺服器位址和位址之後新增&quot;**：ssl**&quot;。 例如： **192.168.0.52:4501:ssl**。

然後，資料會透過安全SSL通訊協定傳送。

## 其他設定 {#additional-configurations}

如有必要，您可以建立要在外部資料庫中處理資料的結構描述。 同樣地，Adobe Campaign可讓您定義外部表格中資料的對應。 這些設定是一般設定，不會專門套用於工作流程。

>[!NOTE]
>
>如需在Adobe Campaign中建立結構描述及定義新資料對應的詳細資訊，請參閱[此頁面](../../configuration/using/about-schema-edition.md)。
