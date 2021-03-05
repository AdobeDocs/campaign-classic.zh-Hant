---
solution: Campaign Classic
product: campaign
title: 行銷宣傳目標受眾
description: 瞭解如何定義行銷宣傳的受眾
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 1%

---


# 選取促銷活動的對象{#marketing-campaign-deliveries}

在行銷促銷活動中，您可以針對每個傳送定義：

* 對象——在[在工作流程中建立對象](#building-the-main-target-in-a-workflow)和[選擇目標人口](#selecting-the-target-population)中瞭解更多資訊。
* 控制組——瞭解[本節](#defining-a-control-group)的詳細內容。
* 種子位址——請參閱[本節](../../delivery/using/about-seed-addresses.md)瞭解更多資訊。

有些資訊可從[促銷活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates)繼承。

若要建立傳送目標，您可以為資料庫中的收件者定義篩選條件。 此收件者選擇模式顯示在[本節](../../delivery/using/steps-defining-the-target-population.md)中。

## 傳送至群組

您可以將人口匯入清單，然後在傳送中定位此清單。 要執行此操作，請遵循下列步驟：

1. 編輯相關的傳送，然後按一下&#x200B;**[!UICONTROL To]**&#x200B;連結以變更目標人口。

1. 在&#x200B;**[!UICONTROL Main target]**&#x200B;標籤中，選擇&#x200B;**[!UICONTROL Defined via the database]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選擇收件人。

![](assets/s_user_target_group_add.png)

1. 選擇&#x200B;**[!UICONTROL A list of recipients]**&#x200B;並按一下&#x200B;**[!UICONTROL Next]**&#x200B;以選擇它。

![](assets/s_user_target_group_next.png)

## 在促銷活動工作流程中建立對象{#building-the-main-target-in-a-workflow}

傳送的主要目標也可以在促銷活動工作流程中定義：此圖形環境可讓您使用查詢、測試和運算子來建立目標：聯合、重複資料消除、共用等。

>[!IMPORTANT]
>
>您不得在促銷活動中新增超過28個工作流程。 超過此限制後，介面中將無法顯示其他工作流程，並可能產生錯誤。

### 建立工作流{#creating-a-targeting-workflow}

您可以透過工作流程中圖形順序的篩選條件組合來建立定位。 您可以建立人口和子人口，並根據您的需求進行定位。 若要顯示工作流程編輯器，請按一下促銷活動控制面板中的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤。

![](assets/s_ncs_user_edit_op_wf_link.png)

目標種群通過在工作流中放置的一個或多個查詢從Adobe Campaign資料庫中提取。 要瞭解如何構建查詢，請參閱[本節](../../workflow/using/query.md)。

您可以透過「聯合」、「交叉點」、「共用」、「排除」等方塊來啟動查詢並共用人口族群。

從工作區左側的清單中選擇對象，並將其連結以構建目標。

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

在圖中，在圖中連結目標構建所需的定位和調度查詢。 在進行建設時，您可以執行定位，以檢查從資料庫擷取的人口。

>[!NOTE]
>
>定義查詢的示例和過程在[本節](../../workflow/using/query.md)中介紹。

編輯器的左側部分包含表示活動的圖形對象庫。 第一個標籤包含定位活動，第二個標籤包含流量控制活動，這些活動偶爾會用來協調定位活動。

您可透過圖編輯器工具列存取定位工作流程執行和格式設定功能。

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>[使用工作流程自動化指南中詳細說明了用於構建圖以及所有顯示和佈局功能的活動。](../../workflow/using/architecture.md)

您可以為單一促銷活動建立數個定位工作流程。 要添加工作流，請執行以下操作：

1. 前往工作流程建立區的左上角區段，按一下滑鼠右鍵，然後選取&#x200B;**[!UICONTROL Add]**。 您也可以使用位於此區域上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕。

   ![](assets/s_ncs_user_add_a_wf.png)

1. 選擇&#x200B;**[!UICONTROL New workflow]**&#x200B;範本並命名此工作流。
1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;確認建立工作流，然後建立此工作流的圖。

### 執行工作流{#executing-a-workflow}

定位工作流程可透過工具列的&#x200B;**[!UICONTROL Start]**&#x200B;按鈕手動啟動，但您必須擁有適當的權限。

可以根據調度（調度器）或事件（外部信號、檔案導入等）對目標進行寫程式以用於自動執行。

與執行定位工作流程（啟動、停止、暫停等）相關的動作 are **asynchronous** processes:命令將保存，當伺服器可用來應用該命令時，該命令將立即生效。

工具列圖示可讓您針對定位工作流程的執行採取相關動作。

* 啟動或重新啟動

   * **[!UICONTROL Start]**&#x200B;圖示可讓您啟動定位工作流程。 當您按一下此圖示時，所有沒有輸入轉場的活動都會啟動（端點跳轉除外）。

      ![](assets/s_user_segmentation_start.png)

      伺服器會將請求納入考量，如其狀態所示：

      ![](assets/s_user_segmentation_start_status.png)

      進程狀態更改為&#x200B;**[!UICONTROL Started]**。

   * 您可以透過適當的工具列圖示，重新啟動定位工作流程。 如果&#x200B;**[!UICONTROL Start]**&#x200B;圖示不可用，例如當正在停止定位工作流時，此命令可能很有用。 在這種情況下，按一下&#x200B;**[!UICONTROL Restart]**&#x200B;表徵圖以預測重新啟動。 伺服器會將請求納入考量，其狀態如下：

      ![](assets/s_user_segmentation_restart_status.png)

      然後，進程進入&#x200B;**[!UICONTROL Started]**&#x200B;狀態。

* 停止或暫停

   * 工具列圖示可讓您停止或暫停進行中的定位工作流程。

      按一下&#x200B;**[!UICONTROL Pause]**&#x200B;時，進行中的操作&#x200B;**[!UICONTROL are not]**&#x200B;暫停，但直到下次重新啟動後才啟動其他活動。

      ![](assets/s_user_segmentation_pause.png)

      伺服器會考慮到該命令，其狀態如下：

      ![](assets/s_user_segmentation_pause_status.png)

      您也可以在定位工作流程執行到達特定活動時自動暫停。 若要這麼做，請以滑鼠右鍵按一下要暫停定位工作流程的活動，然後選取&#x200B;**[!UICONTROL Enable but do not execute]**。

      ![](assets/s_user_segmentation_donotexecute.png)

      此配置由特殊表徵圖顯示。

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >此選項在進階定位促銷活動設計和測試階段中很實用。

      按一下&#x200B;**[!UICONTROL Start]**&#x200B;以繼續執行。

   * 按一下&#x200B;**[!UICONTROL Stop]**&#x200B;表徵圖可停止正在執行的操作。

      ![](assets/s_user_segmentation_stop.png)

      伺服器會考慮到該命令，其狀態如下：

      ![](assets/s_user_segmentation_stop_status.png)
   您也可以在執行到達活動時自動停止定位工作流程。 若要這麼做，請以滑鼠右鍵按一下將停止定位工作流程的活動，然後選取&#x200B;**[!UICONTROL Do not activate]**。

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   此配置由特殊表徵圖顯示。

   >[!NOTE]
   >
   >此選項在進階定位促銷活動設計和測試階段中很實用。

* 無條件停止

   在「檔案總管」中，選取&#x200B;**[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]**&#x200B;以存取每個促銷活動工作流程並採取行動。

   按一下&#x200B;**[!UICONTROL Actions]**&#x200B;表徵圖並選擇&#x200B;**[!UICONTROL Unconditional]**&#x200B;停止，可以無條件停止工作流。 此動作會終止您的促銷活動工作流程。

   ![](assets/s_user_segmentation_stop_unconditional.png)

## 添加控制組{#defining-a-control-group}

控制組是不接收交貨的人口；它可用來透過與已收到傳送的目標人口的行為比較，來追蹤傳送後的行為和促銷活動影響。

控制組可從主目標提取和／或來自特定組或查詢。

### 啟用促銷活動的控制群組{#activating-the-control-group-for-a-campaign}

您可以在促銷活動層級定義控制群組，在此情況下，控制群組將套用至相關促銷活動的每個傳送。

1. 編輯相關促銷活動，然後按一下&#x200B;**[!UICONTROL Edit]**&#x200B;標籤。
1. 按一下 **[!UICONTROL Advanced campaign settings]**。

   ![](assets/s_ncs_user_edit_op_target.png)

1. 選擇&#x200B;**[!UICONTROL Enable and edit control group configuration]**&#x200B;選項。
1. 按一下&#x200B;**[!UICONTROL Edit...]**&#x200B;配置控制組。

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

配置過程在[從主目標](#extracting-the-control-group-from-the-main-target)提取控制組和[添加控制組](#adding-a-population)中顯示。

### 啟用傳送{#activating-the-control-group-for-a-delivery}的控制群組

您可以在傳送層定義控制群組，在此情況下，控制群組將套用至相關促銷活動的每個傳送。

依預設，在促銷活動層級定義的控制群組設定會套用至該促銷活動的每個傳送。 不過，您可以針對個別傳送調整控制群組。

>[!NOTE]
>
>如果您已為促銷活動定義控制群組，而且您也將其設定為連結至此促銷活動的傳送，則只會套用為傳送定義的控制群組。

1. 編輯相關的傳送，然後按一下&#x200B;**[!UICONTROL Email parameters]**&#x200B;區段中的&#x200B;**[!UICONTROL To]**&#x200B;連結。

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. 按一下&#x200B;**[!UICONTROL Control group]**&#x200B;頁籤，然後選擇&#x200B;**[!UICONTROL Enable and edit control group configuration]**。
1. 按一下&#x200B;**[!UICONTROL Edit...]**&#x200B;配置控制組。

配置過程在[從主目標](#extracting-the-control-group-from-the-main-target)提取控制組和[添加控制組](#adding-a-population)中顯示。

### 從主目標{#extracting-the-control-group-from-the-main-target}中提取控制組

您可以從傳送的主要目標擷取收件者。 在這種情況下，收件人將從受此配置影響的傳送動作目標中取用。 此提取可以是隨機的，也可以是排序收件者的結果。

![](assets/s_ncs_user_extract_from_target_population.png)

若要擷取控制群組，請啟用促銷活動或傳送的控制群組，並選取下列其中一個選項：**[!UICONTROL Activate random sampling]**&#x200B;或&#x200B;**[!UICONTROL Keep only the first records after sorting]**。

* **[!UICONTROL Activate random sampling]** :此選項會將隨機抽樣套用至目標人口中的收件者。如果您接著將臨界值設為100，則控制群組將由100個從目標人口中隨機選取的收件者組成。 隨機抽樣取決於資料庫引擎。
* **[!UICONTROL Keep only the first records after sorting]**：此選項可讓您根據一或多個排序順序定義限制。如果您選擇&#x200B;**[!UICONTROL Age]**&#x200B;欄位作為排序標準，然後將100定義為臨界值，則控制群組將由100個最年輕的收件者組成。 例如，定義一個控制群組，其中包含購物次數較少的收件者或經常購物的收件者，並比較其行為與已聯絡的收件者的行為。

按一下&#x200B;**[!UICONTROL Next]**&#x200B;定義排序順序（如果需要）並選擇收件者限制模式。

![](assets/s_ncs_user_edit_op_target_param.png)

此設定等同於工作流程中的共用活動，可讓您將目標分割為子集。 控制組是這些子集之一。 如需詳細資訊，請參閱[本節](../../workflow/using/architecture.md)。

### 將新人口用作控制組{#adding-a-population}

您可以定義要用作控制組的新人口。 此人口族群可來自一組收件者，或您可透過特定查詢建立。

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Adobe Campaign查詢編輯器顯示在[此部分](../../workflow/using/query.md)中。


#### 教學課程影片{#create-email-video}

此影片說明如何在Adobe Campaign建立促銷活動和電子郵件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

其他促銷活動操作影片可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。