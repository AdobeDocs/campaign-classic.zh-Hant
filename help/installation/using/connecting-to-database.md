---
product: campaign
title: 連結至外部資料庫
description: 瞭解如何連接到外部資料庫
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 240d7e11-da3a-4d64-8986-1f1c8ebcea3c
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# 連接到資料庫 {#connecting-to-the-database}

![](../../assets/v7-only.svg)

要啟用到外部資料庫的連接，必須指明連接參數，即目標資料源和需要載入資料的表的名稱。

>[!CAUTION]
>
>Adobe Campaign用戶需要外部資料庫和Adobe Campaign應用程式伺服器的特定權限來處理來自外部資料庫的資料。 有關詳細資訊，請參閱 [遠程資料庫訪問權限](../../installation/using/remote-database-access-rights.md) 的子菜單。
>
>為避免任何故障，訪問遠程共用資料的操作員必須在單獨的空間中工作。

## 建立共用連線 {#creating-a-shared-connection}

要啟用到共用外部資料庫的連接，只要此連接處於活動狀態，就可以通過Adobe Campaign訪問資料庫。

1. 配置必須通過 **[!UICONTROL Administration > Platform > External accounts]** 的下界。
1. 按一下 **[!UICONTROL New]** 按鈕 **[!UICONTROL External database]** 的雙曲餘切值。
1. 定義 **[!UICONTROL Connection]** 外部資料庫的參數。

   用於與 **ODBC** 鍵入資料庫 **[!UICONTROL Server]** 欄位必須包含ODBC資料源的名稱，而不包含伺服器名。 此外，根據使用的資料庫，可能需要某些附加配置。 請參閱 [按資料庫類型列出的特定配置](../../installation/using/configure-fda.md) 的子菜單。

1. 輸入參數後，按一下 **[!UICONTROL Test the connection]** 按鈕

   ![](assets/wf-external-account-create.png)

1. 如有必要，請取消選中 **[!UICONTROL Enabled]** 選項，可禁用對此資料庫的訪問而不刪除其配置。
1. 要允許Adobe Campaign訪問此資料庫，必須部署SQL函式。 按一下 **[!UICONTROL Parameters]** 按鈕 **[!UICONTROL Deploy functions]** 按鈕

   ![](assets/wf-external-account-functions.png)

您可以為中的表和索引定義特定的工作表空間 **[!UICONTROL Parameters]** 頁籤。

## 建立臨時連接 {#creating-a-temporary-connection}

您可以直接從工作流活動定義到外部資料庫的連接。 在這種情況下，它將位於本地外部資料庫上，保留用於當前工作流：不會保存在外部帳戶中。 可以在工作流的不同活動上建立此類準時連接，尤其是 **[!UICONTROL Query]**，也請參見Wiki頁。 **[!UICONTROL Data loading (RDBMS)]**，也請參見Wiki頁。 **[!UICONTROL Enrichment]** 或 **[!UICONTROL Split]** 的子菜單。

>[!CAUTION]
>
>不建議使用此類型的配置，但可以定期用於收集資料。 但是，您應建立外部帳戶，如 [建立共用連接](#creating-a-shared-connection) 的子菜單。

例如，在查詢活動中，建立與外部資料庫的定期連接的步驟如下：

1. 按一下 **[!UICONTROL Add data...]** 的 **[!UICONTROL External data]** 頁籤
1. 選擇 **[!UICONTROL Locally defining the data source]** 的雙曲餘切值。

   ![](assets/wf_add_data_local_external_data.png)

1. 在下拉清單中選擇目標資料庫引擎。 輸入伺服器名稱並提供驗證參數。

   還指定外部資料庫的名稱。

   ![](assets/wf_add_data_local_external_data_param.png)

   按一下 **[!UICONTROL Next]** 按鈕。

1. 選擇儲存資料的表。

   可以直接在相應欄位中輸入表的名稱，或按一下編輯表徵圖訪問資料庫表的清單。

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. 按一下 **[!UICONTROL Add]** 按鈕，定義外部資料庫資料與Adobe Campaign資料庫中資料之間的一個或多個協調欄位。 的 **[!UICONTROL Edit expression]** 表徵圖 **[!UICONTROL Remote field]** 和 **[!UICONTROL Local field]** 允許您訪問每個表的欄位清單。

   ![](assets/wf_add_data_local_external_data_join.png)

1. 如有必要，請指定篩選條件和資料排序模式。
1. 選擇要在外部資料庫中收集的其他資料。 為此，請按兩下要添加的欄位，以在 **[!UICONTROL Output columns]**。

   ![](assets/wf_add_data_local_external_data_select.png)

   按一下 **[!UICONTROL Finish]** 確認此配置。

## 安全連接 {#secure-connection}

>[!NOTE]
>
>安全連接僅對PostgreSQL可用。

在配置外部FDA帳戶時，您可以確保對外部資料庫的訪問安全。

為此，請添加「」**:ssl**&quot;在使用的埠的伺服器地址和地址之後。 例如： **192.168.0.52:4501:sys**。

然後，資料將通過安全SSL協定發送。

## 其他設定 {#additional-configurations}

如有必要，可以建立用於處理外部資料庫中資料的架構。 同樣，Adobe Campaign允許您定義外部表中的資料映射。 這些配置是常規配置，不僅適用於工作流。

>[!NOTE]
>
>有關在Adobe Campaign建立架構和定義新資料映射的詳細資訊，請參閱 [此頁](../../configuration/using/about-schema-edition.md)。
