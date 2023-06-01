---
product: campaign
title: 新增其他 SQL 函式
description: 瞭解如何定義其他SQL函式
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# 定義其他SQL函式{#adding-additional-sql-functions}

Adobe Campaign可讓使用者定義 **他們自己的函式** 可以存取SQL函式（包括資料庫提供的SQL函式，以及主控台中尚未提供的SQL函式）。 這對彙總函式（平均、最大值、和）非常有用，例如，彙總函式只能在伺服器上計算，或是資料庫提供較容易實作特定函式的方式，而不是「手動」在主控台中寫入運算式（例如日期管理）時。

如果您想要使用最近或不常見的資料庫引擎SQL函式(Adobe Campaign主控台尚未提供)，也可以使用此機制。

新增這些函式後，它們就會像其他預先定義的函式一樣顯示在運算式編輯器中。

>[!IMPORTANT]
>
>主控台中的SQL函式呼叫不再自然傳送至伺服器。 因此，此處說明的機制會變成 **唯一可以呼叫的方式** 在計畫外的SQL函式伺服器上。

## 安裝 {#installation}

要新增的函式位於 **XML格式的&quot;package&quot;檔案**，其結構於以下段落中詳細說明。

若要從主控台安裝，請選取 **工具/進階/匯入套件** 選單中的選項，然後 **[!UICONTROL Install from file]** ，並依照匯入精靈中的指示操作。

>[!IMPORTANT]
>
>警告：即使匯入的函式清單立即顯示在函式編輯器中，Adobe Campaign重新啟動後才能使用。

## 要匯入的封裝的一般結構 {#general-structure-of-package-to-import}

欲新增的函式可在以下網址找到： **&quot;package&quot;檔案** XML格式。 範例如下：

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "7.1"
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

* 此 **名稱**， **名稱空間** 和 **標籤** 僅供參考。 它們可讓您檢視已安裝套件清單（總管/管理/套件管理/已安裝套件）中的套件摘要。
* 此 **buildVersion** 和 **buildNumber** 欄位為必填欄位。 它們必須對應至主控台所連線的伺服器號碼。 此資訊可在「說明/關於」方塊中找到。
* 下列區塊， **實體** 和 **功能表** 為必填欄位。 在funcList中，「name」和「namespace」欄位是必填欄位，但其名稱由使用者決定，而且這些欄位會唯一指定函式清單。

   這表示如果匯入另一個具有相同名稱空間/名稱配對的函式清單（這裡為「cus：：myList」），則會刪除先前匯入的函式。 相反地，如果您變更此名稱空間/名稱組，新的一系列匯入函式將會新增到上一個函式中。

* 此 **群組** element可讓您指定匯入的函式會顯示在函式編輯器中的函式群組。 @name屬性可以是已經存在的名稱（在此情況下，函式將新增到所考慮的群組中）或新名稱（在此情況下，它將顯示在新群組中）。
* 提醒：中可能為@name屬性的值 `<group>` 元素為：

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
>請務必完成@label屬性：這是將顯示在可用函式清單中的名稱。 如果您未輸入任何內容，群組將不會有名稱。 但是，如果您輸入現有名稱以外的名稱，則整個群組的名稱將會變更。

如果您想要將函式新增至數個不同的群組，您可以建立數個群組 `<group>`  元素會在相同清單中受到追蹤。

最後， `<group>` 元素可以包含一或多個函式的定義，這是套件檔案的目的。 此  `<function>`   元素詳見以下段落。

## 函式描述項 &lt;function>&lt;/function> {#function-descriptor--function-}

這裡呈現的案例是通用案例，我們在此提供 **函式實作**.

以下是「相對成熟」函式的範例，此函式使用年齡指出個人被視為成熟的年數。

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

此 **@name** 欄位會參照函式的名稱，而「args」是將顯示在說明中的引數清單。 在此情況下，函式會顯示為「relativeMaturity ( `<age>` )」。

* **說明** 是顯示在運算式編輯器視窗底部的欄位。
* **@display** 是資訊訊息。

   >[!NOTE]
   >
   >在@help和@display屬性中，字串「$1」代表第一個函式引數（此處為「Age」）中提供的名稱。 $2、$3...代表下列引數。 在下面詳述的@body屬性中，$1會指定在呼叫期間傳遞至函式的引數值。

   >[!NOTE]
   >
   >說明必須是有效XML字元的字串：請注意，使用&#39;&lt;&#39;和&#39;>&#39;而不是&lt;和>。

* **@type** 是函式傳回型別，是標準值(long、string、byte、datetime...)。 如果省略，伺服器會在實作函式的運算式中決定可用型別中的最佳型別。
* **@minArgs** 和 **maxArgs** 指定引數的引數數目（最小值和最大值）。 例如，對於具有2個引數的函式，minArgs和maxArgs將分別為2和2。 若為3個引數加上1個選用引數，則分別為3個和4個。
* 最後， **providerPart** element提供函式實作。

   * 此 **提供者** 屬性是強制的，它會指定提供實作的資料庫系統。 如範例所示，當運算式語法或基礎函式不同時，可以根據資料庫提供替代實作。
   * 此 **@body** 屬性包含函式實作。 請注意：此實作必須是資料庫語言的運算式（不是程式碼區塊）。 視資料庫而定，運算式可以是隻傳回單一值的子查詢(&quot;（從表格中選取資料行……）&quot;)。 例如，這是Oracle的情況（查詢必須寫在方括弧中）。

   >[!NOTE]
   >
   >如果定義的函式可能只查詢一或兩個資料庫，我們一律可以只提供與這些資料庫對應的定義。

## &#39;Pass-through&#39;函式描述項 {#pass-through--function-descriptor}

一個特殊的函式描述元是 **&quot;pass-through&quot;** 區塊，使用未指定的「提供者」資料庫系統。 在此情況下，「body」實作只能包含單一函式呼叫，且語法與所使用的資料庫無關。 同時，「ProviderPart」區塊是唯一的。

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

在此情況下，新增函式僅能讓預設情況下無法使用的資料庫函式，現在可供使用者端使用。

## 範例 {#examples}

進一步函式範例可在預先定義的套件「xtkdatakitfuncList.xml」中找到。
