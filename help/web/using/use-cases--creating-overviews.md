---
title: 「使用案例：建立概述」
seo-title: 「使用案例：建立概述」
description: 「使用案例：建立概述」
seo-description: null
page-status-flag: never-activated
uuid: 404ae82b-2766-4802-8673-aaaa26868f46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: a3834828-4d39-4699-b648-d399797b8ea7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 使用案例：建立覆蓋{#use-cases-creating-overviews}

在下例中，我們將建立概述類型的Web應用程式，以顯示資料庫中的所有Web應用程式。 設定下列元素：

* 資料夾上的篩選(請參 [閱在資料夾上新增篩選](#adding-a-filter-on-a-folder)),
* 用於建立新Web應用程式的按鈕(請參 [閱添加按鈕以配置新Web應用程式](#adding-a-button-to-configure-a-new-web-application)),
* 詳細資訊顯示清單中每個條目(請參 [閱向清單添加詳細資訊](#adding-detail-to-a-list)),
* 每個連結編輯工具一個篩選器(請參 [閱使用連結編輯器建立篩選器](#creating-a-filter-using-a-link-editor)),
* 刷新連結(請參 [閱建立刷新連結](#creating-a-refresh-link))。

![](assets/s_ncs_configuration_webapp_overview.png)

## 建立單頁Web應用程式 {#creating-a-single-page-web-application}

1. 建立單一Web應 **[!UICONTROL Page]** 用程式，並停用傳出轉場和轉場至下一頁。

   ![](assets/s_ncs_configuration_webapp_create.png)

1. 變更頁面標題。

   此標題會出現在概述標題和Web應用程式概述中。

1. 在Web應用程式屬性中，選取範本以修改應用程式的轉 **[!UICONTROL Single-page Web application]** 譯。

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. 開啟您 **[!UICONTROL Page]** 的Web應用程式活動並開啟清單(**[!UICONTROL Static element > List]**)。
1. 在列 **[!UICONTROL Data]** 表的頁籤中，選擇文檔類 **[!UICONTROL Web applications]** 型和 **[!UICONTROL Label]** 、和 **[!UICONTROL Creation date]****[!UICONTROL Type of application]** 輸出列。
1. 在子標 **[!UICONTROL Filter]** 簽中，建立下列篩選，如下所示，以便僅顯示Web應用程式並從您的檢視中排除範本。

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. 關閉頁面的設定視窗，然後按一下 **[!UICONTROL Preview]**。

   將顯示資料庫中可用的Web應用程式清單。

   ![](assets/s_ncs_configuration_webapp_preview.png)

## 在資料夾上新增篩選 {#adding-a-filter-on-a-folder}

在概觀中，您可以根據資料在Adobe Campaign樹狀結構中的位置來選擇存取資料。 這是資料夾上的篩選。 套用下列程式，將它新增至您的概述。

1. 將游標置於Web應 **[!UICONTROL Page]** 用程式的節點上，並添加 **[!UICONTROL Select folder]** 元素(**[!UICONTROL Advanced controls > Select folder]**)。
1. 在出現 **[!UICONTROL Storage]** 的視窗中，按一下連 **[!UICONTROL Edit variables]** 結。
1. 變更變數標籤以符合您的需求。
1. 使用資料夾值變更變 **數** 。

   >[!NOTE]
   >
   >變數的名稱必須與連結至資料夾的元素名稱（在架構中定義）相符，即 **資料夾** 。 引用表時，必須重新使用此名稱。

1. 將類型 **[!UICONTROL XML]** 套用至變數。

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. 選取互 **[!UICONTROL Refresh page]** 動。

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. 將游標置於清單上，在標 **[!UICONTROL Advanced]** 簽中，參考先前在清單的標籤中 **[!UICONTROL Folder filter XPath]** 建立的變數。 您必須使用資料夾連結所關注之元素的名稱，即資料 **夾**。

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >在此階段，Web應用程式不在其應用程式內容中，因此無法在資料夾上測試篩選器。

## 新增按鈕以設定新的Web應用程式 {#adding-a-button-to-configure-a-new-web-application}

1. 將游標置於元 **[!UICONTROL Page]** 素上並新增連結(**[!UICONTROL Static elements > Link]**)。
1. 修改連結標籤，因為連結標籤會顯示在概述的按鈕上。

   在我們的範例中，標籤是 **New**。

1. 在URL欄位中插入下列URL: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**。

   >[!NOTE]
   >
   >**nms:webApp** 與Web應用程式模式一致。
   >
   >**nms:newWebApp** 與新的Web應用程式建立嚮導一致。

1. 選擇以在相同視窗中顯示URL。
1. 在影像欄位中新增Web應用程式圖示： **/nms/img/webApp.png**。

   此圖示將出現在按鈕 **[!UICONTROL New]** 上。

1. 在 **欄位中** ，輸入 **[!UICONTROL Style]** 按鈕。

   在先前選取的範本中會參 **[!UICONTROL Single-page Web application]** 考此樣式。

   ![](assets/s_ncs_configuration_webapp_link.png)

## 向清單添加詳細資訊 {#adding-detail-to-a-list}

在概述中設定清單時，您可以選擇顯示清單上每個項目的其他詳細資料。

1. 將游標置於先前建立的清單元素上。
1. 在標 **[!UICONTROL General]** 簽中，選 **[!UICONTROL Columns and additional detail]** 擇下拉式清單中的顯示模式。

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. 在標 **[!UICONTROL Data]** 簽中，新增 **[!UICONTROL Primary key]** 、 **[!UICONTROL Internal name]** 和欄，並選 **[!UICONTROL Description]****[!UICONTROL Hidden field]** 取每個欄的選項。

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   這樣，這些資訊只會顯示在每個條目的詳細資訊中。

1. 在標籤 **[!UICONTROL Additional detail]** 中，新增下列程式碼：

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

## 篩選和更新清單 {#filtering-and-updating-the-list}

在本節中，您將建立篩選器，以顯示由特定運算子建立之Web應用程式的概述。 此篩選器是使用連結編輯器建立的。 選取運算子後，請重新整理清單以套用篩選；這需要建立重新整理連結。

這兩個元素將分組在相同的容器中，以便以圖形方式在概述中分組。

1. 將游標置於元素 **[!UICONTROL Page]** 上並選取 **[!UICONTROL Container > Standard]**。
1. 將欄數設為 **2**，讓連結編輯器和連結彼此相鄰。

   ![](assets/s_ncs_configuration_webapp_container.png)

   如需元素配置的詳細資訊，請參閱 [本節](../../web/using/about-web-forms.md)。

1. 套用 **dottedFilter**。

   此樣式在先前選取的 **[!UICONTROL Single-page Web applicatio]** n個範本中參考。

   ![](assets/s_ncs_configuration_webapp_container002.png)

### 使用連結編輯器建立篩選 {#creating-a-filter-using-a-link-editor}

1. 將游標置於在上一階段建立的容器上，並透過選單插入連結編輯 **[!UICONTROL Advanced controls]** 器。
1. 在自動開啟的儲存視窗中，選取選 **[!UICONTROL Variables]** 項，然後按一下連結並 **[!UICONTROL Edit variables]** 建立XML變數以篩選資料。

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. 修改標籤。

   它將出現在概述 **[!UICONTROL Filter]** 中欄位旁。

1. 選擇Operator表作為應用程式方案。

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. 將游標置於清單元素上，並透過標籤建立篩選 **[!UICONTROL Data > Filter]** 器：

   * **** 運算式：「建立者」連結的外鍵
   * **** 運算元：等於
   * **** 值：變數（變數）
   * **** 在下列情況下，請考慮：&#39;$(var2/@id)&#39;!=&quot;
   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Web應用程式使用者必須是已識別的營運商，具有適當的Adobe Campaign權限才能存取資訊。 此類型的組態無法用於匿名Web應用程式。

### 建立刷新連結 {#creating-a-refresh-link}

1. 將游標置於容器上，並透過選 **[!UICONTROL Link]** 單插入 **[!UICONTROL Static elements]** 一個。
1. 修改標籤。
1. Select **[!UICONTROL Refresh data in a list]**.
1. 新增先前建立的清單。

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. 在欄位中新增重新整理 **[!UICONTROL Image]** 圖示：**/xtk/img/refresh.png **。
1. 使用排序順序箭頭，重新組織Web應用程式的各種元素，如下所示。

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

現在已設定Web應用程式。 您可以按一下標 **[!UICONTROL Preview]** 簽來預覽它。

![](assets/s_ncs_configuration_webapp_result.png)

