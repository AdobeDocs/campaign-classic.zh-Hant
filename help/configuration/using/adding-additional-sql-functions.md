---
product: campaign
title: 新增其他 SQL 函式
description: 了解如何定義其他SQL函式
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# 定義其他SQL函式{#adding-additional-sql-functions}

Adobe Campaign可讓使用者定義 **自己的功能** 可訪問SQL函式的SQL函式，包括資料庫提供的函式和控制台中尚未提供的函式。 例如，這對於匯總函式（平均、最大、總和）非常有用，它只能在伺服器上計算，或者當資料庫提供了實現某些函式的更簡單方法時，而不是在控制台中「手動」寫入表達式（例如，日期管理）時。

如果您想使用Adobe Campaign主控台尚未提供的最新或不常見資料庫引擎SQL函式，也可使用此機制。

新增這些函式後，這些函式就會像其他預先定義的函式一樣出現在運算式編輯器中。

>[!IMPORTANT]
>
>主控台中的SQL函式呼叫不再自然傳送至伺服器。 因此，此處所述的機制會變成 **唯一的通話方式** 在計畫外的SQL函式伺服器上。

## 安裝 {#installation}

要新增的函式位於 **XML格式的「包」檔案**，其結構於下段詳述。

若要從主控台安裝，請選取 **工具/進階/匯入套件** 選項，然後 **[!UICONTROL Install from file]** ，並遵循匯入精靈中的指示。

>[!IMPORTANT]
>
>警告：即使匯入的函式清單直接出現在函式編輯器中，但在Adobe Campaign重新啟動前，這些函式將無法使用。

## 要導入的包的一般結構 {#general-structure-of-package-to-import}

若要新增的函式，請參閱 **&quot;package&quot;檔案** 格式。 以下是範例：

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "6.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>
```

* 此 **名稱**, **命名空間** 和 **標籤** 僅供參考。 它們可讓您在已安裝的套件清單（檔案總管/管理/套件管理/已安裝套件）中檢視套件的摘要。
* 此 **buildVersion** 和 **buildNumber** 欄位是必填欄位。 它們必須與控制台所連接的伺服器號相對應。 可在「說明/關於」方塊中找到此資訊。
* 以下是區塊， **實體** 和 **基督** 是必填的。 在funcList中，「name」和「namespace」欄位是必填欄位，但其名稱由用戶自行決定，而它們只能指定函式清單。

   這表示，如果匯入另一個具有相同命名空間/名稱配對（此處為「cus::myList」）的函式清單，則先前匯入的函式將會刪除。 相反地，如果更改此命名空間/名稱對，新的一系列導入函式將添加到前一個函式中。

* 此 **群組** 元素可讓您指定匯入的函式將出現在函式編輯器中的函式群組。 @name屬性可以是已存在的名稱（在這種情況下，函式將添加到考慮的組）或新名稱（在此情況下，它將出現在新組中）。
* 提醒：@name屬性在 `<group>` 元素包括：

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!IMPORTANT]
>
>請務必完成@label屬性：這是將顯示在可用函式清單中的名稱。 如果未輸入任何內容，則組將沒有名稱。 但是，如果輸入的名稱不是現有名稱，則整個組的名稱將更改。

如果您想要將函式新增至數個不同群組，您可以建立數個 `<group>`  元素會在相同清單中受到追蹤。

最後， `<group>` 元素可包含一或多個函式的定義，而此函式是封裝檔案的目的。 此  `<function>`   元素在以下段落中詳細說明。

## 函式描述符 &lt;function>&lt;/function> {#function-descriptor--function-}

本文所介紹的案例是我們希望提供 **函式實現**.

以下是「相對成熟度」函式的範例，其使用年齡來指出該人已被視為成熟的年份。

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

此 **@name** 欄位會參照函式的名稱，而「args」是說明中將顯示的參數清單。 在此情況下，函式會顯示為「relativeMaturity」( `<age>` )」。

* **說明** 是顯示在運算式編輯器視窗底部的欄位。
* **@display** 是資訊性訊息。

   >[!NOTE]
   >
   >在@help和@display屬性中，字串「$1」代表第一個函式參數（此處為「年齡」）中指定的名稱。 $2、$3..表示下列參數。 在以下詳@body的屬性中，$1會指定在呼叫期間傳遞至函式的引數值。

   >[!NOTE]
   >
   >說明必須是有效XML字元的字串：請注意「&lt;」和「>」的用法，而不是&lt;和>。

* **@type** 是函式返回類型，是標準值(long、string、byte、datetime..)。 如果省略，則伺服器會在實作函式的運算式內，決定可用類型中的最佳類型。
* **@minArgs** 和 **maxArgs** 指定參數的參數數（最小和最大）。 例如，對於具有2個參數的函式，minArgs和maxArgs會是2和2。 若為3個參數，加上1個選用項目，則分別為3和4。
* 最後， **providerPart** 元素提供函式實施。

   * 此 **提供者** 屬性是必填的，它指定提供實施的資料庫系統。 如範例所示，當運算式語法或基礎函式不同時，可根據資料庫提供替代實施。
   * 此 **@body** 屬性包含函式實施。 請注意：此實作必須是資料庫語言的運算式（而非程式碼區塊）。 根據資料庫，運算式可以是子查詢(&quot;（從表中選擇列，其中……）&quot;)，僅返回一個值。 例如，Oracle中就是這種情況（查詢必須以方括弧寫入）。

   >[!NOTE]
   >
   >如果定義的函式可能只查詢一個或兩個資料庫，則我們始終只能提供與這些資料庫對應的定義。

## &#39;傳遞&#39;函式描述符 {#pass-through--function-descriptor}

特殊函式描述符為 **&quot;傳遞&quot;** 塊，帶有未指定的「提供程式」資料庫系統。 在此情況下，「body」實作只能包含單一函式呼叫，其語法與使用的資料庫無關。 同時，「ProviderPart」塊是唯一的。

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

在此情況下，新增函式只會讓資料庫函式（預設情況下不可用）變得可見（現在可供用戶端檢視）。

## 範例 {#examples}

可在預先定義的套件&quot;xtkdatakitfuncList.xml&quot;中找到更多函式範例。
