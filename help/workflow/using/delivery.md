---
product: campaign
title: 傳遞
description: 深入瞭解傳遞型別工作流程活動
feature: Workflows, Channels Activity
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# 傳遞{#delivery}



**傳遞**&#x200B;型別的活動可讓您建立傳遞動作。 可使用輸入元素來建構。

若要設定，請編輯活動並輸入傳送選項。

![](assets/edit_diffusion.png)

1. **傳送**

   您可以：

   * 對入站轉變中指定的傳遞採取行動。 若要這麼做，請選取視窗&#x200B;**[!UICONTROL Delivery]**&#x200B;區段的第一個選項。

     當先前的工作流程活動已建立或指定傳送時，可使用此選項。 如以下範例所示，這可以由產生出站轉變的相同型別的活動完成。

     在下列範例中，會首次建立傳送。 母體及內容將於稍後定義。 接著，系統會使用入站轉變，將這三個元素的資訊重新輸入新的傳送活動，以便傳送。

     ![](assets/specified_transition_option_exemple.png)

   * 直接選取相關的傳遞。 若要這麼做，請選取&#x200B;**[!UICONTROL Explicit]**&#x200B;選項，然後從&#x200B;**[!UICONTROL Delivery]**&#x200B;欄位的下拉式清單中選取傳遞。

     清單預設會顯示&#x200B;**傳送**&#x200B;資料夾中包含的未完成傳送。 若要存取其他行銷活動，請按一下&#x200B;**[!UICONTROL Select link]**&#x200B;圖示。

     ![](assets/diffusion_edit_1.png)

     從&#x200B;**[!UICONTROL Folder]**&#x200B;欄位的下拉式清單中選取行銷活動，或按一下&#x200B;**[!UICONTROL Display sub-levels]**&#x200B;以顯示子資料夾中包含的所有傳遞：

     ![](assets/diffusion_edit_2.png)

     選取傳遞動作後，您可以按一下&#x200B;**[!UICONTROL Edit link]**&#x200B;圖示來顯示內容。

   * 建立指令碼以計算傳遞。 若要這麼做，請選取&#x200B;**[!UICONTROL Computed by a script]**&#x200B;選項並輸入指令碼。 您可以按一下&#x200B;**[!UICONTROL Edit...]**&#x200B;選項來開啟輸入視窗。 以下範例會復原傳遞的識別碼：

     ![](assets/diffusion_edit_3.png)

   * 建立新傳遞。 若要這麼做，請選取&#x200B;**[!UICONTROL New, created from a template]**&#x200B;選項，然後選取傳遞將依據的傳遞範本。

     ![](assets/diffusion_edit_4.png)

     按一下「**[!UICONTROL Select link]**」圖示以瀏覽資料夾，如果您想要檢視所選範本的內容，請按一下「**[!UICONTROL Edit link]**」圖示。

1. **個收件者**

   收件者可由傳入事件指定，例如在檔案匯入後，或在傳遞動作中指定。 它們也可以儲存在一個或多個檔案中。

   ![](assets/diffusion_edit_5.png)

1. **內容**

   訊息的內容可在傳遞或傳入事件中定義。

   ![](assets/diffusion_edit_6.png)

1. **要執行的動作**

   您可以建立傳遞、準備、開始、估計目標或傳送證明。

   ![](assets/diffusion_edit_7.png)

   選取要執行的動作型別：

   * **[!UICONTROL Save]**：此選項可讓您建立傳遞並儲存。 它不會分析或傳遞。
   * **[!UICONTROL Estimate the target]**：此選項可讓您計算傳遞目標，以評估其潛在（第一個分析階段）。 此動作等同於選取&#x200B;**[!UICONTROL Estimate the population to be targeted]**&#x200B;選項，並在透過&#x200B;**傳遞**&#x200B;將傳遞傳送到主要目標時按一下&#x200B;**[!UICONTROL Analyze]**。
   * **[!UICONTROL Prepare]**：此選項可讓您執行完整分析程式（目標計算與內容準備）。 不會傳送傳遞。 此動作等同於選取&#x200B;**[!UICONTROL Deliver as soon as possible]**&#x200B;選項，並在傳送傳遞至具有&#x200B;**傳遞**&#x200B;的主要目標時按一下&#x200B;**[!UICONTROL Analyze]**。
   * **[!UICONTROL Send a proof]**：此選項可讓您傳送傳遞的證明。 此動作等同於在具有&#x200B;**傳遞**&#x200B;的傳遞工具列中按一下&#x200B;**[!UICONTROL Send a proof]**&#x200B;按鈕
   * **[!UICONTROL Prepare and start]**：此選項會啟動完整分析程式（目標計算與內容準備）並傳送傳遞。 此動作等同於使用&#x200B;**傳遞**&#x200B;將傳遞傳送到主要目標時按一下&#x200B;**[!UICONTROL Deliver as soon as possible]**、**[!UICONTROL Analyze]**&#x200B;和&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;選項。

   在工作流程中繼續使用的&#x200B;**[!UICONTROL Act on a delivery]**&#x200B;活動可讓您啟動啟動啟動傳送（目標計算、內容準備、傳送）所需的所有剩餘步驟。 如需詳細資訊，請參閱[傳遞控制](delivery-control.md)。

   也可使用下列選項：

   * **[!UICONTROL Generate an outbound transition]**

     建立將在執行結束時啟用的出站轉變。 您可以選擇是否要擷取傳出傳遞的目標。

   * **[!UICONTROL Do not recover target]**

     不會復原傳出傳遞動作的目標。

   * **[!UICONTROL Processing errors]**

     請參閱[傳遞控制](delivery-control.md)。

   **指令碼**&#x200B;索引標籤可讓您修改傳遞引數。

   ![](assets/edit_diffusion_fil_script.png)

## 範例：傳遞工作流程 {#example--delivery-workflow}

建立新工作流程並新增活動，如下圖所示：

![](assets/new-workflow-5.png)

開啟&#x200B;**傳遞**&#x200B;活動並定義屬性，如下所示：

* 在&#x200B;**[!UICONTROL Delivery]**&#x200B;區段中，選取&#x200B;**[!UICONTROL New, created from a template]**&#x200B;並選取傳遞範本。
* 在&#x200B;**[!UICONTROL Recipients]**&#x200B;區段中，選取&#x200B;**[!UICONTROL Specified in the delivery]**。
* 在&#x200B;**[!UICONTROL Action to execute]**&#x200B;區段中，保留&#x200B;**[!UICONTROL Prepare]**&#x200B;選項。

![](assets/new-workflow-param-delivery.png)

按一下&#x200B;**[!UICONTROL OK]**&#x200B;以關閉屬性視窗。 您剛剛設定了活動，包括根據將在其內指定目標的傳遞範本建立和準備新傳遞。

開啟&#x200B;**核准**&#x200B;活動並定義屬性，如下所示：

1. 在&#x200B;**[!UICONTROL Assignment type]**&#x200B;欄位中，選取您已註冊的群組。 如果您是使用「管理員」帳戶連線，請選取「管理」群組。
1. 接下來，輸入標題，並在訊息本文中插入下列文字：

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   此訊息包含以JavaScript撰寫的運算式： **[!UICONTROL vars.recCount]**&#x200B;代表傳遞前一個任務所定位的收件者數目。 如需JavaScript運算式的詳細資訊，請參閱[JavaScript指令碼和範本](javascript-scripts-and-templates.md)。

   ![](assets/new-workflow-param-validation.png)

   [核准](approval.md)中詳細說明了核准任務。

## 輸入引數 {#input-parameters}

傳遞識別碼，如果在&#x200B;**[!UICONTROL Delivery]**&#x200B;區段中選取&#x200B;**[!UICONTROL Specified in the transition]**&#x200B;選項。

* deliveryId
* tableName
* 結構描述

每個傳入事件都必須指定由這些引數定義的目標。

>[!NOTE]
>
>只有在&#x200B;**[!UICONTROL Recipients]**&#x200B;區段中選取&#x200B;**[!UICONTROL Specified by inbound event(s)]**&#x200B;選項時，此引數才會出現。

* 檔案名稱

  在&#x200B;**[!UICONTROL Recipients]**&#x200B;區段中選取&#x200B;**[!UICONTROL File(s) specified by inbound event(s)]**&#x200B;選項時所產生檔案的完整名稱。

* contentId

  如果在&#x200B;**[!UICONTROL Content]**&#x200B;區段中選取&#x200B;**[!UICONTROL Specified by inbound events]**&#x200B;選項，則為內容識別碼。

## 輸出引數 {#output-parameters}

* tableName
* 結構描述
* recCount

這組三個值可識別傳送產生的目標。 **[!UICONTROL tableName]**&#x200B;是記憶目標識別碼的資料表名稱，**[!UICONTROL schema]**&#x200B;是母體的結構描述（通常是nms：recipient），而&#x200B;**[!UICONTROL recCount]**&#x200B;是資料表中的元素數目。

與補充關聯的轉變有相同的引數。

>[!NOTE]
>
>選取&#x200B;**[!UICONTROL Do not recover target]**&#x200B;選項時沒有輸出引數。
