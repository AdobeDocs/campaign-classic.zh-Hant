---
product: campaign
title: 建立摘要清單
description: 建立摘要清單
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: 39cec42a-c7ac-41b1-8f61-799b559ce002
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 2%

---

# 建立摘要清單{#creating-a-summary-list}



此使用案例詳細說明如何建立工作流程，收集檔案並完成數個擴充功能後，即可建立摘要清單。 此範例是根據在商店中進行購買的聯絡人清單。

![](assets/uc2_enrich_overview.png)

以下是使用的資料結構：

![](assets/uc2_enrich_data.png)

其目的是：

* 使用擴充活動的各種選項
* 若要在調解之後更新資料庫中的資料
* 若要建立擴充資料的全域「檢視」

若要建立摘要清單，您必須依照下列步驟進行：

1. 在工作流程的工作表中收集和載入「購買」檔案
1. 透過建立參照表格的連結來擴充匯入的資料
1. 使用擴充資料更新「購買」表格
1. 使用「購買」表格的彙總計算豐富「聯絡人」資料
1. 建立摘要清單

## 步驟1：載入檔案並調解匯入的資料 {#step-1--loading-the-file-and-reconciling-the-imported-data}

要載入的資料為具有以下格式的「購買」相關資料：

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

1. 將&#x200B;**檔案收集器**&#x200B;和&#x200B;**資料載入（檔案）**&#x200B;活動新增至工作流程。

   **檔案收集器**&#x200B;活動可讓您從Adobe Campaign伺服器收集檔案，並將檔案傳送至該伺服器。

   **資料載入（檔案）**&#x200B;活動可讓您使用收集的資料擴充工作流程的工作表。

   如需此活動的詳細資訊，請參閱[從檔案載入資料](../../platform/using/import-export-workflows.md#loading-data-from-a-file)。

1. 設定&#x200B;**檔案收集器**&#x200B;活動，以從選取的目錄中收集文字(&#42;.txt)型別檔案。

   ![](assets/uc2_enrich_collecteur.png)

   **檔案收集器**&#x200B;活動可讓您管理來源目錄中沒有檔案。 若要這麼做，請核取&#x200B;**[!UICONTROL Process file nonexistence]**&#x200B;選項。 在此工作流程中，已新增&#x200B;**等待**&#x200B;活動以嘗試其他檔案集合（如果在集合時目錄中遺失該集合）。

1. 使用與要匯入的資料格式相同的範例檔案，設定&#x200B;**資料載入（檔案）**&#x200B;活動。

   ![](assets/uc2_enrich_chargement1.png)

   按一下&#x200B;**[!UICONTROL Click here to change the file format...]**&#x200B;連結，使用「購買」表格的內部名稱和標籤重新命名欄。

   ![](assets/uc2_enrich_chargement2.png)

在匯入資料後，透過建立符合「商店」方案的參考表格的連結來執行擴充。

新增擴充活動，並依照以下方式設定：

1. 從&#x200B;**資料載入（檔案）**&#x200B;活動中選取由資料組成的主集。

   ![](assets/uc2_enrich_enrich1.png)

1. 按一下&#x200B;**[!UICONTROL Add data]**，然後選取&#x200B;**[!UICONTROL A link]**&#x200B;選項。

   ![](assets/uc2_enrich_enrich2.png)

1. 選取 **[!UICONTROL Define a collection]** 選項。
1. 選取「儲存」結構描述作為目標。

   ![](assets/uc2_enrich_enrich3.png)

如需各種連結型別的詳細資訊，請參閱[擴充及修改資料](targeting-data.md#enriching-and-modifying-data)。

在下列視窗中，您必須藉由選取來源欄位（在主要集中）與目標欄位（屬於「儲存」綱要）來設定資料調解，以建立聯結條件。

![](assets/uc2_enrich_enrich4.png)

現在連結已建立，我們會從「商店」結構描述新增欄至工作流程的工作表：「郵遞區號參考」欄位。

1. 開啟擴充活動。
1. 按一下&#x200B;**[!UICONTROL Edit additional data]**。
1. 將「郵遞區號參考」欄位新增至&#x200B;**[!UICONTROL Output columns]**。

![](assets/uc2_enrich_enrich5.png)

在此擴充後，工作流程工作表中的資料將如下：

![](assets/uc2_enrich_population1.png)

## 步驟2：將擴充資料寫入「購買」表格 {#step-2--writing-enriched-data-to-the--purchases--table}

此步驟詳細說明如何將匯入和擴充的資料寫入「購買」表格。 若要這麼做，我們需要使用&#x200B;**更新資料**&#x200B;活動。

在更新&#x200B;**Purchases**&#x200B;資料表中的資料之前，必須先執行工作流程工作表中的資料與&#x200B;**Purchases**&#x200B;目標維度之間的調解。

1. 按一下擴充活動的&#x200B;**[!UICONTROL Reconciliation]**&#x200B;標籤。
1. 選取目標維度，即此案例中的「購買」結構描述。
1. 在工作流程表格中的資料（在此例中為「storeName」欄位）選取「Source運算式」。
1. 為「購買」表格中的資料選取「目的地運算式」（在此例中為「storename」欄位）。
1. 核取 **[!UICONTROL Keep unreconciled data coming from the work table]** 選項。

![](assets/uc2_enrich_reconciliation.png)

在&#x200B;**更新資料**&#x200B;活動中，需要下列設定：

1. 在&#x200B;**[!UICONTROL Operation type]**&#x200B;欄位中選取&#x200B;**[!UICONTROL Insert or update]**&#x200B;選項，以避免每次收集檔案時都建立新記錄。
1. 選取&#x200B;**[!UICONTROL Record identification]**&#x200B;選項的&#x200B;**[!UICONTROL By directly using the targeting dimension]**&#x200B;值。
1. 選取「購買」結構描述做為&#x200B;**[!UICONTROL Document type]**。
1. 指定要更新的欄位清單。 **[!UICONTROL Destination]**&#x200B;欄可讓您定義「購買」結構描述的欄位。 **[!UICONTROL Expression]**&#x200B;欄可讓您選取工作表中的欄位以執行對應。
1. 按一下&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;選項。

![](assets/uc2_enrich_miseajour.png)

## 步驟3：擴充「連絡人」資料 {#step-3--enriching--contact--data-}

「連絡人」結構描述會實際連結至「購買」結構描述。 這表示您可以使用「擴充」選項的另一個選項：新增連結至篩選維度的資料。

此第二次擴充的目的是針對購買結構建立彙總，以計算每個已識別連絡人的購買總額。

1. 新增&#x200B;**查詢**&#x200B;型別活動，讓您復原所有儲存的&#x200B;**連絡人**。
1. 新增&#x200B;**擴充**&#x200B;活動，然後選取上一個查詢產生的主要集。
1. 按一下[新增&#x200B;**[!UICONTROL Data]**]。
1. 按一下&#x200B;**[!UICONTROL Data linked to the targeting dimension]**&#x200B;選項。
1. 在&#x200B;**[!UICONTROL Select fields to add]**&#x200B;視窗中按一下&#x200B;**[!UICONTROL Data linked to the filtering dimension]**&#x200B;選項。
1. 選取&#x200B;**[!UICONTROL Purchases]**&#x200B;節點，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc2_enrich_enrich9.png)

1. 選取&#x200B;**[!UICONTROL Aggregates]**&#x200B;選項以變更&#x200B;**[!UICONTROL Collected data]**&#x200B;欄位。

   ![](assets/uc2_enrich_enrich10.png)

1. 按一下&#x200B;**[!UICONTROL Next]**。
1. 新增下列運算式以計算每個聯絡人的購買總計：&quot;Sum(@prodprice)&quot;。

   ![](assets/uc2_enrich_enrich6.png)

若要準備摘要清單，您必須從「購買」欄位及首次擴充欄位（「郵遞區號參考」欄位）新增欄位。

1. 按一下擴充活動中的&#x200B;**[!UICONTROL Edit additional data...]**&#x200B;連結。
1. 新增「商店名稱」和「購買/郵遞區號參考」欄位。

   ![](assets/uc2_enrich_enrich7.png)

1. 按一下「**[!UICONTROL Properties]**」標籤。
1. 變更第二個連結，僅建立一行。

   ![](assets/uc2_enrich_enrich8.png)

## 步驟4：建立並新增至摘要清單 {#step-4--creating-and-adding-to-a-summary-list}

最後一個步驟涉及將所有擴充資料寫入清單。

1. 將&#x200B;**清單更新**&#x200B;活動新增至工作流程。 此活動必須連結至第二個擴充活動的出站轉變。
1. 選取 **[!UICONTROL Create the list if necessary (Calculated name)]** 選項。
1. 選取計算名稱的值。 為清單選擇的標籤為目前日期： &lt;%= formatDate(new Date()， &quot;%2D/%2M/%2Y&quot;) %>。

執行工作流程後，清單將包含：

* 連絡人清單，
* 「購買總數」欄、
* 「商店名稱」欄、
* 針對包含在商店參考結構描述中的所有商店輸入的「郵遞區號參考」欄。

![](assets/uc2_enrich_listfinal.png)
