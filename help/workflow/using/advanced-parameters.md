---
solution: Campaign Classic
product: campaign
title: 高級參數
description: 高級參數
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%

---

# 高級參數{#advanced-parameters}

活動的屬性螢幕有一個&#x200B;**[!UICONTROL Advanced]**&#x200B;頁籤，可讓您定義出錯時的行為，即活動的執行期；並讓您輸入初始化指令碼。 此標籤有兩個版本：

* 簡化版（例如&#x200B;**[!UICONTROL Start]**&#x200B;和&#x200B;**[!UICONTROL End]**&#x200B;活動）

   ![](assets/wf-advanced-basic.png)

* 更詳細的版本（例如&#x200B;**[!UICONTROL Query]**&#x200B;活動）

   ![](assets/wf-advanced-full.png)

**[!UICONTROL Advanced]**&#x200B;標籤中要輸入的欄位在以下幾節中有詳細說明。

## 名稱 {#name}

此欄位包含活動的內部名稱。

## 影像 {#image}

此欄位可讓您變更連結至活動的影像。 有關詳情，請參閱：[管理活動映像](../../workflow/using/managing-activity-images.md)。

## 執行 {#execution}

此欄位可讓您定義觸發任務時要執行的動作。 有三種可能的選項：

這些選項通常在購物車中以滑鼠右鍵按一下活動來選取。

* **[!UICONTROL Normal]**:活動照常執行。
* **[!UICONTROL Do not activate]**:不會執行此任務和以下所有任務（在同一分支中）。
* **[!UICONTROL Activate but do not execute]**:此任務和以下所有任務（在同一分支中）都將自動停止。如果您希望在任務啟動時在該位置，則此選項會很有用。 要手動執行任務，請按一下右鍵該活動並選擇&#x200B;**[!UICONTROL Normal execution]**。

## 相關性{#affinity}

您可以選擇強制在特定電腦上執行工作流或工作流活動。 為此，您必須在工作流或相關活動的級別定義一個或多個傾向性。

高可用性工作流配置在[部分](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)中有詳細說明。


## Max. 執行期{#max--execution-period}

此欄位可讓您在工作過長時設定警告。 它不會影響工作流操作。 如果&#x200B;**[!UICONTROL Max. execution period]**&#x200B;結束前任務尚未完成，則&#x200B;**[!UICONTROL Instance monitoring]**&#x200B;頁面將顯示此工作流的警告。 此頁可通過首頁的&#x200B;**[!UICONTROL Monitoring]**&#x200B;頁籤訪問。

## 行為{#behavior}

此欄位可讓您定義要套用至使用非同步工作的行為。 有兩種可能的選項：

* **[!UICONTROL Several tasks authorized]**:即使第一個任務未完成，也可以一次執行多個任務。
* **[!UICONTROL The current task has priority]**:正在進行的任務優先。只要任務正在進行中，就不會執行任何其他任務。

## 時區 {#time-zone}

此欄位可讓您選取活動的時區。 如需詳細資訊：[管理時區](../../workflow/using/managing-time-zones.md)。

## 發生錯誤時{#in-case-of-errors}

此欄位可讓您定義活動有錯誤時要執行的動作。 有兩種可能的選項：

* **[!UICONTROL Stop the process]**:工作流程會自動停止。其狀態變更為&#x200B;**[!UICONTROL Failed]**。 問題解決後，請重新啟動工作流程。
* **[!UICONTROL Ignore]**:不會執行此任務和以下所有任務（在同一個分支中）。這對於循環性工作非常有用。 如果分支的調度程式位於上游，則該調度程式將在下次執行日期照常啟動。

## 初始化指令碼{#initialization-script}

此欄位可讓您初始化變數或修改活動屬性。 有關詳情，請參閱：[JavaScript指令碼和範本](../../workflow/using/javascript-scripts-and-templates.md)。

## 注釋{#comment}

**[!UICONTROL Comment]**&#x200B;欄位是可讓您新增說明的免費欄位。
