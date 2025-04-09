---
product: campaign
title: 使用案例：建立概覽
description: 使用案例：建立概覽
badge-v8: label="也適用於 v8" type="Positive" tooltip="亦適用於 Campaign v8"
feature: Web Apps
level: Intermediate, Experienced
exl-id: a1ac3aab-dc81-4533-9207-26d5dc5e1c88
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 0%

---

# 使用案例：建立概覽頁面{#use-cases-creating-overviews}



在下面的範例中，我們將創建概述類型的 Web 應用程式來顯示資料庫中的所有 Web 應用程式。 設定下列元素：

* 資料夾的篩選器（請參閱在 [資料夾](#adding-a-filter-on-a-folder)上添加篩選器），
* 創建新網路應用程式的按鈕（請參閱 [添加新按鈕以配置新網路應用程式](#adding-a-button-to-configure-a-new-web-application)），
* 清單中每個專案的詳細信息顯示（請參閱向清單](#adding-detail-to-a-list)添加詳細信息），[
* 每個連結編輯工具一個篩選器（請參閱 [使用連結創建篩選器編輯者](#creating-a-filter-using-a-link-editor)），
* 重新整理連結（請参閱 [建立重新整理連結](#creating-a-refresh-link)）。

![](assets/s_ncs_configuration_webapp_overview.png)

## 建立單頁面網路應用程式 {#creating-a-single-page-web-application}

1. 建立單個 **[!UICONTROL Page]** 網路應用程式並禁用出站轉換和到下一個頁面的轉換。

   ![](assets/s_ncs_configuration_webapp_create.png)

1. 變更頁面標題。

   此標題將顯示在概覽標題和Web應用程式概覽中。

1. 在網路應用程式屬性中，通過選擇 **[!UICONTROL Single-page Web application]** 範本來修改應用程式的呈現。

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. **[!UICONTROL Page]**&#x200B;打開網路應用程式的活動，然後打開一個清單 （**[!UICONTROL Static element > List]**）。
1. 在 **[!UICONTROL Data]** 清單標籤中，選擇文件類型 **[!UICONTROL Web applications]** 以及 **[!UICONTROL Label]** 和 **[!UICONTROL Creation date]** **[!UICONTROL Type of application]** 輸出列。
1. 在 **[!UICONTROL Filter]** 子標籤中，創建如下所示的篩選器，以便僅显示 Web 應用程式並從視圖中排除範本。

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. 關閉頁面的配置窗口，然後按下 **[!UICONTROL Preview]**。

   將顯示資料庫中可用的 Web 應用程式清單。

   ![](assets/s_ncs_configuration_webapp_preview.png)

## 在資料夾上添加篩選器 {#adding-a-filter-on-a-folder}

在概述中，您可以根據數據在Adobe Campaign樹中的位置選擇訪問數據。 這是對資料夾的篩選器。 套用以下過程以將其添加到概述中。

1. 將游標放在 **[!UICONTROL Page]** 網路應用程式的節點上，然後添加一個 **[!UICONTROL Select folder]** 元素 （**[!UICONTROL Advanced controls > Select folder]**）。
1. 在 **[!UICONTROL Storage]** 出現的窗口中，按兩下 **[!UICONTROL Edit variables]** 連結。
1. 更改變數標籤以滿足您的需求。
1. 使用資料夾&#x200B;**值更改**&#x200B;變數名稱。

   >[!NOTE]
   >
   >變數的名稱必須與連結到資料夾（在綱要中定義）的元素的名稱匹配，即 **本例中的資料夾** 。 引用表時必須重新使用此名稱。

1. **[!UICONTROL XML]**&#x200B;將類型套用為變數。

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. 選擇交互 **[!UICONTROL Refresh page]** 。

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. 將游標放在清單上，在標籤中 **[!UICONTROL Advanced]** ，引用之前在清單標籤中創建 **[!UICONTROL Folder filter XPath]** 的變數。 您必須使用資料夾連結相關的元素的名稱，即 **資料夾**。

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >此時階段，網路應用程式不在其應用程式上下文中，因此無法在資料夾上測試篩選器。

## 新增按鈕以設定新的Web應用程式 {#adding-a-button-to-configure-a-new-web-application}

1. 將游標放在&#x200B;**[!UICONTROL Page]**&#x200B;專案上並新增連結(**[!UICONTROL Static elements > Link]**)。
1. 修改連結標籤，因為該標籤會出現在概覽的按鈕上。

   在我們的範例中，標籤是 **新**。

1. 在URL欄位中插入以下URL： **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**。

   >[!NOTE]
   >
   >**nms：webApp** 與 網路應用程式 綱要重合。
   >
   >**nms：newWebApp** 與新的 網路應用程式 建立助手重合。

1. 選擇在同一視窗中顯示URL。
1. 在影像字段中新增網路應用程式圖示： **/nms/img/webApp.png**。

   此圖示將出現在 **[!UICONTROL New]** 按鈕上。

1. 在&#x200B;**[!UICONTROL Style]**&#x200B;欄位中輸入&#x200B;**按鈕**。

   此樣式在之前選擇的範本中 **[!UICONTROL Single-page Web application]** 引用。

   ![](assets/s_ncs_configuration_webapp_link.png)

## 向清單添加詳細信息 {#adding-detail-to-a-list}

在概述中配置清單時，可以選擇顯示清單上每個條目的其他詳細信息。

1. 將游標置於先前建立的 清單 元素上。
1. 在 **[!UICONTROL General]** 標籤中，在下拉式清單中選擇 **[!UICONTROL Columns and additional detail]** 显示模式。

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
>JavaScript程式庫需要5分鐘的時間在伺服器上重新整理。 您可以重新啟動伺服器以避免等待此延遲。

## 篩選和更新清單 {#filtering-and-updating-the-list}

在本節中，您將創建一個篩選器，用於顯示由特定運算符創建的 Web 應用程式的概述。 建立此篩選時采用了連結編輯者。 選擇運算符后，刷新清單以應用篩選器;這需要創建刷新連結。

這兩個元素將分組在同一容器中，以便在概述中以圖形方式分組。

1. 將游標放在元素上 **[!UICONTROL Page]** ，然後選擇 **[!UICONTROL Container > Standard]**。
1. 將列 **数設置為 2**，以便連結編輯者和連結彼此相鄰。

   ![](assets/s_ncs_configuration_webapp_container.png)

   有關元素佈局的資訊，請參閱 [此部分](about-web-forms.md)。

1. **套用點篩檢程式**。

   此樣式在之前選擇的範本中 **[!UICONTROL Single-page Web application]** 引用。

   ![](assets/s_ncs_configuration_webapp_container002.png)

### 使用 連結 編輯者建立篩選器 {#creating-a-filter-using-a-link-editor}

1. 將游標放在上一個階段中創建的容器上，然後通過功能表插入 **[!UICONTROL Advanced controls]** 連結編輯者。
1. 在自動打開的儲存視窗中，選擇該 **[!UICONTROL Variables]** 選項，然後按下 **[!UICONTROL Edit variables]** 連結並創建用於篩選數據的 XML 變數。

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. 修改標籤。

   它將顯示在概述中的欄位旁邊 **[!UICONTROL Filter]** 。

1. 選擇作數表作為應用程式綱要。

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. 將游標放在清單元素上，然後通過標籤 **[!UICONTROL Data > Filter]** 創建過濾器：

   * **表達式：“** 创建者”連結的外鍵
   * **運算子：** 等於
   * **值：** 變數 （變數）
   * **考慮條件：**「$(var2/@id)」!=

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Web應用程式使用者必須是已識別的運運算元，並擁有存取資訊的適當Adobe Campaign許可權。 此型別的設定不適用於匿名Web應用程式。

### 建立重新整理連結 {#creating-a-refresh-link}

1. 將游標放在容器上，然後通過&#x200B;**[!UICONTROL Static elements]**&#x200B;功能表插入。**[!UICONTROL Link]**
1. 修改標籤。
1. 選取 **[!UICONTROL Refresh data in a list]**。
1. 添加之前創建的清單。

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. 在欄位上 **[!UICONTROL Image]** 新增重新整理圖示： **/xtk/img/refresh.png**。
1. 使用排序順序箭頭，重新組織網路應用程式的各個元素，如下所示。

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

網路應用程式現已設定。 您可以按下 **[!UICONTROL Preview]** 標籤進行預覽。

![](assets/s_ncs_configuration_webapp_result.png)
