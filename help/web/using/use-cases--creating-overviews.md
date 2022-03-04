---
product: campaign
title: '"使用案例：建立概覽"'
description: '"使用案例：建立概覽"'
feature: Web Apps
exl-id: a1ac3aab-dc81-4533-9207-26d5dc5e1c88
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# 使用案例：建立概述頁{#use-cases-creating-overviews}

![](../../assets/common.svg)

在以下示例中，我們將建立概述類型的Web應用程式，以顯示資料庫中的所有Web應用程式。 配置以下元素：

* 資料夾上的篩選器(請參閱 [在資料夾上添加篩選器](#adding-a-filter-on-a-folder))
* 用於建立新Web應用程式的按鈕(請參閱 [添加按鈕以配置新Web應用程式](#adding-a-button-to-configure-a-new-web-application))
* 清單中每個條目的詳細資訊顯示(請參閱 [將詳細資訊添加到清單](#adding-detail-to-a-list))
* 每個連結編輯工具一個篩選器(請參閱 [使用連結編輯器建立篩選器](#creating-a-filter-using-a-link-editor))
* 刷新連結(請參閱 [建立刷新連結](#creating-a-refresh-link))。

![](assets/s_ncs_configuration_webapp_overview.png)

## 建立單頁Web應用程式 {#creating-a-single-page-web-application}

1. 建立單個 **[!UICONTROL Page]** Web應用程式並禁用出站過渡和到下一頁的過渡。

   ![](assets/s_ncs_configuration_webapp_create.png)

1. 更改頁面標題。

   此標題將出現在概述標題和Web應用程式概述中。

1. 在Web應用程式屬性中，通過選擇 **[!UICONTROL Single-page Web application]** 的下界。

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. 開啟 **[!UICONTROL Page]** Web應用程式的活動並開啟清單(**[!UICONTROL Static element > List]**)。
1. 在 **[!UICONTROL Data]** 頁籤，選擇 **[!UICONTROL Web applications]** 和 **[!UICONTROL Label]** 。 **[!UICONTROL Creation date]** 和 **[!UICONTROL Type of application]** 輸出列。
1. 在 **[!UICONTROL Filter]** 子頁籤中，建立以下篩選器，如下所示，以便僅顯示Web應用程式並從視圖中排除模板。

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. 關閉頁面的配置窗口，然後按一下 **[!UICONTROL Preview]**。

   將顯示資料庫中可用的Web應用程式清單。

   ![](assets/s_ncs_configuration_webapp_preview.png)

## 在資料夾上添加篩選器 {#adding-a-filter-on-a-folder}

在概覽中，您可以根據資料在Adobe Campaign樹中的位置來選擇訪問資料。 這是資料夾上的篩選器。 應用以下流程將其添加到您的概述中。

1. 將游標置於 **[!UICONTROL Page]** 節點，並添加 **[!UICONTROL Select folder]** 元素(E)**[!UICONTROL Advanced controls > Select folder]**)。
1. 在 **[!UICONTROL Storage]** 窗口，按一下 **[!UICONTROL Edit variables]** 的子菜單。
1. 更改變數標籤以滿足您的需要。
1. 使用 **資料夾** 值。

   >[!NOTE]
   >
   >變數的名稱必須與連結到資料夾（在架構中定義）的元素的名稱匹配，即 **資料夾** 在這個例子中。 引用表時必須重新使用此名稱。

1. 應用 **[!UICONTROL XML]** 鍵入到變數。

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. 選擇 **[!UICONTROL Refresh page]** 交互。

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. 將游標置於清單中， **[!UICONTROL Advanced]** 頁籤，引用先前在 **[!UICONTROL Folder filter XPath]** 的子菜單。 必須使用資料夾連結所關注元素的名稱，即 **資料夾**。

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >在此階段，Web應用程式不在其應用程式上下文中，因此無法在資料夾上測試篩選器。

## 添加按鈕以配置新Web應用程式 {#adding-a-button-to-configure-a-new-web-application}

1. 將游標置於 **[!UICONTROL Page]** 元素並添加連結(**[!UICONTROL Static elements > Link]**)。
1. 修改連結標籤，因為它將出現在概覽的按鈕上。

   在本例中，標籤是 **新建**。

1. 在URL欄位中插入以下URL: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**。

   >[!NOTE]
   >
   >**nms:webApp** 與Web應用程式架構一致。
   >
   >**nms:newWebApp** 與「新建Web應用程式建立」嚮導一致。

1. 選擇以在同一窗口中顯示URL。
1. 在影像欄位中添加Web應用程式表徵圖： **/nms/img/webApp.png**。

   此表徵圖將出現在 **[!UICONTROL New]** 按鈕

1. 輸入 **按鈕** 的 **[!UICONTROL Style]** 的子菜單。

   此樣式在 **[!UICONTROL Single-page Web application]** 模板。

   ![](assets/s_ncs_configuration_webapp_link.png)

## 將詳細資訊添加到清單 {#adding-detail-to-a-list}

在概覽中配置清單時，您可以選擇顯示清單中每個條目的附加詳細資訊。

1. 將游標置於先前建立的清單元素上。
1. 在 **[!UICONTROL General]** 頁籤 **[!UICONTROL Columns and additional detail]** 在下拉清單中顯示模式。

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. 在 **[!UICONTROL Data]** 頁籤 **[!UICONTROL Primary key]** 。 **[!UICONTROL Internal name]** 和 **[!UICONTROL Description]** 列，然後選擇 **[!UICONTROL Hidden field]** 選項。

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   這樣，此資訊將僅在每個條目的詳細資訊中可見。

1. 在 **[!UICONTROL Additional detail]** 頁籤，添加以下代碼：

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
>在伺服器上刷新JavaScript庫需要5分鐘。 您可以重新啟動伺服器以避免等待此延遲。

## 篩選和更新清單 {#filtering-and-updating-the-list}

在本節中，您將建立一個篩選器，用於顯示由特定運算子建立的Web應用程式的概述。 此篩選器是使用連結編輯器建立的。 選擇運算子後，刷新清單以應用篩選器；這需要建立刷新連結。

這兩個元素將分組到同一容器中，以便在概覽中以圖形方式分組。

1. 將游標置於 **[!UICONTROL Page]** 元素和選擇 **[!UICONTROL Container > Standard]**。
1. 將列數設定為 **2**，以便連結編輯器和連結彼此相鄰。

   ![](assets/s_ncs_configuration_webapp_container.png)

   有關元素佈局的資訊，請參閱 [此部分](about-web-forms.md)。

1. 應用 **點式篩選器**。

   此樣式在 **[!UICONTROL Single-page Web application]** 模板。

   ![](assets/s_ncs_configuration_webapp_container002.png)

### 使用連結編輯器建立篩選器 {#creating-a-filter-using-a-link-editor}

1. 將游標置於在上一階段建立的容器上，並通過 **[!UICONTROL Advanced controls]** 的子菜單。
1. 在自動開啟的儲存窗口中，選擇 **[!UICONTROL Variables]** ，然後按一下 **[!UICONTROL Edit variables]** 連結並建立用於篩選資料的XML變數。

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. 修改標籤。

   它將出現在 **[!UICONTROL Filter]** 的子菜單。

1. 選擇運算子表作為應用程式架構。

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. 將游標置於清單元素上，並通過 **[!UICONTROL Data > Filter]** 頁籤：

   * **表達式：** 「建立者」連結的外鍵
   * **運算子：** 等於
   * **值：** 變數（變數）
   * **在下列情況下，將考慮：** &#39;$(var2/@id)&#39;!=&quot;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Web應用程式用戶必須是具有相應Adobe Campaign權限的已識別操作員才能訪問資訊。 此類型的配置對匿名Web應用程式不起作用。

### 建立刷新連結 {#creating-a-refresh-link}

1. 將游標置於容器上並插入 **[!UICONTROL Link]** 通過 **[!UICONTROL Static elements]** 的子菜單。
1. 修改標籤。
1. 選取 **[!UICONTROL Refresh data in a list]**。
1. 添加以前建立的清單。

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. 在 **[!UICONTROL Image]** 欄位： **/xtk/img/refresh.png**。
1. 使用排序順序箭頭，重新組織Web應用程式的各個元素，如下所示。

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

現在已配置Web應用程式。 您可以按一下 **[!UICONTROL Preview]** 按鈕。

![](assets/s_ncs_configuration_webapp_result.png)
