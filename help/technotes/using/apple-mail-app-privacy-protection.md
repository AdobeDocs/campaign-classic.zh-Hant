---
product: campaign
title: Apple郵件應用程式中的郵件隱私保護
description: 了解Apple的郵件隱私權保護功能對您的行銷活動有何影響
exl-id: e044b35a-b49f-408a-900d-2afe8ff10212
source-git-commit: 1a9e0f8bf374e10af938d15dcebe943819ae327b
workflow-type: tm+mt
source-wordcount: '2100'
ht-degree: 1%

---

# Apple郵件應用程式中的郵件隱私保護

![適用於v7和v8](../../assets/common.svg)

## 有什麼改變？

2021年，Apple推出其原生Mail應用程式的新隱私權保護功能。 此應用程式現在包含Apple的郵件隱私權保護功能。 基本上，傳送者無法再使用追蹤像素來收集關於已選擇開啟Apple Mail Privacy Protection功能的收件者的資訊。 [了解詳情](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/apple-mail-privacy-faq.html?lang=zh-Hant){target=&quot;_blank&quot;}。

## 我的促銷活動會受到哪些影響？

Adobe Campaign提供使用追蹤像素來追蹤電子郵件開啟次數的功能。 此功能不僅可用於定位和促銷活動，也可用於量度。 例如，您可以使用電子郵件開放率來評估促銷活動的成效和使用者參與度。 簡而言之，您的促銷活動可能會影響區段、鎖定目標和量度。 [了解詳情](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/apple-mail-privacy-faq.html#in-addition-to-measuring-opens%2C-what-else-is-impacted%3F){target=&quot;_blank&quot;}。

## 我該採取什麼行動？

Apple的新功能是業界在電子郵件隱私保護方面應具備的特色。 強烈建議您遵循Adobe的建議。

### 評估對促銷活動觸發程式的影響

評估這些變更如何影響您目前的促銷活動觸發程式。 識別將電子郵件開啟作為細分、鎖定目標或重新鎖定目標的標準的工作流程。 閱讀 [提示與秘訣](#find-email-open-tracking).

### 保留您的資料

保留您的資料並整合您目前在裝置上的知識。 您可以根據使用者代理程式的關鍵績效指標(KPI)。 例如，您可以根據使用iOS和Apple郵件應用程式之人員的設定檔來建立KPI。 閱讀 [提示與秘訣](#preserve-tracking-data).

### 在保留期之後封存您的追蹤記錄

在Adobe Campaign的保留期以外封存您的追蹤記錄：

1. 檢查促銷活動例項中的保留期間。
1. 再次檢查活動目標映射。 除了現成可用的設定檔表格(`nmsRecipient`)。
1. 從Adobe Campaign匯出追蹤記錄。 包含包含使用者代理和作業系統相關資料的記錄檔。

### 評估開放率的當前趨勢

決定受眾中在iOS裝置上使用Apple郵件應用程式的比例。
使用此評估，可以識別潛在的異常間隙及其原因。 您可以判斷間隙是由於促銷活動效能問題還是Apple的隱私權保護功能所致。 閱讀 [提示與秘訣](#measure-ios-footprint).

### 重新評估您的促銷活動策略和績效量度

最重要的是，我們強烈建議您主動重新評估您的促銷活動策略和促銷活動績效量度。 您可以重新關注更可靠的量度，例如點進次數、產品檢視和購買。

建議您探索目前可用的資料，並評估開放率與其他量度之間的關聯性。 如果這些量度持續產生關聯，您便可以充分信賴並改善觸發器。

## 提示與秘訣

### 測量整體iOS足跡 {#measure-ios-footprint}

若要收集Adobe Campaign資料的深入分析，您可以使用現成可用的報表：

* **[!UICONTROL Operating Systems]** 報告

   若要識別每個作業系統和每個版本的訪客比例，請使用此報表。 [顯示全文](../../reporting/using/global-reports.md#operating-systems)。

   您可以檢視每個作業系統的訪客劃分，與訪客總數相關。

   ![](../../reporting/using/assets/s_ncs_user_os_report.png)

   對於每個作業系統，您可以檢視每個作業系統版本的訪客劃分。

   ![](../../reporting/using/assets/s_ncs_user_os_report2.png)

* **[!UICONTROL Breakdown of opens]** 報告

   若要識別每個作業系統的電子郵件開啟比例，請使用此報表。 [顯示全文](../../reporting/using/global-reports.md#breakdown-of-opens)。

   ![](../../reporting/using/assets/dlv_useragent_report.png)

### 決定如何使用電子郵件開啟追蹤 {#find-email-open-tracking}

您可以識別將電子郵件開啟作為細分、鎖定目標及重新鎖定目標的標準的工作流程。

若要這麼做，您可以使用 **[!UICONTROL type]** 屬性(**[!UICONTROL url/@type]**)。 對於開啟的電子郵件，此屬性會設為 **[!UICONTROL Open]**. 此屬性可從查詢編輯器、 **[!UICONTROL Query]** 工作流程中的活動，以及預先定義的篩選。 您可以將此屬性用作行銷活動的定位標準。

![](assets/identify-email-open-tracking-1.png)

在此範例中，行銷人員想要傳送獎勵優惠給在過去七天內開啟特定傳送電子郵件並在過去一個月內購買的收件者。 在工作流程查詢中，您可以透過各種方式使用電子郵件開啟：

* 您可以將電子郵件開啟作為查詢中的定位標準。

   您可以將特定傳送之追蹤記錄檔的URL類型設定為篩選條件 **[!UICONTROL Open]**.

   ![](assets/identify-email-open-tracking-2.png)

* 您可以使用預先定義的篩選。 [深入瞭解](../../workflow/using/creating-a-filter.md)。

   ![](assets/identify-email-open-tracking-3.png)

   您可以在工作流程的查詢活動中使用此預先定義的篩選。

   ![](assets/identify-email-open-tracking-4.png)

   >[!NOTE]
   >
   >在工作流程中，您無法檢視預先定義篩選器的鎖定目標條件。

若要擷取其中使用電子郵件開啟作為定位標準的工作流程清單，您必須查詢 `xtk:workflow` 綱要。 工作流程的內容儲存在 **[!UICONTROL XML memo (data)]** 欄位。

![](assets/identify-email-open-tracking-5.png)

您可以指定工作流程必須包含此內容：

`expr="[url/@type] = 2"`

此定位准則表示追蹤URL的類型必須設為 **[!UICONTROL Open]**.

![](assets/identify-email-open-tracking-6.png)

#### 實作範例和範例套件

您可以使用此實作範例來識別將電子郵件開啟作為目標准則的工作流程，並傳送通知給您選擇的促銷活動運算子。 您可將此實作用於下列用途：

* 您可以在目標工作流程中測量從電子郵件開啟切換至其他KPI的潛在影響。 如果您未使用電子郵件開啟，則不需要進一步動作。
* 當您重新評估實作時，可以使用此範例來避免略過工作流程。

此範例顯示單一技術工作流程中的自訂實作。

![](assets/identify-email-open-wkf-1.png)

>[!IMPORTANT]
>
>此套件僅以範例提供，且Adobe不支援以產品功能的形式提供。
>
>您可能需要調整范常式式碼以配合您的行銷活動實施。
>
>一般使用者是安裝和使用此範例套件的唯一責任人。
>
>強烈建議您在非生產環境中測試及驗證此套件。

下載 [範例套件](assets/PKG_Search_workflows_using_Opens_in_queries_V1.xml) 並安裝。 [深入瞭解](../../platform/using/working-with-data-packages.md#importing-packages)。

安裝套件後，您可以從包含執行個體中現成技術工作流程的資料夾存取工作流程：

`/Administration/Production/Technical workflows/nmsTechnicalWorkflow`

從使用者介面中，選擇 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

![](assets/identify-email-open-tracking-8.png)

工作流程包含下列主要步驟：

1. 列出將電子郵件開啟作為目標准則的工作流程。
1. 列出將電子郵件開啟作為定位准則的預先定義篩選器。
1. 列出使用這些預先定義篩選器的工作流程。
1. 將兩個工作流程清單合併為一個清單。
1. 傳送電子郵件通知給指定的運算子。

工作流程包含下列詳細步驟：

1. 初始活動是 `xtk:workflow` 綱要。 此活動可用來在根據例項中尋找包含電子郵件的明確工作流程查詢，以作為定位標準。

   ![](assets/identify-email-open-tracking-9.png)

   ![](assets/identify-email-open-tracking-10.png)

   ![](assets/identify-email-open-tracking-11.png)

   結果會傳回工作流程清單。

   ![](assets/identify-email-open-tracking-12.png)

   由於此資訊被重複使用，因此工作表的名稱將儲存在全局工作流實例變數中。

   ![](assets/identify-email-open-tracking-13.png)

1. 第二個查詢用於尋找包含電子郵件開啟的預先定義篩選器。

   ![](assets/identify-email-open-tracking-14.png)

   ![](assets/identify-email-open-tracking-15.png)

   ![](assets/identify-email-open-tracking-16.png)

   系統會隨之傳回預先定義的篩選器清單。

   ![](assets/identify-email-open-tracking-17.png)

1. 此預先定義篩選器清單可用來尋找使用這些篩選器的工作流程。
1. 工作流程兩份清單合併為一份清單。

   為此，需使用JavaScript程式碼。

   ![](assets/identify-email-open-tracking-18.png)

   ```javascript
   const queryPredFilter = xtk.queryDef.create(
     <queryDef schema={vars.targetSchema} operation="select">
        <select>
          <node alias="@id" expr="@id" />
          <node alias="@name" expr="@name"  />
        </select>
        <where/>
     </queryDef>
       ).ExecuteQuery()
   
   var qDef =
     <queryDef schema="xtk:workflow" operation="select">
       <select>
         <node expr="@id"/>
         <node expr="@internalName"/>
         <node expr="@label"/>
       </select>
       <where>
         <condition boolOperator="OR" expr={"data like '%expr=[url/@type] = 2%'" }/>
       </where>
     </queryDef>
   
   for each (var filter in queryPredFilter) {       
   
      //logInfo (filter.@name);
      var condition;
      condition =<condition boolOperator="OR" expr={"data like '%" + filter.@name + "%'" }/>
      qDef.where.appendChild(condition);   
   
   }
   
   var queryWorkflowList = xtk.queryDef.create(qDef);
   var workflowList = queryWorkflowList.ExecuteQuery();
   
   var sWorkflowList = "";
   var iCount = 0
   for each (var workflow in workflowList) {       
   
      //logInfo ("Workflow ID: " + workflow.@id + " in " + instance.vars.mainTargetSchema);
   
      iWorkflowId = workflow.@id;
      iWorkflowName = workflow.@internaName;
      iWorkflowLabel = workflow.@label;
   
       xtk.session.Write(
             <{instance.vars.mainTargetSchema.split(':')[1]}
               _operation="insertOrUpdate"       
               _key="@id"
               xtkschema={instance.vars.mainTargetSchema}
               id={iWorkflowId}
               internaName={iWorkflowName}
               label={iWorkflowLabel}
             />
       )
   }
   ```

1. 複製的工作流程會從合併的清單中移除。

   ![](assets/identify-email-open-tracking-19.png)

1. 會執行測試以檢查清單是否非空白。

   ![](assets/identify-email-open-tracking-20.png)

   如果清單不為空，則會將其插入電子郵件通知的HTML表中。

   ![](assets/identify-email-open-tracking-21.png)

   ```js
   const queryWorkflow = xtk.queryDef.create(
       <queryDef schema={vars.targetSchema} operation="select">
           <select>
               <node alias="@id" expr="@id" />
               <node alias="@internalName" expr="@internalName"  />
               <node alias="@label" expr="@label"  />
           </select>
           <where/>
       </queryDef>
   ).ExecuteQuery()
   
   var sWorkflowList = '<table border="0" >';
   
   sWorkflowList = sWorkflowList + "<tr><th>Worklow Id</th><th>Name</th><th>Label</th></tr>";
   
   for each (var workflow in queryWorkflow) {       
   
      sWorkflowList = sWorkflowList + "<tr>" +
                       "<td>" + workflow.@id + "</td>" +
                       "<td>" + workflow.@internalName + "</td>" +
                       "<td>" + workflow.@label + "</td>" +
                       "</tr>";
   
   }
   
   sWorkflowList = sWorkflowList + "</table>";
   
   instance.vars.workflowList = sWorkflowList;
   ```

1. HTML表格會新增至通知範本。

   ```js
   <%= instance.vars.workflowLIst%>
   ```

   ![](assets/identify-email-open-tracking-22.png)

   電子郵件通知包含包含工作流程的清單，這些工作流程包含以電子郵件開啟作為查詢中的定位標準。

   ![](assets/identify-email-open-tracking-23.png)

### 保留您目前的追蹤資料 {#preserve-tracking-data}

#### 哪些資料會受到影響？

設定檔資料富含來自動作（例如電子郵件開啟和點進）的追蹤資料。 追蹤功能也會在有此資訊時透過使用者代理，提供使用者裝置的重要資訊。

簡而言之，Adobe Campaign追蹤資料提供以下資訊：

* 與開啟或點進特定電子郵件訊息之人員相關聯的設定檔
* 開啟日期
* 使用的裝置，例如iPhone或Mac
* 作業系統和版本，例如iOS 15、macOS 12或Windows 10
* 應用程式（如郵件應用程式或Web瀏覽器）和版本（如Outlook 2019）

#### 為何應保留追蹤資料？

基於多種原因，強烈建議您保留此資料：

* 此資料由Adobe Campaign保留有限期間。 保留期會依執行個體的設定而有所不同。

   檢查執行個體的設定。 [顯示全文](../../platform/using/privacy-management.md#data-retention)。

* 除了Apple最近的變更外，您還可以使用追蹤資料來創造巨大的價值，進而促進您對象的參與度。
* Apple可能會對其原生郵件應用程式及其郵件隱私權保護功能進行進一步變更。

基於上述原因，我們強烈建議您盡快匯出這些資料。 否則，您部分對象的追蹤資料可能會受到負面影響。

#### 如何保留追蹤資料？

若要保留追蹤資料，您必須將其從Adobe Campaign匯出至資訊系統。 [顯示全文](../../platform/using/get-started-data-import-export.md)。

>[!IMPORTANT]
>
>下列範例著重於現成可用 `nms:Recipient` 架構，此為預設配置檔案架構。 如果您使用附加至自訂設定檔的其他自訂目標對應，建議您將此匯出策略擴充至所有自訂記錄檔表格。 [顯示全文](../../configuration/using/target-mapping.md)。

##### 原則

依預設， `nms:Recipient` 結構連結至您必須匯出的三個結構：

| 結構 | 內容 |
| --- | --- |
| nms:trackingLogRcp | 追蹤資料（例如，使用者、時間和相關訊息） |
| nms:trackingUrl | 連結的詳細資訊，包括性質，例如電子郵件開啟或點進 |
| nms:userAgent | 有關設備的資訊 |

表在資料模型中連結。

![](assets/data-schema-for-tracking-data.png)

使用這些關係建立單個導出查詢。

![](assets/export-tracking-data-1.png)

您可以透過連結結構的有用資訊來擴充此資料：

| 結構 | 內容 |
| --- | --- |
| nms：收件者 | 與設定檔相關的詳細資訊 |
| nms：傳遞 | 使用者回應的訊息的相關資訊 |

您可以將結果匯出至Adobe Campaign支援的外部儲存解決方案：

* SFTP
* S3
* Azure Blob

##### 實作

此範例說明如何從Adobe Campaign匯出追蹤資料。

1. 建立以查詢開頭的工作流程。

   初始查詢可用來擷取最近三個月的追蹤記錄。
您可以使用增量查詢僅提取尚未導出的記錄。

   從 **[!UICONTROL Additional data]** 節點。

   ![](assets/export-tracking-data-2.png)

1. 新增 **[!UICONTROL Data extraction (file)]** 活動。 將查詢中的所有資料對應至解壓縮檔案格式。

   ![](assets/export-tracking-data-3.png)

   選擇檔案格式，例如TXT或CSV。

   ![](assets/export-tracking-data-4.png)

1. 將檔案上傳至支援的儲存解決方案時，新增第三個和最後一個活動。

![](assets/export-tracking-data-5.png)

##### 進階實作：依iOS裝置劃分

您可以使用工作流程來判斷收件者是否使用Apple的郵件應用程式。 您可以依裝置分割追蹤記錄。 例如，您可以使用查詢篩選器，依iOS裝置來劃分記錄：

| 應用程式 | 作業系統或設備  | 查詢篩選器 |
| --- | --- | --- |
| Apple Mail | iOS 15 | `operating System (Browser) contains 'iOS 15' and browser (Browser) contains 'ApplewebKit'` |
| Apple Mail | iOS14或iOS13 | `browser contains 'AppleWebKit' and operating System of browser contains 'iOS 14' or operating System of browser contains 'iOS 13'` |
| Apple Mail | iOS行動裝置：iPad、iPod和iPhone | `device (Browser) contains iPhone or device (Browser) equal to iPod or device (Browser) equal to iPad and browser (Browser) equal to 'AppleWebKit'` |
| Apple Mail | iPhone、iPad或iPod | `browser (Browser) equal to 'AppleWebKit' and device (Browser) equal to iPhone or device (Browser) equal to iPod or device (Browser) equal to iPad` |
| Apple Mail | Mac | `browser (Browser) equal to 'AppleWebKit' and operating System (Browser) contains 'Mac'` |
| Safari | macOS | `browser (Browser) equal to 'Safari' and device (Browser) equal to PC and operating System (Browser) contains 'Mac'` |
| Safari | 行動裝置 | `browser (Browser) equal to 'Safari' and device (Browser) equal to iPad or device (Browser) equal to iPod or device (Browser) equal to iPhone` |

![](assets/export-tracking-data-6.png)

您可以將這些規則用於各種用途：

* 將資料導出並存檔到外部儲存解決方案
* 計算要附加至設定檔的KPI
* 建立隱藏清單
* 報告

以下範例說明如何使用工作流程來依iOS裝置劃分記錄：

* 第一個範例工作流程包含下列活動：

   1. 初始 **[!UICONTROL Query]** 活動可用來選取最近三個月所有開啟的電子郵件。
   1. A **[!UICONTROL Split]** 活動可用來依電子郵件應用程式、瀏覽器、作業系統和裝置來分割選取項目。

   1. A **[!UICONTROL Deduplication]** 活動遵循每個 **[!UICONTROL Split]** 活動。 此 **[!UICONTROL Deduplication]** 活動可用來移除重複的電子郵件地址。

      此 **[!UICONTROL Deduplication]** 活動會定位在 **[!UICONTROL Split]** 活動，以避免遺失使用各種裝置的收件者的相關資訊。

   1. 安 **[!UICONTROL End]** 活動遵循每個 **[!UICONTROL Deduplication]** 活動。

   如果您只將收件者儲存在現成可用的收件者表格中，以便鎖定目標，此類型的工作流程將十分實用。

   ![](assets/export-tracking-data-wkf-1.png)

* 第二個範例工作流程包含下列活動：

   1. 初始 **[!UICONTROL Query]** 活動可用來選取最近三個月所有開啟的電子郵件。
   1. A **[!UICONTROL Deduplication]** 活動可用來移除重複的電子郵件地址。
   1. A **[!UICONTROL Fork]** 活動：

      * 在一個轉變中， **[!UICONTROL Change dimension]** 活動可用來尋找追蹤記錄所參照的收件者。
      * 在另一個轉變中， **[!UICONTROL Split]** 活動可用來依電子郵件應用程式、瀏覽器、作業系統和裝置來分割選取項目。
   1. 安 **[!UICONTROL End]** 活動會遵循 **[!UICONTROL Split]** 活動。

   如果您將收件者儲存在現成可用的收件者表格以外的表格中，此類型的工作流程將十分實用。

   ![](assets/export-tracking-data-wkf-2.png)

## 實用連結

[Apple郵件隱私權保護常見問題集](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/apple-mail-privacy-faq.html){target=&quot;_blank&quot;}
