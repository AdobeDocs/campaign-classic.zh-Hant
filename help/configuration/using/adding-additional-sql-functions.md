---
product: campaign
title: 新增其他 SQL 函式
description: 瞭解如何定義其他SQL函式
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 0%

---

# 定義其他SQL函式{#adding-additional-sql-functions}

Adobe Campaign可讓使用者定義可存取SQL函式的&#x200B;**自己的函式**，包括資料庫所提供的函式以及主控台中尚未提供的函式。 例如，這對於彙總函式(average、maximum、sum)非常有用，這些函式只能在伺服器上計算，或者在資料庫提供更簡單的方式實作某些函式時，才可以計算，而不是在主控台中「手動」寫入運算式（例如日期管理）。

如果您想要使用最近使用或不常見的資料庫引擎SQL函式(Adobe Campaign主控台尚未提供)，也可以使用此機制。

新增這些函式後，就會像其他預先定義的函式一樣顯示在運算式編輯器中。

>[!IMPORTANT]
>
>主控台中的SQL函式呼叫不再自然傳送至伺服器。 因此，此處說明的機制會成為&#x200B;**在計畫外的SQL函式伺服器上呼叫**&#x200B;的唯一方法。

## 安裝 {#installation}

要新增的函式位於XML格式&#x200B;**的**&quot;package&quot;檔案中，其結構詳見以下段落。

若要從主控台安裝，請從功能表選取&#x200B;**工具/進階/匯入套件**&#x200B;選項，然後選取&#x200B;**[!UICONTROL Install from file]**，然後依照匯入小幫手中的指示進行。

>[!IMPORTANT]
>
>警告：即使匯入的函式清單會立即顯示在函式編輯器中，Adobe Campaign重新啟動後才能使用。

## 要匯入的封裝的一般結構 {#general-structure-of-package-to-import}

可以在&#x200B;**「封裝」檔案**&#x200B;中找到XML格式要新增的函式。 範例如下：

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

* **名稱**、**名稱空間**&#x200B;和&#x200B;**標籤**&#x200B;僅供參考。 它們可讓您檢視已安裝套件清單（總管/管理/套件管理/已安裝套件）中的套件摘要。
* **buildVersion**&#x200B;和&#x200B;**buildNumber**&#x200B;欄位是必要的。 它們必須對應至主控台所連線的伺服器編號。 此資訊可在「說明/關於」方塊中找到。
* 下列區塊、**實體**&#x200B;和&#x200B;**運算式清單**&#x200B;是必要的。 在funcList中，「name」和「namespace」欄位是必填欄位，但它們的名稱由使用者決定，而且它們會唯一指定函式清單。

  這表示如果匯入另一個具有相同名稱空間/名稱組的函式清單（這裡為「cus：：myList」），則會刪除先前匯入的函式。 相反地，如果您變更此名稱空間/名稱組，新的一系列匯入函式將會新增到上一個函式中。

* **群組**&#x200B;元素可讓您指定匯入的函式將在函式編輯器中出現的函式群組。 @name屬性可以是已經存在的名稱（在此情況下，函式將新增到考慮的群組中）或新名稱（在此情況下，它將顯示在新群組中）。
* 提醒： `<group>`元素中@name屬性的可能值是：

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
>請務必完成@label屬性：這是將顯示在可用函式清單中的名稱。 如果您未輸入任何內容，群組就沒有名稱。 但是，如果您輸入現有名稱以外的名稱，則整個群組的名稱將會變更。

如果您想要將函式新增至數個不同的群組，您可以讓數個`<group>`元素在同一個清單中受到追蹤。

最後，`<group>`元素可以包含一或多個函式的定義，這是封裝檔案的目的。 `<function>`   元素詳見下段。

## 函式描述項&lt;function>&lt;/function> {#function-descriptor--function-}

這裡呈現的案例是我們希望提供&#x200B;**函式實作**&#x200B;的一般案例。

以下是「相對成熟」函式的範例，此函式使用年齡表示該人員被視為成熟的年數。

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

**@name**&#x200B;欄位參考函式的名稱，而「args」是將顯示在說明中的引數清單。 在這種情況下，函式會在函式選取視窗中顯示為「relativeMaturity ( `<age>` )」。

* **help**&#x200B;是運算式編輯器視窗底部顯示的欄位。
* **@display**&#x200B;是資訊訊息。

  >[!NOTE]
  >
  >在@help和@display屬性中，字串「$1」代表在第一個函式引數（此處為「Age」）中指定的名稱。 $2、$3...代表下列引數。 在下面詳述的@body屬性中，$1會指定呼叫期間傳遞至函式的引數值。

  >[!NOTE]
  >
  >說明必須是有效XML字元的字串：請注意，使用&#39;&lt;&#39;和&#39;>&#39;而非&lt;和>。

* **@type**&#x200B;是函式傳回型別，是標準值(long、string、byte、datetime...)。 如果省略，伺服器會在實作函式的運算式中，決定可用型別中最佳型別。
* **@minArgs**&#x200B;和&#x200B;**maxArgs**&#x200B;指定引數的引數數目（最小值和最大值）。 例如，若是有2個引數的函式，minArgs和maxArgs將分別為2和2。 若為3個引數加上1個選用引數，則分別為3個和4個。
* 最後，**providerPart**&#x200B;元素提供函式實作。

   * **provider**&#x200B;屬性是必要的，它指定提供實作的資料庫系統。 如範例所示，當運算式語法或基礎函式不同時，可以根據資料庫提供替代實作。
   * **@body**&#x200B;屬性包含函式實作。 請注意：此實作必須是資料庫語言的運算式（不是程式碼區塊）。 視資料庫而定，運算式可以是隻傳回單一值的子查詢(&quot;（從表格中選取資料行，其中……）&quot;)。 例如，Oracle就是這種情況（查詢必須用方括弧撰寫）。

  >[!NOTE]
  >
  >如果定義的函式可能只查詢一或兩個資料庫，我們永遠只能提供對應到這些資料庫的定義。

## &#39;Pass-through&#39;函式描述項 {#pass-through--function-descriptor}

特殊函式描述項是&#x200B;**&quot;pass-through&quot;**&#x200B;區塊，包含未指定的&quot;provider&quot;資料庫系統。 在這種情況下，「body」實作只能包含具有語法的單一函式呼叫，且該語法與使用的資料庫無關。 同時，「ProviderPart」區塊是唯一的。

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

在這種情況下，新增函式只能讓預設情況下無法使用的資料庫函式，現在可供使用者端使用。

## 範例 {#examples}

在預先定義的套件「xtkdatakitfuncList.xml」中可以找到進一步的函式範例。
