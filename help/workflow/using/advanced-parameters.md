---
product: campaign
title: 高級參數
description: 高級參數
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 5%

---

# 高級參數{#advanced-parameters}



活動的屬性畫面有&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤，可讓您定義發生錯誤時的行為、活動的執行期間，以及輸入初始化指令碼。 此標籤有兩個版本：

* 簡化版本（針對執行個體的&#x200B;**[!UICONTROL Start]**&#x200B;和&#x200B;**[!UICONTROL End]**&#x200B;活動）

  ![](assets/wf-advanced-basic.png)

* 更詳細的版本（例如&#x200B;**[!UICONTROL Query]**&#x200B;活動的）

  ![](assets/wf-advanced-full.png)

將在&#x200B;**[!UICONTROL Advanced]**&#x200B;索引標籤中輸入的欄位在以下各節中詳細說明。

## 名稱 {#name}

此欄位包含活動的內部名稱。

## 影像 {#image}

此欄位可讓您變更連結至活動的影像。 如需詳細資訊，請參閱[變更活動影像](managing-activity-images.md)。

## 執行 {#execution}

此欄位可讓您定義觸發任務時要執行的動作。 有三個可能的選項：

通常在購物車中按一下右鍵活動以選取這些選項。

* **[!UICONTROL Normal]**：活動會照常執行。
* **[!UICONTROL Do not activate]**：此任務和下列所有任務（在相同分支中）都不會執行。
* **[!UICONTROL Activate but do not execute]**：此任務和下列所有任務（在相同分支中）會自動停止。 如果您想在任務啟動時到達該處，這會很有用。 若要手動執行工作，請在活動上按一下滑鼠右鍵，然後選取&#x200B;**[!UICONTROL Normal execution]**。

## 相似性 {#affinity}

您可以選擇在特定電腦上強制執行工作流程或工作流程活動。 若要這麼做，您必須在工作流程或相關活動的層級定義一或多個屬性。

高可用性工作流程組態在此[區段](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)中有詳細說明。


## 最大 執行期間 {#max--execution-period}

此欄位可讓您設定當任務花費太久時的警告。 這不會影響工作流程作業。 如果工作在&#x200B;**[!UICONTROL Max. execution period]**&#x200B;結束前未完成，**[!UICONTROL Instance monitoring]**&#x200B;頁面會顯示此工作流程的警告。 透過首頁的&#x200B;**[!UICONTROL Monitoring]**&#x200B;索引標籤存取此頁面。

## 行為 {#behavior}

此欄位可讓您定義要套用於使用非同步工作的行為。 您有兩個選擇：

* **[!UICONTROL Several tasks authorized]**：可以同時執行數個工作，即使第一個工作尚未完成。
* **[!UICONTROL The current task has priority]**：進行中的任務優先順序。 只要任務仍在進行中，就不會執行其他任務。

## 時區 {#time-zone}

此欄位可讓您選取活動的時區。 有關詳細資訊： [管理時區](managing-time-zones.md)。

## 發生錯誤時 {#in-case-of-errors}

此欄位可讓您定義活動發生錯誤時要執行的動作。 您有兩個選擇：

* **[!UICONTROL Suspend the process]**：工作流程已自動停止。 其狀態變更為&#x200B;**[!UICONTROL Failed]**。 問題解決後，請重新啟動工作流程。
* **[!UICONTROL Ignore]**：此任務和下列所有任務（在相同分支中）都不會執行。 這對於週期性任務非常有用。 如果分支有排程器放在上游，它將在下一個執行日期照常啟動。
* **[!UICONTROL Abort on error]**：工作流程已自動停止，無法重新啟動。 其狀態變更為&#x200B;**[!UICONTROL Failed]**。

## 初始化指令碼 {#initialization-script}

此欄位可讓您初始化變數或修改活動屬性。 如需詳細資訊，請參閱： [JavaScript指令碼和範本](javascript-scripts-and-templates.md)。

## 備註 {#comment}

**[!UICONTROL Comment]**&#x200B;欄位是免費欄位，可讓您新增說明。
