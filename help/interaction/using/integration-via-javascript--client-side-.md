---
product: campaign
title: 透過 JavaScript 進行整合 (用戶端)
description: 透過 JavaScript 進行整合 (用戶端)
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a9842e59-120c-4a35-abdf-6540a0bbdd6d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1140'
ht-degree: 2%

---

# 透過 JavaScript 進行整合 (用戶端){#integration-via-javascript-client-side}

![](../../assets/v7-only.svg)

若要在網頁中呼叫互動引擎，請將對JavaScript程式碼的呼叫直接插入頁面中。 此呼叫會傳回目標中的選件內容

元素。

Adobe建議使用JavaScript整合方法。

呼叫URL的指令碼看起來像這樣：

```
<script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=" type="text/javascript"></script>
```

「**env**」參數接收專用於匿名互動的即時環境的內部名稱。

若要呈現選件，我們需要在Adobe Campaign中建立環境和選件空間，然後設定HTML頁面。

下列使用案例詳細說明透過JavaScript整合優惠方案的可能選項。

## HTML模式 {#html-mode}

### 呈現匿名選件 {#presenting-an-anonymous-offer}

1. **準備互動引擎**

   開啟Adobe Campaign介面並準備匿名環境。

   建立連結至匿名環境的優惠方案空間。

   建立連結至優惠方案空間的優惠方案及其表示法。

1. **HTML頁面的內容**

   HTML頁面必須包含

   具有@id屬性的元素，其值為已建立選件空間的內部名稱(「i_internal name space」)。 選件會插入此
元素。

   在本例中，@id屬性接收「i_SPC12」值，其中「SPC12」是先前建立的優惠方案空間的內部名稱：

   ```
   <div id="i_SPC12"></div>
   ```

   在我們的範例中，呼叫指令碼的URL如下（「OE3」是即時環境的內部名稱）:

   ```
   <script id="interactionProposalScript" src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" type="text/javascript"></script>
   ```

   >[!IMPORTANT]
   >
   >`<script>`標籤不得自行關閉。

   此靜態呼叫會自動產生包含互動引擎所需所有參數的動態呼叫。

   此行為可讓您在相同頁面上使用數個優惠方案空間，由對引擎的單一呼叫管理。

1. **結果為HTML頁面**

   互動引擎會將選件表示的內容傳回至HTML頁面：

   ```
   <div id="banner_header">
     <div id="i_SPC12">
       <table>
         <tbody>
           <tr>
             <td><h3>Fly to Japan!</h3></td>
           </tr>
           <tr>
             <td><img width="150px" src="https://instance.adobe.org/res/Track/874fdaf72ddc256b2d8260bb8ec3a104.jpg"></td>
             <td>
               <p>Discover Japan for 2 weeks at an unbelievable price!!</p>
               <p><b>2345 Dollars - All inclusive</b></p>
             </td>
           </tr>
         </tbody>
       </table>
     </div>
     <script src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" id="interactionProposalScript" type="text/javascript"></script>
   </div>
   ```

### 呈現已識別的優惠方案 {#presenting-an-identified-offer}

若要向已識別的聯絡人呈現優惠方案，程式與此處詳述的程式類似：[呈現匿名選件](#presenting-an-anonymous-offer)。 在網頁的內容中，您需要新增下列指令碼，以在呼叫引擎期間識別連絡人：

```
<script type="text/javascript">
  interactionTarget = <contact_identifier>;
</script>
```

1. 前往網頁將呼叫的優惠方案空間，按一下&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;並新增一或多個識別金鑰。

   ![](assets/interaction_htmlmode_001.png)

   在此範例中，識別金鑰為複合金鑰，因為它同時以電子郵件和收件者名稱為基礎。

1. 在網頁顯示期間，指令碼評估可讓您將收件者ID傳遞至選件引擎。 如果ID是複合的，則會以與進階設定中使用相同的順序顯示索引鍵，並以 | 。

   在下列範例中，連絡人已登入網站，且在呼叫互動引擎期間，由於其電子郵件和姓名而被識別。

   ```
   <script type="text/javascript">
     interactionTarget = myEmail|myName;
   </script>
   ```

### 使用HTML呈現函式 {#using-an-html-rendering-function}

若要自動產生HTML選件表示法，您可以使用呈現函式。

1. 前往選件空間，然後按一下&#x200B;**[!UICONTROL Edit functions]**&#x200B;連結。
1. 選取 **[!UICONTROL Overload the HTML rendering function]**。
1. 前往&#x200B;**[!UICONTROL HTML rendering]**&#x200B;標籤，並插入與選件空間中針對選件內容定義之欄位相符的變數。

   ![](assets/interaction_htmlmode_002.png)

   在此範例中，選件會以網頁中橫幅的形式顯示，由可點按的影像和標題組成，標題與選件內容中定義的欄位相符。

## XML模式 {#xml-mode}

### 呈現優惠方案 {#presenting-an-offer}

互動可讓您將XML節點傳回至呼叫選件引擎的HTML頁面。 此XML節點可由客戶端開發的函式進行處理。

對互動引擎的呼叫如下所示：

```
<script type="text/javascript" id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=&cb="></script>
```

「**env**」參數會接收即時環境的內部名稱。

&quot;**cb**&quot;參數接收函式的名稱，該函式將讀取引擎返回的包含（回撥）命題的XML節點。 此參數為選用。

「**t**」參數僅用於已識別的互動，接收目標的值。 此參數也可以與&#x200B;**interactionTarget**&#x200B;變數一併傳遞。 此參數為選用。

「**c**」參數接收類別的內部名稱清單。 此參數為選用。

「**th**」參數接收主題清單。 此參數為選用。

「**gctx**」參數接收到整個頁面的呼叫資料全域（內容）。 此參數為選用。

傳回的XML節點如下所示：

```
<propositions>
 <proposition id="" offer-id="" weight="" rank="" space="" div=""> //proposition identifiers
   ...XML content defined in Adobe Campaign...
 </proposition>
 ...
</propositions>
```

下列使用案例詳細說明在Adobe Campaign中執行以啟用XML模式的設定，然後在HTML頁面中顯示對引擎的呼叫結果。

1. **建立環境和優惠方案空間**

   如需建立環境的詳細資訊，請參閱[即時/設計環境](../../interaction/using/live-design-environments.md)。

   如需建立優惠方案空間的詳細資訊，請參閱[建立優惠方案空間](../../interaction/using/creating-offer-spaces.md)。

1. **擴充優惠方案結構以新增欄位**

   此架構將定義下列欄位：標題2和價格。

   範例中的架構名稱為&#x200B;**cus:offer**

   ```
   <srcSchema _cs="Marketing offers (cus)" created="2013-01-18 17:14:20.762Z" createdBy-id="0"
              desc="" entitySchema="xtk:srcSchema" extendedSchema="nms:offer" img="nms:offer.png"
              label="Marketing offers" labelSingular="Marketing offers" lastModified="2013-01-18 15:20:18.373Z"
              mappingType="sql" md5="F14A7AA009AE1FCE31B0611E72866AC3" modifiedBy-id="0"
              name="offer" namespace="cus" xtkschema="xtk:srcSchema">
     <createdBy _cs="Administrator (admin)"/>
     <modifiedBy _cs="Administrator (admin)"/>
     <element img="nms:offer.png" label="Marketing offers" labelSingular="Marketing offer"
              name="offer">
       <element label="Content" name="view">
         <element label="Price" name="price" type="long" xml="true"/>
         <element label="Title 2" name="title2" type="string" xml="true"/>
   
         <element advanced="true" desc="Price calculation script." label="Script price"
                  name="price_jst" type="CDATA" xml="true"/>
         <element advanced="true" desc="Title calculation script." label="Script title"
                  name="title2_jst" type="CDATA" xml="true"/>
       </element>
     </element>
   </srcSchema>
   ```

   >[!IMPORTANT]
   >
   >每個元素都需定義兩次。 CDATA(「_jst」)類型元素可以包含個人化欄位。
   >
   >別忘了更新資料庫結構。 如需詳細資訊，請參閱[本章節](../../configuration/using/updating-the-database-structure.md)。

   >[!NOTE]
   >
   >您可以擴充選件結構，以批次和統一模式，以及任何格式（文字、HTML和XML）新增欄位。

1. **擴充優惠方案公式以編輯新欄位和修改現有欄位**

   編輯&#x200B;**選件(nsm)**&#x200B;輸入表單。

   在「檢視」區段中，插入兩個新欄位，並包含下列內容：

   ```
   <input label="Title 2" margin-right="5" prebuildSubForm="false" type="subFormLink"
                        xpath="title2_jst">
                   <form label="Edit title 2" name="editForm" nothingToSave="true">
                     <input nolabel="true" toolbarAlign="horizontal" type="jstEdit"
                            xpath="." xpathInsert="/ignored/customizeTitle2">
                       <container>
                         <input menuId="viewMenuBuilder" options="inbound" type="customizeBtn"
                                xpath="/ignored/customizeTitle2"/>
                       </container>
                     </input>
                   </form>
                 </input>
                 <input nolabel="true" type="edit" xpath="title2_jst"/>
   
                 <input label="Price" margin-right="5" prebuildSubForm="false" type="subFormLink"
                        xpath="price_jst">
                   <form label="Edit price" name="editForm" nothingToSave="true">
                     <input nolabel="true" toolbarAlign="horizontal" type="jstEdit"
                            xpath="." xpathInsert="/ignored/customizePrice">
                       <container>
                         <input menuId="viewMenuBuilder" options="inbound" type="customizeBtn"
                                xpath="/ignored/customizePrice"/>
                       </container>
                     </input>
                   </form>
                 </input>
                 <input colspan="2" label="Prix" nolabel="true" type="number" xpath="price_jst"/>
   ```

   註解目標URL欄位：

   ![](assets/interaction_xmlmode_form_001.png)

   >[!IMPORTANT]
   >
   >(`<input>`)表單的欄位必須指向建立架構中定義的CDATA類型元素。

   優惠方案表示表單中的呈現如下所示：

   ![](assets/interaction_xmlmode_form.png)

   已新增&#x200B;**[!UICONTROL Title 2]**&#x200B;和&#x200B;**[!UICONTROL Price]**&#x200B;欄位，且不再顯示&#x200B;**[!UICONTROL Destination URL]**&#x200B;欄位。

1. **建立優惠方案**

   如需建立優惠方案的詳細資訊，請參閱[建立優惠方案](../../interaction/using/creating-an-offer.md)。

   在下列使用案例中，選件的輸入方式如下：

   ![](assets/interaction_xmlmode_offer.png)

1. 核准優惠方案或讓其他人核准優惠方案，然後在最後一個步驟建立的優惠方案空間上加以啟用，以便在連結的即時環境中使用。
1. **HTML頁面上的引擎呼叫和結果**

   HTML頁面中對互動引擎的呼叫看起來像這樣：

   ```
   <script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=OE7&cb=alert" type="text/javascript">
   ```

   「**env**」參數的值是即時環境的內部名稱。

   &quot;**cb**&quot;參數的值是需要解譯引擎返回的XML節點的函式的名稱。 在我們的範例中，呼叫的函式會開啟一個模組視窗(alert()函式)。

   交互引擎返回的XML節點如下所示：

   ```
   <propositions>
    <proposition id="a28002" offer-id="10322005" weight="1" rank="1" space="SPC14" div="i_SPC14">
     <xmlOfferView>
      <title>Travel to Russia</title>
      <price>3456</price>
      <description>Discover this vacation package!INCLUDES 10 nights. FEATURES buffet breakfast daily. BONUS 5th night free.</description>
      <image>
       <path>https://myinstance.com/res/Track/ae1d2113ed732d58a3beb441084e5960.jpg</path>
       <alt>Travel to Russia</alt>
      </image>
     </xmlOfferView>
    </proposition>
   </propositions>
   ```

### 使用呈現函式 {#using-a-rendering-function-}

可以使用XML呈現函式來建立優惠方案簡報。 此函式將修改在呼叫引擎期間傳回至HTML頁面的XML節點。

1. 前往選件空間，然後按一下&#x200B;**[!UICONTROL Edit functions]**&#x200B;連結。
1. 選取 **[!UICONTROL Overload the XML rendering function]**。
1. 前往&#x200B;**[!UICONTROL XML rendering]**&#x200B;標籤，並插入所需的函式。

   函式可能如下所示：

   ```
   function (proposition) {
     delete proposition.@id;
     proposition.@newAttribute = "newValue";
   } 
   ```

![](assets/interaction_xmlmode_001.png)
