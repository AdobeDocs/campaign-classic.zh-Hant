---
product: campaign
title: '"使用案例：建立概述"'
description: '"使用案例：建立概述"'
audience: web
content-type: reference
topic-tags: web-applications
exl-id: a1ac3aab-dc81-4533-9207-26d5dc5e1c88
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# 使用案例：建立概述頁面{#use-cases-creating-overviews}

![](../../assets/common.svg)

在以下示例中，我們將建立概述類型的Web應用程式，以顯示資料庫中的所有Web應用程式。 設定下列元素：

* 資料夾的篩選器(請參閱 [在資料夾上新增篩選器](#adding-a-filter-on-a-folder)),
* 建立新Web應用程式的按鈕(請參閱 [添加按鈕以配置新的Web應用程式](#adding-a-button-to-configure-a-new-web-application)),
* 清單中每個條目的詳細資訊顯示(請參閱 [將詳細資訊添加到清單](#adding-detail-to-a-list)),
* 每個連結編輯工具一個篩選器(請參閱 [使用連結編輯器建立篩選](#creating-a-filter-using-a-link-editor)),
* 重新整理連結(請參閱 [建立重新整理連結](#creating-a-refresh-link))。

![](assets/s_ncs_configuration_webapp_overview.png)

## 建立單頁Web應用程式 {#creating-a-single-page-web-application}

1. 建立單一 **[!UICONTROL Page]** 網頁應用程式，並停用出站轉變和轉變至下一頁。

   ![](assets/s_ncs_configuration_webapp_create.png)

1. 變更頁面標題。

   此標題將出現在概述標題和Web應用程式概述中。

1. 在Web應用程式屬性中，通過選擇 **[!UICONTROL Single-page Web application]** 範本。

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. 開啟 **[!UICONTROL Page]** Web應用程式的活動，並開啟清單(**[!UICONTROL Static element > List]**)。
1. 在 **[!UICONTROL Data]** ，請選取 **[!UICONTROL Web applications]** 檔案和 **[!UICONTROL Label]** , **[!UICONTROL Creation date]** 和 **[!UICONTROL Type of application]** 輸出欄。
1. 在 **[!UICONTROL Filter]** 子頁簽中，建立以下篩選器，如下所示，以便僅顯示Web應用程式並從您的視圖中排除模板。

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. 關閉頁面的設定視窗，然後按一下 **[!UICONTROL Preview]**.

   將顯示資料庫中可用的Web應用程式清單。

   ![](assets/s_ncs_configuration_webapp_preview.png)

## 在資料夾上新增篩選器 {#adding-a-filter-on-a-folder}

在概觀中，您可以根據資料在Adobe Campaign樹狀結構中的位置來選擇存取資料。 這是資料夾上的篩選器。 套用下列程式，將其新增至您的概覽。

1. 將游標置於 **[!UICONTROL Page]** 節點，並新增 **[!UICONTROL Select folder]** 元素(**[!UICONTROL Advanced controls > Select folder]**)。
1. 在 **[!UICONTROL Storage]** 視窗，按一下 **[!UICONTROL Edit variables]** 連結。
1. 變更變數標籤以符合您的需求。
1. 使用 **資料夾** 值。

   >[!NOTE]
   >
   >變數的名稱必須符合連結至資料夾的元素名稱（在架構中定義），即 **資料夾** 在這個情況下。 引用表時，必須重新使用此名稱。

1. 套用 **[!UICONTROL XML]** 輸入至變數。

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. 選取 **[!UICONTROL Refresh page]** 互動。

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. 將游標放在清單上， **[!UICONTROL Advanced]** 索引標籤，參考先前在 **[!UICONTROL Folder filter XPath]** 頁簽。 您必須使用資料夾連結所關注元素的名稱，即 **資料夾**.

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >在此階段，Web應用程式不在其應用程式上下文中，因此無法在資料夾上測試篩選器。

## 添加按鈕以配置新的Web應用程式 {#adding-a-button-to-configure-a-new-web-application}

1. 將游標置於 **[!UICONTROL Page]** 元素和新增連結(**[!UICONTROL Static elements > Link]**)。
1. 修改連結標籤，因為它將出現在概述的按鈕上。

   在範例中，標籤為 **新增**.

1. 在URL欄位中插入下列URL: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**.

   >[!NOTE]
   >
   >**nms:webApp** 與Web應用程式架構一致。
   >
   >**nms:newWebApp** 與新的Web應用程式建立嚮導重合。

1. 選擇在同一視窗中顯示URL。
1. 在影像欄位中新增Web應用程式圖示： **/nms/img/webApp.png**.

   此圖示會顯示在 **[!UICONTROL New]** 按鈕。

1. 輸入 **按鈕** 在 **[!UICONTROL Style]** 欄位。

   此樣式在 **[!UICONTROL Single-page Web application]** 先前選取的範本。

   ![](assets/s_ncs_configuration_webapp_link.png)

## 將詳細資訊添加到清單 {#adding-detail-to-a-list}

當您在概覽中設定清單時，可以選擇顯示清單上每個項目的其他詳細資訊。

1. 將游標置於先前建立的清單元素上。
1. 在 **[!UICONTROL General]** 頁簽，選擇 **[!UICONTROL Columns and additional detail]** 顯示模式。

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. 在 **[!UICONTROL Data]** 頁簽，添加 **[!UICONTROL Primary key]** , **[!UICONTROL Internal name]** 和 **[!UICONTROL Description]** 欄，然後選取 **[!UICONTROL Hidden field]** 選項。

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   這樣，此資訊只會顯示在每個項目的詳細資訊中。

1. 在 **[!UICONTROL Additional detail]** 索引標籤，新增下列程式碼：

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
>伺服器上重新整理JavaScript程式庫需要5分鐘。 您可以重新啟動伺服器以避免等待此延遲。

## 篩選和更新清單 {#filtering-and-updating-the-list}

在本節中，您將建立一個篩選器，用於顯示由特定運算子建立的Web應用程式的概觀。 此篩選器是使用連結編輯器建立。 選取運算子後，重新整理清單以套用篩選器；這需要建立重新整理連結。

這兩個元素將分組在相同的容器中，以便以圖形方式在概覽中分組。

1. 將游標置於 **[!UICONTROL Page]** 元素和選取 **[!UICONTROL Container > Standard]**.
1. 將欄數設為 **2**，讓連結編輯器和連結彼此相鄰。

   ![](assets/s_ncs_configuration_webapp_container.png)

   有關元素佈局的資訊，請參閱 [本節](about-web-forms.md).

1. 套用 **dottedFilter**.

   此樣式在 **[!UICONTROL Single-page Web application]** 先前選取的範本。

   ![](assets/s_ncs_configuration_webapp_container002.png)

### 使用連結編輯器建立篩選 {#creating-a-filter-using-a-link-editor}

1. 將游標置於上一階段期間建立的容器上，並透過 **[!UICONTROL Advanced controls]** 功能表。
1. 在自動開啟的儲存窗口中，選擇 **[!UICONTROL Variables]** ，然後按一下 **[!UICONTROL Edit variables]** 連結並建立XML變數以篩選資料。

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. 修改標籤。

   它會顯示在 **[!UICONTROL Filter]** 欄位。

1. 選擇運算子表作為應用程式方案。

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. 將游標放在清單元素上，並透過 **[!UICONTROL Data > Filter]** 標籤：

   * **運算式：** 「建立者」連結的外鍵
   * **運算子：** 等於
   * **值：** 變數（變數）
   * **若：** &#39;$(var2/@id)&#39;!=&quot;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Web應用程式用戶必須是已標識的操作員，具有訪問資訊的適當Adobe Campaign權限。 此類型的配置對匿名Web應用程式無效。

### 建立重新整理連結 {#creating-a-refresh-link}

1. 將游標置於容器上並插入 **[!UICONTROL Link]** 透過 **[!UICONTROL Static elements]** 功能表。
1. 修改標籤。
1. 選取 **[!UICONTROL Refresh data in a list]**。
1. 新增先前建立的清單。

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. 在 **[!UICONTROL Image]** 欄位： **/xtk/img/refresh.png**.
1. 使用排序順序箭頭，重新組織Web應用程式的各種元素，如下所示。

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

現在已配置Web應用程式。 您可以按一下 **[!UICONTROL Preview]** 標籤來預覽。

![](assets/s_ncs_configuration_webapp_result.png)
