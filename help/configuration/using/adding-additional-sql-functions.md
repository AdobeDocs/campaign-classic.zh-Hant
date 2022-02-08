---
product: campaign
title: 新增其他 SQL 函式
description: 瞭解如何定義其他SQL函式
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# 定義其他SQL函式{#adding-additional-sql-functions}

![](../../assets/v7-only.svg)

Adobe Campaign允許用戶定義 **自己的功能** 可以訪問SQL函式的SQL函式，包括資料庫提供的函式和控制台中尚未提供的函式。 這對於聚合函式（平均、最大值、總和）很有用，例如，只有在伺服器上或資料庫提供了實現某些函式的更簡單方法時，才能計算這些函式，而不是在控制台中「手動」寫入表達式（如日期管理）。

如果您想使用Adobe Campaign控制台尚未提供的最近或不常見的資料庫引擎SQL函式，也可以使用此機制。

添加這些函式後，它們將像其他預定義函式一樣顯示在表達式編輯器中。

>[!IMPORTANT]
>
>控制台中的SQL函式調用不再自然地發送到伺服器。 因此，此處描述的機制 **唯一的方法** 意外的SQL函式伺服器上。

## 安裝 {#installation}

要添加的函式位於 **XML格式的&quot;package&quot;檔案**&#x200B;其結構詳見下段。

要從控制台安裝它，請選擇 **工具/高級/導入包** 選項，然後 **[!UICONTROL Install from file]** ，並按照導入嚮導中的說明進行操作。

>[!IMPORTANT]
>
>警告：即使導入的函式清單直接出現在函式編輯器中，但在Adobe Campaign重新啟動之前，它們將無法使用。

## 要導入的包的一般結構 {#general-structure-of-package-to-import}

要添加的函式可在 **&quot;包&quot;檔案** 的子菜單。 下面是一個示例：

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

* 的 **名稱**。 **命名空間** 和 **標籤** 僅供參考。 它們允許您在已安裝的軟體包清單（Explorer/Administration/Package management/Installed軟體包）中查看軟體包的摘要。
* 的 **buildVersion** 和 **buildNumber（內部編號）** 欄位為必填項。 它們必須與控制台所連接的伺服器號相對應。 此資訊可在「幫助/關於」框中找到。
* 以下幾塊， **實體** 和 **葬禮** 的子菜單。 在funcList中，欄位&quot;name&quot;和&quot;namespace&quot;是必需的，但其名稱由用戶決定，它們唯一地指定函式清單。

   這意味著，如果導入了具有相同命名空間/名稱對（此處為「cus::myList」）的另一個函式清單，則先前導入的函式將被刪除。 相反，如果更改此命名空間/名稱對，則新的一系列導入函式將添加到前一個函式。

* 的 **組** 「元素」(element)，用於指定導入的函式將出現在函式編輯器中的函陣列。 @name屬性可以是已存在的名稱（在此情況下，函式將添加到考慮的組），也可以是新名稱（在此情況下，函式將出現在新組中）。
* 提醒：中@name屬性的可能值 `<group>` 元素為：

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
>確保完成@label屬性：這是將顯示在可用函式清單中的名稱。 如果您未輸入任何內容，則組將沒有名稱。 但是，如果輸入的名稱不是現有名稱，則整個組的名稱將更改。

如果要向多個不同的組添加函式，可以建立多個 `<group>`  元素將在同一清單中跟蹤。

最後， `<group>` 元素可以包含一個或多個函式的定義，這些函式是包檔案的目的。 的  `<function>`   元素詳見下段。

## 函式描述符 &lt;function>&lt;/function> {#function-descriptor--function-}

這裡介紹的案例是我們希望提供 **函式實現**。

下面是&quot;相對成熟度&quot;函式的示例，該函式使用年齡來表示該人被視為成熟的年份。

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

的 **@name** 欄位引用函式的名稱，而「args」是將在說明中顯示的參數清單。 在這種情況下，該函式將顯示為「relativeMaturity( `<age>` )。

* **幫助** 是表達式編輯器窗口底部顯示的欄位。
* **@display** 是一條資訊性資訊。

   >[!NOTE]
   >
   >在@help和@display屬性中，字串「$1」表示在第一個函式參數（此處為「Age」）中指定的名稱。 2美元，3美元……表示以下參數。 在下面詳細的@body屬性中，$1指定在調用期間傳遞給函式的參數值。

   >[!NOTE]
   >
   >說明必須是包含有效XML字元的字串：請注意使用「&lt;」和「>」而不是&lt;和>。

* **@type** 是函式返回類型，是標準值(long、string、byte、datetime...)。 如果省略，伺服器將確定實現該函式的表達式中可用類型中的最佳類型。
* **@minArgs** 和 **maxArgs** 指定參數的參數數（最小和最大）。 例如，對於具有2個參數的函式，minArgs和maxArgs將是2和2。 對於3個參數，加上1個可選參數，它們將分別為3和4。
* 最後， **providerPart** 元素提供函式實現。

   * 的 **提供程式** 屬性是必需的，它指定為其提供實現的資料庫系統。 如示例所示，當表達式語法或基礎函式不同時，可以根據資料庫提供替代實現。
   * 的 **@body** 屬性包含函式實現。 請注意：此實現必須是以資料庫語言（而不是代碼塊）表示的表達式。 根據資料庫的不同，表達式可以是子查詢(「（從表中選擇列，其中……）」)，只返回一個值。 例如，Oracle中就是這種情況（查詢必須寫在方括弧中）。

   >[!NOTE]
   >
   >如果定義的函式可能只查詢一兩個資料庫，則我們始終只能提供與這些資料庫對應的定義。

## 「傳遞」函式描述符 {#pass-through--function-descriptor}

一個特殊的函式描述符是 **&quot;傳遞&quot;** 塊，具有未指定的「provider」資料庫系統。 在這種情況下，&quot;body&quot;實現只能包含一個語法與所使用的資料庫無關的函式調用。 同時，「ProviderPart」塊是唯一的。

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

在這種情況下，添加函式僅用於使預設情況下不可用的資料庫函式（現在對客戶端可見）。

## 範例 {#examples}

在預定義的包&quot;xtkdatakitfuncList.xml&quot;中可找到更多函式示例。
