---
product: campaign
title: 建立摘要清單
description: 建立摘要清單
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: 39cec42a-c7ac-41b1-8f61-799b559ce002
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 2%

---

# 建立摘要清單{#creating-a-summary-list}



此使用案例詳細說明如何建立工作流程，收集檔案並遵循幾項擴充功能後，工作流程可讓您建立摘要清單。 此範例是根據在商店中購買商品的聯絡人清單。

![](assets/uc2_enrich_overview.png)

使用下列資料結構：

![](assets/uc2_enrich_data.png)

其目的是：

* 使用擴充活動的各種選項
* 調解後更新資料庫中的資料
* 若要建立擴充資料的全域「檢視」

若要建立摘要清單，您必須依照下列步驟進行：

1. 在工作流程的工作表中收集和載入「購買」檔案
1. 透過建立參照表格的連結來擴充匯入的資料
1. 使用擴充資料更新「購買」表格
1. 使用「購買」表格的彙總計算擴充「聯絡人」資料
1. 建立摘要清單

## 步驟1：載入檔案並調解匯入的資料 {#step-1--loading-the-file-and-reconciling-the-imported-data}

要載入的資料為以下格式的「購買」相關資料：

```
Product Name;Product price;Store
Computer;2000;London 3
Tablet;600;Cambridge
Computer;2000;London 5
Computer;2000;London 8
Tablet;600;Cambridge
Phone;500;London 5
```

此資料包含在「Purchases.txt」文字檔中。

1. 新增 **檔案收集器** 和 **資料載入（檔案）** 活動至工作流程。

   此 **檔案收集器** 活動可讓您從Adobe Campaign伺服器收集檔案，以及將檔案傳送至該伺服器。

   此 **資料載入（檔案）** 活動可讓您使用收集的資料擴充工作流程的工作表。

   如需此活動的詳細資訊，請參閱 [從檔案載入資料](../../platform/using/import-export-workflows.md#loading-data-from-a-file).

1. 設定 **檔案收集器** 收集文字的活動(&#42;.txt)從選取的目錄中鍵入檔案。

   ![](assets/uc2_enrich_collecteur.png)

   此 **檔案收集器** 活動可讓您管理來源目錄中不存在檔案。 若要這麼做，請核取 **[!UICONTROL Process file nonexistence]** 選項。 在此工作流程中， **等待** 已新增活動，以嘗試另一個檔案集合（如果在集合時目錄中遺失）。

1. 設定 **資料載入（檔案）** 活動，使用與要匯入的資料具有相同格式的範例檔案。

   ![](assets/uc2_enrich_chargement1.png)

   按一下 **[!UICONTROL Click here to change the file format...]** 使用「購買」表格的內部名稱和標籤重新命名欄的連結。

   ![](assets/uc2_enrich_chargement2.png)

匯入資料後，透過建立符合「商店」結構的參考表格連結來執行擴充。

新增擴充活動，並依照以下方式加以設定：

1. 從中選擇由資料組成的主要集合 **資料載入（檔案）** 活動。

   ![](assets/uc2_enrich_enrich1.png)

1. 按一下 **[!UICONTROL Add data]**，然後選取 **[!UICONTROL A link]** 選項。

   ![](assets/uc2_enrich_enrich2.png)

1. 選取 **[!UICONTROL Define a collection]** 選項。
1. 選取「商店」結構描述作為目標。

   ![](assets/uc2_enrich_enrich3.png)

如需各種連結型別的詳細資訊，請參閱 [擴充及修改資料](targeting-data.md#enriching-and-modifying-data).

在下列視窗中，您需要建立連線條件，方法是選取來源欄位（在主集中）和目標欄位（屬於「儲存」綱要）來設定資料協調。

![](assets/uc2_enrich_enrich4.png)

現在連結已建立，我們將從「商店」結構描述中新增欄至工作流程的工作表：「郵遞區號參考」欄位。

1. 開啟擴充活動。
1. 按一下&#x200B;**[!UICONTROL Edit additional data]**。
1. 將「郵遞區號參考」欄位新增至 **[!UICONTROL Output columns]**.

![](assets/uc2_enrich_enrich5.png)

在此擴充後，工作流程工作表中的資料將如下所示：

![](assets/uc2_enrich_population1.png)

## 步驟2：將擴充資料寫入「購買」表格 {#step-2--writing-enriched-data-to-the--purchases--table}

此步驟詳細說明如何將匯入和擴充的資料寫入「購買」表格。 為此，我們需要使用 **更新資料** 活動。

工作流程工作表內的資料與 **購買** 目標維度必須在中的資料之前執行 **購買** 表格已更新。

1. 按一下 **[!UICONTROL Reconciliation]** 擴充活動的索引標籤。
1. 選取目標維度，在此例中為「購買」結構描述。
1. 為工作流程表格中的資料選取「來源運算式」（在此例中為「storeName」欄位）。
1. 為「購買」表格中的資料選取「目的地運算式」（在此例中為「storename」欄位）。
1. 核取 **[!UICONTROL Keep unreconciled data coming from the work table]** 選項。

![](assets/uc2_enrich_reconciliation.png)

在 **更新資料** 活動，需要下列設定：

1. 選取 **[!UICONTROL Insert or update]** 中的選項 **[!UICONTROL Operation type]** 欄位，以避免每次收集檔案時都建立新記錄。
1. 選取 **[!UICONTROL By directly using the targeting dimension]** 的值 **[!UICONTROL Record identification]** 選項。
1. 選取「購買」結構描述作為 **[!UICONTROL Document type]**.
1. 指定要更新的欄位清單。 此 **[!UICONTROL Destination]** 欄可讓您定義「購買」結構描述的欄位。 此 **[!UICONTROL Expression]** 欄可讓您選取工作表中的欄位以執行對應。
1. 按一下 **[!UICONTROL Generate an outbound transition]** 選項。

![](assets/uc2_enrich_miseajour.png)

## 步驟3：擴充「連絡人」資料 {#step-3--enriching--contact--data-}

「連絡人」結構描述會實際連結至「購買」結構描述。 這表示您可以使用「擴充」選項的另一個選項：新增連結至篩選維度的資料。

此第二次擴充的目的是建立購買結構的彙總，以計算每個已識別連絡人的購買總額。

1. 新增 **查詢** 鍵入可讓您全部復原的活動 **連絡人** 已儲存。
1. 新增 **擴充** 活動，然後選取上一個查詢產生的主要集。
1. 按一下新增 **[!UICONTROL Data]**.
1. 按一下 **[!UICONTROL Data linked to the targeting dimension]** 選項。
1. 按一下 **[!UICONTROL Data linked to the filtering dimension]** 中的選項 **[!UICONTROL Select fields to add]** 視窗。
1. 選取 **[!UICONTROL Purchases]** 節點，然後按一下 **[!UICONTROL Next]**.

   ![](assets/uc2_enrich_enrich9.png)

1. 變更 **[!UICONTROL Collected data]** 欄位，方法是選取 **[!UICONTROL Aggregates]** 選項。

   ![](assets/uc2_enrich_enrich10.png)

1. 按一下&#x200B;**[!UICONTROL Next]**。
1. 新增下列運算式以計算每個連絡人的購買總計：&quot;Sum(@prodprice)&quot;。

   ![](assets/uc2_enrich_enrich6.png)

若要準備摘要清單，您需要從「購買」欄位和第一次擴充新增欄位：「郵遞區號參考」欄位。

1. 按一下 **[!UICONTROL Edit additional data...]** 擴充活動中的連結。
1. 新增「商店名稱」和「購買/郵遞區號參考」欄位。

   ![](assets/uc2_enrich_enrich7.png)

1. 按一下 **[!UICONTROL Properties]** 標籤。
1. 變更第二個連結以僅建立一行。

   ![](assets/uc2_enrich_enrich8.png)

## 步驟4：建立並新增至摘要清單 {#step-4--creating-and-adding-to-a-summary-list}

最後一個步驟是將所有擴充資料寫入清單。

1. 新增 **清單更新** 活動至工作流程。 此活動必須連結至第二個擴充活動的出站轉變。
1. 選取 **[!UICONTROL Create the list if necessary (Calculated name)]** 選項。
1. 選取計算名稱的值。 為清單選擇的標籤為目前日期： &lt;%= formatDate(new Date()， &quot;%2D/%2M/%2Y&quot;) %>。

執行工作流程後，清單將包含：

* 連絡人清單，
* 「購買總數」欄，
* 「商店名稱」欄、
* 針對包含在商店參考結構描述中的所有商店輸入的「郵遞區號參考」欄。

![](assets/uc2_enrich_listfinal.png)
