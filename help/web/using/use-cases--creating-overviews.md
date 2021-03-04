---
solution: Campaign Classic
product: campaign
title: '"使用案例：建立概述"'
description: '"使用案例：建立概述"'
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 11ff62238a8fb73658f2263c25dbeb27d2e0fb23
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 0%

---


# 使用案例：建立概述頁面{#use-cases-creating-overviews}

在下例中，我們將建立概述類型的Web應用程式，以顯示資料庫中的所有Web應用程式。 設定下列元素：

* 資料夾上的篩選（請參閱[在資料夾上新增篩選）,](#adding-a-filter-on-a-folder)
* 用於建立新Web應用程式的按鈕（請參閱[添加按鈕以配置新Web應用程式](#adding-a-button-to-configure-a-new-web-application)）,
* 詳細顯示清單中每個條目（請參閱[向清單添加詳細資訊](#adding-detail-to-a-list)）,
* 每個連結編輯工具一個篩選器（請參閱[使用連結編輯器建立篩選器）,](#creating-a-filter-using-a-link-editor)
* 刷新連結（請參閱[建立刷新連結](#creating-a-refresh-link)）。

![](assets/s_ncs_configuration_webapp_overview.png)

## 建立單頁Web應用程式{#creating-a-single-page-web-application}

1. 建立單一&#x200B;**[!UICONTROL Page]** Web應用程式，並停用傳出轉場和轉場至下一頁。

   ![](assets/s_ncs_configuration_webapp_create.png)

1. 變更頁面標題。

   此標題會出現在概述標題和Web應用程式概述中。

1. 在Web應用程式屬性中，通過選擇&#x200B;**[!UICONTROL Single-page Web application]**&#x200B;模板來修改應用程式的渲染。

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. 開啟Web應用程式的&#x200B;**[!UICONTROL Page]**&#x200B;活動，並開啟清單(**[!UICONTROL Static element > List]**)。
1. 在清單的&#x200B;**[!UICONTROL Data]**&#x200B;頁籤中，選擇&#x200B;**[!UICONTROL Web applications]**&#x200B;文檔類型和&#x200B;**[!UICONTROL Label]** 、 **[!UICONTROL Creation date]**&#x200B;和&#x200B;**[!UICONTROL Type of application]**&#x200B;輸出列。
1. 在&#x200B;**[!UICONTROL Filter]**&#x200B;子標籤中，建立下列篩選，如下所示，以便僅顯示Web應用程式並從您的檢視中排除範本。

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. 關閉頁面的配置窗口，然後按一下&#x200B;**[!UICONTROL Preview]**。

   將顯示資料庫中可用的Web應用程式清單。

   ![](assets/s_ncs_configuration_webapp_preview.png)

## 在資料夾{#adding-a-filter-on-a-folder}上添加篩選器

在概述中，您可以選擇根據資料在Adobe Campaign樹中的位置來存取資料。 這是資料夾上的篩選。 套用下列程式，將它新增至您的概述。

1. 將游標置於Web應用程式的&#x200B;**[!UICONTROL Page]**&#x200B;節點上，並添加&#x200B;**[!UICONTROL Select folder]**&#x200B;元素(**[!UICONTROL Advanced controls > Select folder]**)。
1. 在出現的&#x200B;**[!UICONTROL Storage]**&#x200B;窗口中，按一下&#x200B;**[!UICONTROL Edit variables]**&#x200B;連結。
1. 變更變數標籤以符合您的需求。
1. 使用&#x200B;**folder**&#x200B;值變更變數名稱。

   >[!NOTE]
   >
   >變數的名稱必須與連結至資料夾的元素名稱（在架構中定義）相符，即&#x200B;**folder**。 引用表時，必須重新使用此名稱。

1. 將&#x200B;**[!UICONTROL XML]**&#x200B;類型套用至變數。

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. 選擇&#x200B;**[!UICONTROL Refresh page]**&#x200B;交互。

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. 將游標放在清單上，在&#x200B;**[!UICONTROL Advanced]**&#x200B;頁籤中，引用以前在清單的&#x200B;**[!UICONTROL Folder filter XPath]**&#x200B;頁籤中建立的變數。 您必須使用資料夾連結所關注之元素的名稱，即&#x200B;**folder**。

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >在此階段，Web應用程式不在其應用程式內容中，因此無法在資料夾上測試篩選器。

## 添加用於配置新Web應用程式{#adding-a-button-to-configure-a-new-web-application}的按鈕

1. 將游標置於&#x200B;**[!UICONTROL Page]**&#x200B;元素上並添加連結(**[!UICONTROL Static elements > Link]**)。
1. 修改連結標籤，因為連結標籤會顯示在概述的按鈕上。

   在我們的範例中，標籤為&#x200B;**New**。

1. 在URL欄位中插入下列URL:**xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**。

   >[!NOTE]
   >
   >**nms:** webApp與Web應用程式模式一致。
   >
   >**nms:** newWebApp與新的Web應用程式建立嚮導一致。

1. 選擇以在相同視窗中顯示URL。
1. 在影像欄位中新增Web應用程式圖示：**/nms/img/webApp.png**。

   此表徵圖將顯示在&#x200B;**[!UICONTROL New]**&#x200B;按鈕上。

1. 在&#x200B;**[!UICONTROL Style]**&#x200B;欄位中輸入&#x200B;**button**。

   此樣式在先前選擇的&#x200B;**[!UICONTROL Single-page Web application]**&#x200B;模板中參考。

   ![](assets/s_ncs_configuration_webapp_link.png)

## 向清單{#adding-detail-to-a-list}添加詳細資訊

在概述中設定清單時，您可以選擇顯示清單上每個項目的其他詳細資料。

1. 將游標置於先前建立的清單元素上。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;標籤中，從下拉式清單中選擇&#x200B;**[!UICONTROL Columns and additional detail]**&#x200B;顯示模式。

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. 在&#x200B;**[!UICONTROL Data]**&#x200B;標籤中，添加&#x200B;**[!UICONTROL Primary key]** 、 **[!UICONTROL Internal name]**&#x200B;和&#x200B;**[!UICONTROL Description]**&#x200B;列，並為每個列選擇&#x200B;**[!UICONTROL Hidden field]**&#x200B;選項。

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   這樣，這些資訊只會顯示在每個條目的詳細資訊中。

1. 在&#x200B;**[!UICONTROL Additional detail]**&#x200B;標籤中，新增下列程式碼：

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
>在伺服器上重新整理JavaScript程式庫需要5分鐘。 您可以重新啟動伺服器以避免等待此延遲。

## 篩選和更新清單{#filtering-and-updating-the-list}

在本節中，您將建立篩選器，以顯示由特定運算子建立之Web應用程式的概述。 此篩選器是使用連結編輯器建立的。 選取運算子後，請重新整理清單以套用篩選；這需要建立重新整理連結。

這兩個元素將分組在相同的容器中，以便以圖形方式在概述中分組。

1. 將游標置於&#x200B;**[!UICONTROL Page]**&#x200B;元素上，然後選擇&#x200B;**[!UICONTROL Container > Standard]**。
1. 將欄數設為&#x200B;**2**，讓連結編輯器和連結彼此相鄰。

   ![](assets/s_ncs_configuration_webapp_container.png)

   有關元素佈局的資訊，請參閱[本節](../../web/using/about-web-forms.md)。

1. 套用&#x200B;**dottedFilter**。

   此樣式在先前選擇的&#x200B;**[!UICONTROL Single-page Web applicatio]** n模板中參考。

   ![](assets/s_ncs_configuration_webapp_container002.png)

### 使用連結編輯器{#creating-a-filter-using-a-link-editor}建立過濾器

1. 將游標置於在上一階段建立的容器上，並透過&#x200B;**[!UICONTROL Advanced controls]**&#x200B;功能表插入連結編輯器。
1. 在自動開啟的儲存窗口中，選擇&#x200B;**[!UICONTROL Variables]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Edit variables]**&#x200B;連結並建立用於過濾資料的XML變數。

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. 修改標籤。

   它將出現在概述的&#x200B;**[!UICONTROL Filter]**&#x200B;欄位旁。

1. 選擇Operator表作為應用程式方案。

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. 將游標置於清單元素上，並透過&#x200B;**[!UICONTROL Data > Filter]**&#x200B;標籤建立篩選：

   * **表達式：** &#39;Created by&#39;連結的外鍵
   * **運算元：** 等於
   * **值：變** 數（變數）
   * **考量if:** &#39;$(var2/@id)&#39;!=&quot;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Web應用程式使用者必須是已識別的營運商，具有適當的Adobe Campaign權限才能存取資訊。 此類型的組態無法用於匿名Web應用程式。

### 建立刷新連結{#creating-a-refresh-link}

1. 將游標置於容器上，並透過&#x200B;**[!UICONTROL Static elements]**&#x200B;功能表插入&#x200B;**[!UICONTROL Link]**。
1. 修改標籤。
1. 選取 **[!UICONTROL Refresh data in a list]**。
1. 新增先前建立的清單。

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. 在&#x200B;**[!UICONTROL Image]**&#x200B;欄位中新增重新整理圖示：**/xtk/img/refresh.png**。
1. 使用排序順序箭頭，重新組織Web應用程式的各種元素，如下所示。

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

現在已設定Web應用程式。 您可以按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤來預覽。

![](assets/s_ncs_configuration_webapp_result.png)

