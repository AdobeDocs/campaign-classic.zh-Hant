---
product: campaign
title: 關於立方體
description: 開始使用多維度資料集
feature: Reporting, Monitoring
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
hide: true
hidefromtoc: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 2%

---

# 開始使用多維度資料集{#about-cubes}



## 術語 {#terminology}

以下列出使用立方體時的具體辭彙。

* **Cube** - Cube是多維度資訊的表示法：它為使用者提供專為互動式資料分析設計的結構。

* **事實資料表/結構描述** — 事實資料表（或事實結構描述）包含分析所依據的原始資料或基本資料。 這些主要是大型磁碟區表格（可能有連結表格），可能會有較長的計算。 例如，事實表格可以是：broadlog表格、purchase表格等。

* **Dimension** -Dimension可讓您將資料分割成群組：建立後，維度會作為分析軸。 在大多數情況下，會針對指定維度定義數個層級。 例如，對於暫時維度，層次將為月、日、小時、分鐘等。 這組層級代表維度階層，並可啟用各種層級的資料分析。

* **量化** — 對於某些欄位，您可以定義量化為群組值，使其更容易讀取資訊。 量化會套用至層級。 建議您在可能有許多不同值時定義量化。

* **量值** — 最常見的量值是總和、平均值、最大值、最小值、標準差等。 可以計算度量：例如，優惠的接受率是提供優惠的次數與接受次數的比率。

## Cube工作區 {#cube-workspace}

立方體儲存在&#x200B;**[!UICONTROL Administration > Configuration > Cubes]**&#x200B;節點中。

![](assets/s_advuser_cube_node.png)

立方結構使用的主要內容如下：

* 資料匯出可以直接在Adobe Campaign平台的&#x200B;**[!UICONTROL Reports]**&#x200B;索引標籤中設計的報告中執行。

  要執行此操作，請建立新報表並選取您要使用的立方結構。

  ![](assets/cube_create_new.png)

  立方結構看起來就像範本，根據建立的報表而定。 選擇範本後，按一下&#x200B;**[!UICONTROL Create]**&#x200B;設定並檢視相符的報告。

  您可以調整測量、變更顯示模式或設定表格，然後使用主要按鈕顯示報表。

  ![](assets/cube_display_new.png)

* 您也可以在報告的&#x200B;**[!UICONTROL Query]**&#x200B;方塊中參考Cube，以使用它的指標，如下所示：

  ![](assets/s_advuser_query_using_a_cube.png)

* 您也可以將以立方體為基礎的樞紐分析表插入報表的任何頁面。 若要這麼做，請在相關頁面上參考要在樞紐分析表&#x200B;**[!UICONTROL Data]**&#x200B;索引標籤中使用的Cube。

  ![](assets/s_advuser_cube_in_report.png)

  如需詳細資訊，請參閱[探索報表中的資料](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report)。
