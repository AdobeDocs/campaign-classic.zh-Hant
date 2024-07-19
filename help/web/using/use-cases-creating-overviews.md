---
product: campaign
title: 「使用案例：建立概覽」
description: 「使用案例：建立概覽」
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Apps
exl-id: a1ac3aab-dc81-4533-9207-26d5dc5e1c88
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 0%

---

# 使用案例：建立概觀頁面{#use-cases-creating-overviews}



在下列範例中，我們將建立概觀型別的Web應用程式，以顯示資料庫中的所有網頁應用程式。 設定下列元素：

* 資料夾上的篩選器（請參閱[在資料夾上新增篩選器](#adding-a-filter-on-a-folder)），
* 用於建立新Web應用程式的按鈕（請參閱[新增按鈕以設定新Web應用程式](#adding-a-button-to-configure-a-new-web-application)），
* 清單中每個專案的詳細資訊顯示（請參閱[新增詳細資訊至清單](#adding-detail-to-a-list)），
* 每個連結編輯工具一個篩選器（請參閱[使用連結編輯器建立篩選器](#creating-a-filter-using-a-link-editor)），
* 重新整理連結（請參閱[建立重新整理連結](#creating-a-refresh-link)）。

![](assets/s_ncs_configuration_webapp_overview.png)

## 建立單頁Web應用程式 {#creating-a-single-page-web-application}

1. 建立單一&#x200B;**[!UICONTROL Page]** Web應用程式，並停用出站轉換及下一頁的轉換。

   ![](assets/s_ncs_configuration_webapp_create.png)

1. 變更頁面標題。

   此標題將顯示在概覽標題和Web應用程式概覽中。

1. 在Web應用程式屬性中，選取&#x200B;**[!UICONTROL Single-page Web application]**&#x200B;範本，修改應用程式的轉譯。

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. 開啟網頁應用程式的&#x200B;**[!UICONTROL Page]**&#x200B;活動並開啟清單(**[!UICONTROL Static element > List]**)。
1. 在您的清單的&#x200B;**[!UICONTROL Data]**&#x200B;索引標籤中，選取&#x200B;**[!UICONTROL Web applications]**&#x200B;檔案的型別以及&#x200B;**[!UICONTROL Label]** 、 **[!UICONTROL Creation date]**&#x200B;和&#x200B;**[!UICONTROL Type of application]**&#x200B;輸出欄。
1. 在&#x200B;**[!UICONTROL Filter]**&#x200B;子標籤中，建立下列篩選器，如下所示，以便只顯示Web應用程式並從檢視中排除範本。

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. 關閉頁面的設定視窗並按一下&#x200B;**[!UICONTROL Preview]**。

   會顯示資料庫中可用的Web應用程式清單。

   ![](assets/s_ncs_configuration_webapp_preview.png)

## 在資料夾中新增篩選器 {#adding-a-filter-on-a-folder}

在概觀中，您可以選擇根據資料在Adobe Campaign樹狀結構中的位置來存取資料。 這是資料夾上的篩選器。 套用下列程式以將其新增至您的概觀。

1. 將游標放在網頁應用程式的&#x200B;**[!UICONTROL Page]**&#x200B;節點上，並新增&#x200B;**[!UICONTROL Select folder]**&#x200B;元素(**[!UICONTROL Advanced controls > Select folder]**)。
1. 在出現的&#x200B;**[!UICONTROL Storage]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Edit variables]**&#x200B;連結。
1. 變更變數標籤以符合您的需求。
1. 以&#x200B;**資料夾**&#x200B;值變更變數名稱。

   >[!NOTE]
   >
   >變數的名稱必須符合連結至資料夾（在結構描述中定義）的元素名稱，在此例中是&#x200B;**資料夾**。 參照表格時，必須重複使用此名稱。

1. 將&#x200B;**[!UICONTROL XML]**&#x200B;型別套用至變數。

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. 選取&#x200B;**[!UICONTROL Refresh page]**&#x200B;互動。

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. 將游標放在清單上，並在&#x200B;**[!UICONTROL Advanced]**&#x200B;索引標籤中，參考先前在清單的&#x200B;**[!UICONTROL Folder filter XPath]**&#x200B;索引標籤中建立的變數。 您必須使用資料夾連結涉及的元素名稱，即&#x200B;**資料夾**。

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >在此階段，網頁應用程式不在它的應用程式內容中，因此無法在資料夾上測試篩選器。

## 新增按鈕以設定新的Web應用程式 {#adding-a-button-to-configure-a-new-web-application}

1. 將游標放在&#x200B;**[!UICONTROL Page]**&#x200B;專案上並新增連結(**[!UICONTROL Static elements > Link]**)。
1. 修改連結標籤，因為該標籤會出現在概覽的按鈕上。

   在我們的範例中，標籤是&#x200B;**New**。

1. 在URL欄位中插入下列URL： **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**。

   >[!NOTE]
   >
   >**nms：webApp**&#x200B;與Web應用程式結構描述一致。
   >
   >**nms：newWebApp**&#x200B;與新的Web應用程式建立精靈一致。

1. 選擇在相同視窗中顯示URL。
1. 在影像欄位中新增網頁應用程式圖示： **/nms/img/webApp.png**。

   此圖示將出現在&#x200B;**[!UICONTROL New]**&#x200B;按鈕上。

1. 在&#x200B;**[!UICONTROL Style]**&#x200B;欄位中輸入&#x200B;**按鈕**。

   此樣式已在先前選取的&#x200B;**[!UICONTROL Single-page Web application]**&#x200B;範本中參照。

   ![](assets/s_ncs_configuration_webapp_link.png)

## 新增詳細資料至清單 {#adding-detail-to-a-list}

當您在總覽中設定清單時，您可以選擇顯示清單上每個專案的額外詳細資訊。

1. 將游標放在先前建立的清單元素上。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;索引標籤中，選取下拉式清單中的&#x200B;**[!UICONTROL Columns and additional detail]**&#x200B;顯示模式。

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. 在&#x200B;**[!UICONTROL Data]**&#x200B;索引標籤中，新增&#x200B;**[!UICONTROL Primary key]**、**[!UICONTROL Internal name]**&#x200B;及&#x200B;**[!UICONTROL Description]**&#x200B;欄，並為每個欄選取&#x200B;**[!UICONTROL Hidden field]**&#x200B;選項。

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   如此一來，此資訊只會顯示在每個專案的詳細資訊中。

1. 在&#x200B;**[!UICONTROL Additional detail]**&#x200B;索引標籤中，新增下列程式碼：

   ```
   <div class="detailBox">
     <div class="actionBox">
       <span class="action"><img src="/xtk/img/fileEdit.png"/><a title="Open" class="linkAction" href="xtk://open/?schema=nms:webApp&form=nms:webApp&pk=
       <%=webApp.id%>">Open...</a></span>
       <% 
       if( webApp.@appType == 1 ) { //survey
       %>
       <span class="action"><img src="/xtk/img/report.png"/><a target="_blank" title="Reports" class="linkAction" href="/xtk/report.jssp?_context=selection&
         _schema=nms:webApp&_selection=<%=webApp.@id%>
         &__sessiontoken=<%=document.controller.getSessionToken()%>">Reports</a></span>
       <% 
       } 
       %>
     </div>
     <div>
       Internal name: <%= webApp.@internalName %>
     </div>
     <%
     if( webApp.desc != "" )
     {
     %>
     <div>
       Description: <%= webApp.desc %>
     </div>
     <% 
     } 
     %>
   </div>
   ```

>[!NOTE]
>
>JavaScript程式庫需要5分鐘的時間在伺服器上重新整理。 您可以重新啟動伺服器以避免等候此延遲。

## 篩選和更新清單 {#filtering-and-updating-the-list}

在本節中，您將建立一個篩選器，以顯示特定運運算元所建立之Web應用程式的概觀。 此篩選器是使用連結編輯器建立的。 選取運運算元後，請重新整理清單以套用您的篩選器；這需要建立重新整理連結。

這兩個元素將分組到相同的容器中，以便在概述中以圖形方式分組。

1. 將游標放在&#x200B;**[!UICONTROL Page]**&#x200B;專案上並選取&#x200B;**[!UICONTROL Container > Standard]**。
1. 將欄數設定為&#x200B;**2**，讓連結編輯器和連結彼此相鄰。

   ![](assets/s_ncs_configuration_webapp_container.png)

   如需元素配置的資訊，請參閱[本區段](about-web-forms.md)。

1. 套用&#x200B;**dottedFilter**

   此樣式已在先前選取的&#x200B;**[!UICONTROL Single-page Web application]**&#x200B;範本中參照。

   ![](assets/s_ncs_configuration_webapp_container002.png)

### 使用連結編輯器建立篩選器 {#creating-a-filter-using-a-link-editor}

1. 將游標放在上一個階段建立的容器上，並透過&#x200B;**[!UICONTROL Advanced controls]**&#x200B;功能表插入連結編輯器。
1. 在自動開啟的儲存視窗中，選取&#x200B;**[!UICONTROL Variables]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Edit variables]**&#x200B;連結並建立用於篩選資料的XML變數。

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. 修改標籤。

   它將顯示在總覽中的&#x200B;**[!UICONTROL Filter]**&#x200B;欄位旁。

1. 選擇運運算元表格作為應用程式綱要。

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. 將游標放在清單元素上，並透過&#x200B;**[!UICONTROL Data > Filter]**&#x200B;索引標籤建立篩選器：

   * **運算式：** &#39;建立者&#39;連結的外部索引鍵
   * **運運算元：**&#x200B;等於
   * **值：**&#x200B;變數（變數）
   * **考慮條件：** &#39;$(var2/@id)&#39;！=&quot;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Web應用程式使用者必須是已識別的運運算元，並擁有存取資訊的適當Adobe Campaign許可權。 此型別的設定不適用於匿名Web應用程式。

### 建立重新整理連結 {#creating-a-refresh-link}

1. 將游標放在容器上，並透過&#x200B;**[!UICONTROL Static elements]**&#x200B;功能表插入&#x200B;**[!UICONTROL Link]**。
1. 修改標籤。
1. 選取 **[!UICONTROL Refresh data in a list]**。
1. 新增先前建立的清單。

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. 在&#x200B;**[!UICONTROL Image]**&#x200B;欄位上新增重新整理圖示： **/xtk/img/refresh.png**。
1. 使用排序順序箭頭，重新組織Web應用程式的各種元素，如下所示。

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

Web應用程式現在已設定完畢。 您可以按一下「**[!UICONTROL Preview]**」標籤來預覽。

![](assets/s_ncs_configuration_webapp_result.png)
