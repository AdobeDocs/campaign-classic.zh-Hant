---
solution: Campaign Classic
product: campaign
title: 定義篩選條件
description: 定義篩選條件
audience: platform
content-type: reference
topic-tags: creating-queries
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '3229'
ht-degree: 37%

---


# 定義篩選條件{#defining-filter-conditions}

## 選擇運算子{#choosing-the-operator}

在篩選條件中，您需要使用運算子將兩個值連結在一起。

![](assets/query_editor_nveau_96.png)

以下是可用運算子的清單：

<table> 
 <thead> 
  <tr> 
   <th> 運算元<br /> </th> 
   <th> 目的<br /> </th> 
   <th> 範例 <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Equal to</span> <br /> </td> 
   <td> 傳回與在第二個值欄中輸入的資料相同的結果。<br /> </td> 
   <td> <strong>姓氏(@lastName)等於'Jones'</strong>，將只傳回姓氏為Jones的收件者。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Greater than</span> <br /> </td> 
   <td> 傳回大於輸入值的值。<br /> </td> 
   <td> <strong>年齡(@age)大於50</strong>，將傳回所有大於'50'的值，即「51」、「52」等。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Less than</span> <br /> </td> 
   <td> 傳回小於輸入值的值。<br /> </td> 
   <td> <strong>在'DaysAgo(100)'之前建立日期(@created)</strong>，將會傳回所有在100天前建立的收件者。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Greater than or equal to</span> <br /> </td> 
   <td> 傳回等於或大於輸入值的所有值。<br /> </td> 
   <td> <strong>年齡(@age)大於或等於'30'</strong>，將傳回所有30歲以上的收件者。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Less than or equal to</span> <br /> </td> 
   <td> 傳回等於或低於輸入值的所有值。<br /> </td> 
   <td> <strong>年齡(@age)小於或等於'60'</strong>，將傳回所有60歲或以下的收件者。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不等於</span> <br /> </td> 
   <td> 傳回與輸入值不相同的所有值。<br /> </td> 
   <td> <strong>語言(@language)等於'English'</strong>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">開始於</span> <br /> </td> 
   <td> 傳回以輸入值開始的結果。<br /> </td> 
   <td> <strong>帳戶#(@account)以'32010'開頭。</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不以</span> <br /> </td> 
   <td> 傳回結果，不以輸入值<br />開始 </td> 
   <td> <strong>帳戶#(@account)不以'20'開頭</strong>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Contains</span> <br /> </td> 
   <td> 傳回至少包含輸入值的結果。<br /> </td> 
   <td> <strong>電子郵件網域(@domain)包含'mail'</strong>，將傳回所有包含'mail'的網域名稱。因此，'gmail.com'網域也會傳回。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不包含</span> <br /> </td> 
   <td> 傳回不含輸入值的結果。<br /> </td> 
   <td> <strong>電子郵件網域(@domain)不包含'vo'</strong>。在此情況下，不會傳回包含'vo'的網域名稱。 'voila.fr'網域名稱不會出現在結果中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Like</span> <br /> </td> 
   <td> <span class="uicontrol">Like</span> 與　<span class="uicontrol">Contains</span>　運算子非常類似。它可讓您在值中插入<span class="uicontrol">%</span>萬用字元。<br /> </td> 
   <td> <strong>姓氏(@lastName)，如「Jon%s」</strong>。在這裡，萬用字元會當做「小丑」來尋找"Jones"，如果運算子忘記'n'和's'之間遺失的字母，則會使用此字元尋找"Jones"。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Not like</span> <br /> </td> 
   <td> 類似 <span class="uicontrol">Like</span>。可讓您不復原輸入的值。 在這裡，輸入的值也必須包含 <span class="uicontrol">%</span> 萬用字元。<br /> </td> 
   <td> <strong>姓氏(@lastName)與'Smi%h'不同</strong>。在此，不會傳回姓氏為'Smi%h'的收件者。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Is empty</span> <br /> </td> 
   <td> 在這種情況下，我們尋找的結果與第二個「值」欄中的空值相符。<br /> </td> 
   <td> <strong>行動(@mobilePhone)會傳</strong> 回所有沒有行動號碼的收件者。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不為空</span> <br /> </td> 
   <td> 與<span class="uicontrol">Is empty</span>運算子相反。 無需在第二個值列中輸入資料。<br /> </td> 
   <td> <strong>電子郵件(@email)不為空</strong>。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">包含在</span> <br /> </td> 
   <td> 傳回包含在指定值中的結果。 這些值必須以逗號分隔。<br /> </td> 
   <td> <strong>出生日期(@birthDate)包含在'12/10/1979,12/10/1984'中</strong>，將會傳回在這些日期之間出生的收件者。  <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">不包含在</span> <br /> </td> 
   <td> 類似<span class="uicontrol">Is included in </span>運算子的作用。 在此，我們要根據輸入的值排除收件者。<br /> </td> 
   <td> <strong>出生日期(@birthDate)不包含在'12/10/1979,12/10/1984'中</strong>。與上例不同，在這些日期內出生的收件者將不會傳回。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 使用AND、OR，但{#using-and--or--except}除外

對於使用多個篩選條件的查詢，您需要定義條件之間的連結。 有三個可能的連結：

* **[!UICONTROL And]** 可讓您結合兩個篩選條件，
* **[!UICONTROL Or]** 讓你提供另一種選擇，
* **[!UICONTROL Except]** 可讓您定義例外。

按一下&#x200B;**[!UICONTROL And]**（預設提供）並從下拉式清單中選擇。

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**:新增條件並啟用過濾。
* **[!UICONTROL Or]**:新增條件並啟用過濾。

   下列範例可讓您尋找電子郵件網域包含「orange.co.uk」或其貼文程式碼以「NW」開頭的收件者。

   ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**:如果您有兩個篩選器，而第一個篩選器未傳回值，此類型的連結會建立例外。

   在下列範例中，我們要傳回其電子郵件網域包含「orange.co.uk」的收件者，除非收件者的姓氏是「Smith」。

   ![](assets/query_condition_modif_03.png)

此範例顯示可讓您顯示的篩選：會說西班牙文或OR的收件者是具有行動號碼的女性，或沒有帳號且公司名稱以字母&quot;N&quot;開頭的收件者。

![](assets/query_editor_nveau_31.png)

## 排定條件{#prioritizing-conditions}優先順序

本節說明如何利用工具列中的藍色箭頭來排列條件的優先順序。

* 向右箭頭可讓您在篩選器中新增一級括弧。
* 指向左側的箭頭可讓您從篩選器中刪除選取的括弧層級。

   ![](assets/query_condition_modif_04.png)

* 垂直箭頭可讓您移動條件，從而更改其執行順序。

此示例說明如何使用箭頭刪除括弧層。 從下列篩選條件開始：**[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**。

將游標置於&#x200B;**[!UICONTROL Gender (@gender) equal to Male]**&#x200B;過濾條件上，然後按一下&#x200B;**[!UICONTROL Remove a parenthesis level]**&#x200B;箭頭。

![](assets/query_editor_nveau_32.png)

**[!UICONTROL Gender (@gender) equal to Male]**&#x200B;條件已從括弧中取出。 它已經向「倫敦金融城與倫敦相當」的水準邁進。 這些條件會連結在一起(**[!UICONTROL And]**)。

## 選擇要提取{#selecting-data-to-extract}的資料

可用欄位因表格而異。 所有欄位都儲存在稱為&#x200B;**[!UICONTROL Main element]**&#x200B;的主節點中。 在以下範例中，可用欄位位於收件者表格中。 欄位一律以字母順序顯示。

所選欄位的詳細資訊在窗口底部可見。 例如，**[!UICONTROL Email domain]**&#x200B;欄位是&#x200B;**[!UICONTROL Calculated SQL field]**，其延伸名為&#x200B;**[!UICONTROL (@domain)]**。

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>使用&#x200B;**[!UICONTROL Search]**&#x200B;工具尋找可用欄位。

連按兩下可用欄位，將其新增至輸出欄。 在查詢結束時，每個選定欄位都會在&#x200B;**[!UICONTROL Data preview]**&#x200B;窗口中建立一列。

![](assets/query_editor_nveau_01.png)

預設不會顯示進階欄位。 按一下可用欄位右下角的&#x200B;**[!UICONTROL Display advanced fields]**&#x200B;以顯示所有項目。 再按一下以返回前一個檢視。

例如，在收件者表格中，進階欄位為&#x200B;**Boolean 1**、**[!UICONTROL Boolean 2]**、**[!UICONTROL Boolean 3]**、**[!UICONTROL Foreign key of "Folder" link]**&#x200B;等。

以下示例顯示收件人表的高級欄位。

![](assets/query_editor_nveau_53.png)

各種欄位類別：

<table> 
 <thead> 
  <tr> 
   <th> 圖示<br /> </th> 
   <th> 說明<br /> </th> 
   <th> 範例<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> 簡單欄位<br /> </td> 
   <td> 電子郵件、性別等。<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> 主鍵。 此SQL欄位是標識表中記錄的方法。<br /> </td> 
   <td> 識別碼收件者是主要的金鑰，而識別碼依定義是唯一的。<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> 外鍵。 用作指向另一個表的連結。<br /> </td> 
   <td> 接收方外鍵、服務外鍵等。<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> 計算欄位。 此類型的欄位是使用資料庫中的值在請求時計算的。<br /> </td> 
   <td> 年齡、電子郵件網域等。<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> 包含長文本的欄位。<br /> </td> 
   <td> 注釋、完整地址等。<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> 索引的SQL欄位。<br /> </td> 
   <td> 完整名稱、ISO程式碼等<br /> </td> 
  </tr> 
 </tbody> 
</table>

連結至表格和系列元素：

<table> 
 <thead> 
  <tr> 
   <th> 圖示<br /> </th> 
   <th> 說明<br /> </th> 
   <th> 範例 <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> 特別是表的連結。 這些關聯與1-1類型關聯一致。 源表的具體值只能與目標表的一個具體值一致。 例如，只能將一個收件者連結至國家。<br /> </td> 
   <td> 資料夾、狀態、國家等<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> 特定表格上的收集元素。 這些關聯與1-N類型關聯一致。 一個源表實例可以與目標表的幾個實例重合，但目標表的一個實例只能與源表的一個實例重合。 例如，一個收件者可以訂閱'n'訂閱字母。<br /> </td> 
   <td> 訂閱、清單、排除記錄檔等。<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* 使用&#x200B;**[!UICONTROL Add]**&#x200B;按鈕（位於側表徵圖欄上方）添加要編輯表達式的輸出列。 有關編輯表達式的詳細資訊，請參閱[ Building expressions](#building-expressions)。
>* 按一下紅色的「x」(**Delete**)，以刪除輸出欄。
>* 使用箭頭更改輸出列的順序。
>* **[!UICONTROL Distribution of values]**&#x200B;可作為查看所選欄位值的分佈（例如，連結到接收城鎮、接收人語言等的分佈）的方式。


## 建立計算欄位{#creating-calculated-fields}

如有必要，請在資料格式化期間新增欄。 計算欄位會新增欄至資料預覽區段。 按一下 **[!UICONTROL Add a calculated field]**。

![](assets/query_editor_nveau_43.png)

有四種類型的計算欄位：

* **[!UICONTROL Fixed string]**:可讓您新增字元字串。

   ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**:計算欄位的值會結合字元字串和JavaScript指令。

   ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**:計算欄位的值是JavaScript函式評估的結果。可輸入傳回的值（數字、日期等）。

   ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**:此類型的欄位可讓您使用／修改新欄中其中一個輸出欄的內容。

   可以使用列的源值並為其指定目標值。 此目標值將顯示在新輸出列中。

   有關添加計算欄位類型&#x200B;**[!UICONTROL Enumerations]**&#x200B;的示例，請參閱[本節](../../workflow/using/adding-enumeration-type-calculated-field.md)。

   ![](assets/query_editor_nveau_63.png)

   **[!UICONTROL Enumerations]**&#x200B;類型計算欄位可包含4個條件：

   * **[!UICONTROL Keep the source value]** 將源值還原到目標，而不進行更改。
   * **[!UICONTROL Use the following value]** 可讓您輸入未定義來源值的預設目標值。
   * **[!UICONTROL Generate a warning and continue]** 警告用戶源值無法更改。
   * **[!UICONTROL Generate an error and reject the line]** 防止計算和導入行。

按一下&#x200B;**[!UICONTROL Detail of calculated field]**&#x200B;查看插入欄位的詳細資訊。

若要移除此計算欄位，請按一下&#x200B;**[!UICONTROL Remove the calculated field]**&#x200B;交叉點。

![](assets/query_editor_nveau_58.png)

## 建立運算式{#building-expressions}

運算式編輯工具可讓您計算匯整、產生函式，或使用運算式編輯公式。

以下示例說明如何對主鍵運行計數。

應用以下步驟：

1. 按一下&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中的&#x200B;**[!UICONTROL Add]**。 在&#x200B;**[!UICONTROL Formula type]**&#x200B;窗口中，選擇要輸入表達式的公式類型。

   可用的公式有幾種類型：**[!UICONTROL Field only]**、**[!UICONTROL Aggregate]**、**[!UICONTROL Expression]**。

   選擇&#x200B;**[!UICONTROL Process on an aggregate function]**&#x200B;和&#x200B;**[!UICONTROL Count]**。按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/query_editor_nveau_54.png)

1. 計算主鍵。

   ![](assets/query_editor_nveau_88.png)

以下是&#x200B;**[!UICONTROL Formula types]**&#x200B;視窗中可用選項的詳細檢視：

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** 讓您返回視 **[!UICONTROL Field to select]** 窗。
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**.以下是匯整使用的一些範例：

   * **[!UICONTROL Count]** 可讓您執行主要金鑰計數。
   * **[!UICONTROL Sum]** 可讓您將客戶在一年以上進行的所有購買加總。
   * **[!UICONTROL Maximum value]** 可讓您尋找購買最多「n」個產品的客戶。
   * **[!UICONTROL Minimum value]** 可讓您排序客戶，並尋找最近訂閱過優惠的客戶。
   * **[!UICONTROL Average]**.此函式可讓您計算收件者的平均年齡。

      **[!UICONTROL Distinct]**&#x200B;方塊可讓您恢復列的唯一值和非零值。 例如，您可以復原收件者的所有追蹤記錄檔，而這些追蹤記錄檔會變更為值1，因為這些記錄檔都與相同的收件者有關。

1. **[!UICONTROL Expression]** 開啟窗 **[!UICONTROL Edit the expression]** 口。這可讓您偵測到數字過多的電話號碼，可能是輸入錯誤。

   ![](assets/query_editor_nveau_71.png)

   有關所有可用函式的清單，請參閱[函式清單](#list-of-functions)。

## 函式清單 {#list-of-functions}

如果選擇&#x200B;**[!UICONTROL Expression]**&#x200B;類型公式，則會進入「編輯表達式」窗口。 各種函式類別可關聯至可用欄位：**[!UICONTROL Aggregates]**、**[!UICONTROL String]**、**[!UICONTROL Date]**、**[!UICONTROL Numerical]**、**[!UICONTROL Currency]**、**[!UICONTROL Geomarketing]**、**[!UICONTROL Windowing function]**&#x200B;和&#x200B;**[!UICONTROL Others]**。

運算式編輯器的外觀如下：

![](assets/s_ncs_user_filter_define_expression.png)

它可讓您選擇資料庫表格中的欄位，並新增進階函式。 下列功能可供使用：

**彙總**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>語法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>平均</strong><br /> </td> 
   <td> 返回數字類型列的平均值<br /> </td> 
   <td> Avg(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>計數</strong><br /> </td> 
   <td> 計算列<br />的非空值 </td> 
   <td> Count(&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> 計算傳回的值（所有欄位）<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Countdistinct</strong><br /> </td> 
   <td> 計算列<br />的不同非空值 </td> 
   <td> Countdistinct(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>最大值</strong><br /> </td> 
   <td> 傳回數字、字串或日期類型欄的最大值<br /> </td> 
   <td> Max(&lt;value&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>最小</strong><br /> </td> 
   <td> 傳回數字、字串或日期類型欄<br />的最小值 </td> 
   <td> Min(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> 傳回數字、字串或日期欄的標準差<br /> </td> 
   <td> StdDev(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>總和</strong><br /> </td> 
   <td> 傳回數字、字串或日期類型欄值之和<br /> </td> 
   <td> Sum(&lt;value&gt;)<br /></td> 
  </tr> 
 </tbody> 
</table>

**String**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>語法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> 指示所有參數是否為非空值且非空白<br /> </td> 
   <td> AllNonNull2(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> 指示所有參數是否為非空值且非空白<br /> </td> 
   <td> AllNonNull3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> 傳回字串中第一個字元的　ASCII　值.<br /> </td> 
   <td> Ascii(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> 傳回與　'n' ASCII　代碼對應的字元<br /> </td> 
   <td> 字元(&lt;number&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> 傳回字串　1　中字串　2　的位置.<br /> </td> 
   <td> Charindex(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> 傳回字串的第　n　行（從　1　到　n）<br /> </td> 
   <td> GetLine(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> 如果前兩個參數相等，則傳回第三個參數。 否則，返回最後一個參數<br /> </td> 
   <td> IfEquals(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> 指示作為參數傳遞的備忘錄是否為空<br /> </td> 
   <td> IsMemoNull(&lt;memo&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> 串連作為參數傳遞的字串。 在字串之間添加空格（如有必要）。<br /> </td> 
   <td> JuxtWords(&lt;string&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> 串連作為參數傳遞的字串。 如有必要，在字串之間添加空格<br /> </td> 
   <td> JuxtWords3(&lt;string&gt;, &lt;string&gt;, &lt;string&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> 傳回左側的已完成字串<br /> </td> 
   <td> LPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> 傳回字串的前　n　個字元<br /> </td> 
   <td> Left(&lt;string&gt;, &lt;number&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> 傳回字串長度<br /> </td> 
   <td> Length(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> 傳回小寫字串<br /> </td> 
   <td> Lower(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> 移除字串左側的空格<br /> </td> 
   <td> Ltrim(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> 返回字串　MD5　鍵的十六進位表示<br /> </td> 
   <td> Md5Digest(&lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> 指定備忘錄是否包含作為參數傳遞的字串<br /> </td> 
   <td> MemoContains(&lt;memo&gt;, &lt;string&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> 傳回右側的已完成字串<br /> </td> 
   <td> RPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> 傳回字串的最後　n　個字元<br /> </td> 
   <td> Right(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> 移除字串右側的空格<br /> </td> 
   <td> Rtrim(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> 傳回字串，每個字詞的首字母以大寫表示<br /> </td> 
   <td> Smart(&lt;string&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> 從字串的字元n1和長度n2<br />開始提取子字串 </td> 
   <td> Substring(&lt;string&gt;, &lt;offset&gt;, &lt;length&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> 將數字轉換為字串<br /> </td> 
   <td> ToString(&lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> 以大寫傳回字串<br /> </td> 
   <td> Upper(&lt;string&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> 傳回連結的外鍵，如果其他兩個參數相等，則傳遞為參數<br /> </td> 
   <td> VirtualLink(&lt;number&gt;、&lt;number&gt;、&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> 傳回連結的外鍵（文字）索引鍵，如果其他兩個參數相等，則傳回該連結的外鍵　(text)　<br /> </td> 
   <td> VirtualLinkStr(&lt;string&gt;, &lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> 傳回字串大小<br /> </td> 
   <td> dataLength(&lt;string&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**日期**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>語法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> 新增日期的天數<br /> </td> 
   <td> AddDays(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> 將小時數新增至日期<br /> </td> 
   <td> AddHours(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> 將分鐘數新增至日期<br /> </td> 
   <td> AddMinutes(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> 新增月份至日期<br /> </td> 
   <td> AddMonths(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> 新增秒數至日期<br /> </td> 
   <td> AddSeconds(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> 在日期中新增多年<br /> </td> 
   <td> AddYears(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> 僅傳回日期（時間為00:00）*<br /> </td> 
   <td> DateOnly(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Day</strong><br /> </td> 
   <td> 傳回代表日期的數字<br /> </td> 
   <td> Day(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> 傳回日期<br />年中的日數 </td> 
   <td> DayOfYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> 傳回與目前日期對應的日期減去n天<br /> </td> 
   <td> DaysAgo(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> 傳回與目前日期對應的日期（整數yyymmdd）減去n天<br /> </td> 
   <td> DaysAgoInt(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> 兩個日期之間的天數<br /> </td> 
   <td> DaysDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> 傳回日期的年齡（以天為單位）<br /> </td> 
   <td> DaysOld(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> 返回伺服器的目前系統日期<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> 傳回日期的小時數<br /> </td> 
   <td> Hour(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> 傳回兩個日期之間的小時數<br /> </td> 
   <td> HoursDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> 傳回日期的分鐘數<br /> </td> 
   <td> Minute(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> 傳回兩個日期之間的分鐘數<br /> </td> 
   <td> MinutesDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> 傳回代表日期月份的數字<br /> </td> 
   <td> Month(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> 傳回與目前日期對應的日期減去n個月<br /> </td> 
   <td> MonthsAgo(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> 傳回兩個日期之間的月數<br /> </td> 
   <td> MonthsDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> 傳回日期的月份<br /> </td> 
   <td> MonthsOld(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> 傳回日期的秒數<br /> </td> 
   <td> Second(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> 傳回兩個日期之間的秒數<br /> </td> 
   <td> SecondsDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> 從日期減去天數<br /> </td> 
   <td> SubDays(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> 從日期減去數小時<br /> </td> 
   <td> SubHours(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> 從日期減去分鐘數<br /> </td> 
   <td> SubMinutes(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> 從日期減去幾個月<br /> </td> 
   <td> SubMonths(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> 從日期減去秒數<br /> </td> 
   <td> SubSeconds(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> 從日期減去數年<br /> </td> 
   <td> SubYears(&lt;date&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> 將日期　+　時間轉換為日期<br /> </td> 
   <td> ToDate(&lt;date + time&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> 將字串轉換為日期+時間<br /> </td> 
   <td> ToDateTime(&lt;string&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> 將日期+時間四捨五入至最接近的秒數<br /> </td> 
   <td> TruncDate(@lastModified, &lt;number of seconds&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> 將日期+時間四捨五入為以秒為單位的指定精確度<br /> </td> 
   <td> TruncDateTZ(&lt;date&gt;, &lt;number of seconds&gt;, &lt;time zone&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> 將日期捨入為季度<br /> </td> 
   <td> TruncQuarter(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> 將時間部分捨入到最接近的秒數<br /> </td> 
   <td> TruncTim（e&lt;date&gt;, &lt;秒數&gt;）<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> 將日期捨入為一週<br /> </td> 
   <td> TruncWeek(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> 將日期+時間捨入至年度的　1　月　1　日<br /> </td> 
   <td> TruncYear(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> 傳回代表日期當週中某天的數字<br /> </td> 
   <td> WeekDay(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>年</strong><br /> </td> 
   <td> 傳回代表日期年份的數字<br /> </td> 
   <td> Year(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearAnd Month</strong><br /> </td> 
   <td> 傳回代表日期的年份和月份的數字<br /> </td> 
   <td> YearAndMonth(&lt;date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> 傳回兩個日期之間的年數<br /> </td> 
   <td> YearsDiff(&lt;end date&gt;, &lt;start date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> 傳回日期的年齡<br /> </td> 
   <td> YearsOld(&lt;date&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>請注意，**Dateonly**&#x200B;函式會考慮伺服器的時區，而非運算子的時區。

**數值**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>語法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> 返回數字的絕對值<br /> </td> 
   <td> Abs(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> 傳回大於或等於數字的最小整數<br /> </td> 
   <td> Ceil(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> 傳回大於或等於數字<br />的最大整數 </td> 
   <td> Floor(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> 傳回兩個數字中的較大值<br /> </td> 
   <td> Greatest(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> 傳回兩個數字中的較小者<br /> </td> 
   <td> Least(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> 傳回n1除以n2<br />的整數除的余數 </td> 
   <td> Mod(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Percent</strong><br /> </td> 
   <td> 傳回兩個數字的比率，以百分比表示<br /> </td> 
   <td> Percent(&lt;number 1&gt;, &lt;number 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Random</strong><br /> </td> 
   <td> 傳回隨機值<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> 將數字四捨五入為n個小數<br /> </td> 
   <td> Round(&lt;number&gt;, &lt;number of decimals&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> 傳回數字元號<br /> </td> 
   <td> Sign(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> 將整數轉換為浮點數<br /> </td> 
   <td> ToDouble(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> 將浮點數轉換為　64　位整數<br /> </td> 
   <td> ToInt64(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> 將浮點數轉換為整數<br /> </td> 
   <td> ToInteger(&lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> 截斷　n1　到　n2　小數<br /> </td> 
   <td> Trunc(&lt;n1&gt;, &lt;n2&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

1. 貨幣

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>語法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> 將來源貨幣中的金額換算為目標貨幣中的金額<br /> </td> 
   <td> ConvertCurrency(&lt;amount&gt;, &lt;source currency&gt;, &lt;target currency&gt;, &lt;conversion date&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatCurrency</strong><br /> </td> 
   <td> 根據所選貨幣設定格式化顯示的金額<br /> </td> 
   <td> FormatCurrency(&lt;amount&gt;, &lt;currency&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Geomarketing**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>語法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>距離</strong><br /> </td> 
   <td> 傳回由經度和緯度定義的兩個點之間的距離，以度表示。<br /> </td> 
   <td> 距離（&lt;Longitude A&gt;, &lt;Latitude A&gt;, &lt;Longitude B&gt;, &lt;Latitude B&gt;）<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Others**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>語法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>案例</strong><br /> </td> 
   <td> 如果條件為true，則返回值1。 否則，返回值2.<br /> </td> 
   <td> Case(When(&lt;condition&gt;, &lt;value 1&gt;), Else(&lt;value 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> 刪除值中的旗標<br /> </td> 
   <td> ClearBit(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>合併</strong><br /> </td> 
   <td> 如果值　1　為　零或　null，則傳回值　2，否則傳回值　1<br /> </td> 
   <td> Coalesce(&lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> 如果值1 =值2，則返回值3。 如果不返回值4.<br /> </td> 
   <td> Decode(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;, &lt;value 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> 傳回值　1（只能用作　case　函式的參數）<br /> </td> 
   <td> Else(&lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> 從電子郵件地址中提取域<br /> </td> 
   <td> GetEmailDomain(&lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> 檢索鏡像頁伺服器的URL<br /> </td> 
   <td> GetMirrorURL(&lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> 如果運算式為true，則傳回值1。 否則，返回值2<br /> </td> 
   <td> Iif(&lt;condition&gt;, &lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> 指出旗標是否在值中<br /> </td> 
   <td> IsBitSet(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> 如果字串1為空，則返回值2，否則返回值3<br /> </td> 
   <td> IsEmptyString(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> 如果引數為　NULL，則返回空字串<br /> </td> 
   <td> NoNull(&lt;value&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> 返回行號<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> 強制值中的旗標<br /> </td> 
   <td> SetBit(&lt;identifier&gt;, &lt;flag&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> 將數字轉換為布林值<br /> </td> 
   <td> ToBoolean(&lt;number&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> 如果運算式為true，則傳回值1。 否則，它返回值2（只能用作case函式的參數）<br /> </td> 
   <td> When(&lt;condition&gt;, &lt;value 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**窗口函式**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>語法</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> 套用遞減排序<br /> </td> 
   <td> Desc(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> 對分區內的結果進行排序<br /> </td> 
   <td> OrderBy(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> 對表上的查詢結果進行分區<br /> </td> 
   <td> PartitionBy(&lt;value 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> 根據表分區和排序順序生成行號。<br /> </td> 
   <td> RowNum(PartitionBy(&lt;value 1&gt;), OrderBy(&lt;value 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>