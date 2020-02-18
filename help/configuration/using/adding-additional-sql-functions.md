---
title: 添加其他SQL函式
seo-title: 添加其他SQL函式
description: 添加其他SQL函式
seo-description: null
page-status-flag: never-activated
uuid: d66b5ca2-ac7d-4654-9f0e-9bfe56490c19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 728a95f8-46fe-49a8-a645-a0dd6eeb6615
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 添加其他SQL函式{#adding-additional-sql-functions}

## 簡介 {#introduction}

Adobe Campaign可讓使用者定義 **自己可存取SQL函式的函式** ，包括資料庫提供的函式和控制台中尚未提供的函式。 例如，這對聚合函式（平均、最大、總和）非常有用，只能在伺服器上計算，或者當資料庫提供實現某些函式的更簡單方法時，而不是在控制台中「手動」寫入表達式（如日期管理）。

如果您想要使用Adobe Campaign主控台尚未提供的最近或不常見的資料庫引擎SQL函式，也可以使用此機制。

在新增這些函式後，它們就會像其他預先定義的函式一樣出現在運算式編輯器中。

>[!IMPORTANT]
>
>控制台中的SQL函式調用不再自然地發送到伺服器。 因此，此處介紹的機 **製成為在計畫外** SQL函式伺服器上調用的唯一方法。

## 安裝 {#installation}

要添加的函式以XML格 **式在「包」檔案中**，其結構在以下段落中詳述。

要從控制台進行安裝，請從菜單中選擇「 **Tools/Advanced/Import** （工具／高級／導入）」包選項，然後 **[!UICONTROL Install from file]** 選擇和，並按照導入嚮導中的說明操作。

>[!IMPORTANT]
>
>警告：即使匯入的函式清單立即顯示在函式編輯器中，在Adobe Campaign重新啟動之前，這些函式將無法使用。

## 要導入的包的一般結構 {#general-structure-of-package-to-import}

要添加的函式可在XML格式的「 **package」檔案中找** 到。 以下是範例：

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

* 名 **稱**、命名空間 **** 和標籤 **** ，僅供資訊之用。 它們可讓您在已安裝的軟體包清單中查看軟體包的摘要（Explorer/Administration/Package management/Installed軟體包）。
* buildVersion **和build** Number **** 欄位是必填欄位。 它們必須與控制台所連接的伺服器號相對應。 此資訊可在「說明／關於」方塊中找到。
* 以下塊、實 **體****和基** 元。 在funcList中，「name」和「namespace」欄位是必填欄位，但其名稱由用戶決定，並且它們唯一地指定了函式清單。

   這表示，如果匯入另一個具有相同namespace/name對（此處為&quot;cus::myList&quot;）的函式清單，則先前匯入的函式將會刪除。 相反地，如果更改此namespace/name對，則新的一系列導入函式將添加到上一個函式。

* 組元 **素** 可讓您指定在函式編輯器中顯示所導入函式的函陣列。 @name屬性可以是已存在的名稱（在這種情況下，函式將添加到被考慮的組）或新名稱（在這種情況下，該名稱將出現在新組中）。
* 提醒：元素中@name屬性的可能 `<group>` 值為：

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
>請確定填寫@label屬性：這是將顯示在可用函式清單中的名稱。 如果您未輸入任何內容，則群組將沒有名稱。 不過，如果您輸入的名稱不是現有名稱，則整個群組的名稱將會變更。

如果您想要將函式新增至數個不同群組，可讓同一清單中 `<group>` 的數個元素受到追蹤。

最後，元 `<group>` 素可包含一個或多個函式的定義，即包檔案的目的。 該 `<function>` 要素在以下段落中詳述。

## 函式描述符&lt;function>&lt;/function> {#function-descriptor--function-}

這裡介紹的案例是一個一般案例，我們希望提供功能 **實現**。

以下是&quot;相對成熟度&quot;函式的範例，使用年齡來指出該人被認為成熟的年份。

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

@name **(@name** )欄位引用函式的名稱，「args」是將在說明中顯示的參數清單。 在這種情況下，函式將在函式選擇窗口中顯示為&quot;relativeMaturity( `<age>` )&quot;。

* **help** 是表達式編輯器窗口底部顯示的欄位。
* **@display** 是資訊性訊息。

   >[!NOTE]
   >
   >在@help和@display屬性中，字串&quot;$1&quot;代表第一個函式參數（此處為&quot;Age&quot;）中指定的名稱。 二，三……表示下列參數。 在下面詳細的@body屬性中，$1表示在調用期間傳遞給函式的引數值。

   >[!NOTE]
   >
   >說明必須是有效XML字元的字串：請注意使用&#39;&lt;&#39;和&#39;>&#39;，而非&lt;和>。

* **@type是函式返回類型** ，是標準值(long、string、byte、datetime...)。 如果省略，則伺服器將在實現函式的表達式中確定可用類型的最佳類型。
* **@minArgs** 和 **maxArgs** 指定參數的參數數（最小和最大）。 例如，對於具有2個參數的函式，minArgs和maxArgs將是2和2。 若是3個參數，加上1個可選參數，則分別為3和4。
* 最後， **providerPart元素** 提供了函式實現。

   * provider **屬性** 是必需的，它指定為其提供實施的資料庫系統。 如示例所示，當表達式語法或基礎函式不同時，可以根據資料庫提供替代實現。
   * @body **** 屬性包含函式實現。 請注意：此實作必須是以資料庫語言（而非程式碼區塊）表示的運算式。 根據資料庫，表達式可以是僅返回單個值的子查詢(&quot;（從表中選擇列……）&quot;)。 例如，Oracle中就是這種情況（查詢必須用括弧寫入）。
   >[!NOTE]
   >
   >如果定義的函式可能只查詢一或兩個資料庫，則我們始終只能提供與這些資料庫對應的定義。

## 「直通」函式描述符 {#pass-through--function-descriptor}

特殊函式描述符是「 **傳遞」塊** ，具有未指定的「提供程式」資料庫系統。 在此例中，&quot;body&quot;實作只能包含單一函式呼叫，其語法與所使用的資料庫無關。 同時，「ProviderPart」區塊是唯一的。

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

在這種情況下，添加函式僅用於使資料庫函式成為預設情況下不可用的函式，現在對客戶端可見。

## 範例 {#examples}

在預先定義的套件&quot;xtkdatakitfuncList.xml&quot;中，可找到更多函式範例。
