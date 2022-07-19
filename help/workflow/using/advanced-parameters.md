---
product: campaign
title: 高級參數
description: 高級參數
feature: Workflows, Data Management
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 2%

---

# 高級參數{#advanced-parameters}

![](../../assets/v7-only.svg)

活動的屬性螢幕具有 **[!UICONTROL Advanced]** 頁籤，用於在出錯時定義行為，即活動的執行期；並輸入初始化指令碼。 此頁籤有兩個版本：

* 簡化版本( **[!UICONTROL Start]** 和 **[!UICONTROL End]** 例如活動)

   ![](assets/wf-advanced-basic.png)

* 更詳細的版本( **[!UICONTROL Query]** 例如，活動

   ![](assets/wf-advanced-full.png)

要在 **[!UICONTROL Advanced]** 頁籤

## 名稱 {#name}

此欄位包含活動的內部名稱。

## 影像 {#image}

此欄位允許您更改連結到活動的影像。 有關此內容的詳細資訊，請參閱 [更改活動映像](managing-activity-images.md)。

## 執行 {#execution}

此欄位用於定義觸發任務時要執行的操作。 有三種可能的選擇：

這些選項通常通過按一下右鍵活動在購物車中選擇。

* **[!UICONTROL Normal]**:該活動照常執行。
* **[!UICONTROL Do not activate]**:此任務和以下所有任務（位於同一分支中）不會執行。
* **[!UICONTROL Activate but do not execute]**:此任務和以下所有任務（在同一分支中）將自動停止。 如果希望在任務啟動時存在，則此功能將非常有用。 要手動執行任務，請按一下右鍵活動並選擇 **[!UICONTROL Normal execution]**。

## 親和 {#affinity}

您可以選擇強制在特定電腦上執行工作流或工作流活動。 為此，必須在工作流或相關活動的層定義一個或多個優先順序。

高可用性工作流配置在此中詳述 [節](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。


## 麥克斯。 執行期 {#max--execution-period}

此欄位允許您為任務過長時設定警告。 它不會影響工作流操作。 如果任務在 **[!UICONTROL Max. execution period]** 結束了， **[!UICONTROL Instance monitoring]** 頁面將顯示此工作流的警告。 通過 **[!UICONTROL Monitoring]** 的子菜單。

## 行為 {#behavior}

此欄位用於定義要應用於使用非同步任務的行為。 有兩種可能的選擇：

* **[!UICONTROL Several tasks authorized]**:即使第一個任務尚未完成，也可以同時執行多個任務。
* **[!UICONTROL The current task has priority]**:正在執行的任務優先。 只要正在執行任務，就不會執行其他任務。

## 時區 {#time-zone}

此欄位允許您選擇活動的時區。 有關此內容的詳細資訊： [管理時區](managing-time-zones.md)。

## 如果出錯 {#in-case-of-errors}

此欄位用於定義在活動有錯誤時要執行的操作。 有兩種可能的選擇：

* **[!UICONTROL Suspend the process]**:工作流將自動停止。 其狀態更改為 **[!UICONTROL Failed]**。 解決問題後，重新啟動工作流。
* **[!UICONTROL Ignore]**:此任務和以下所有任務（位於同一分支中）不會執行。 這對於循環任務可能很有用。 如果分支有調度程式位於上游，則它將在下一個執行日期照常啟動。
* **[!UICONTROL Abort on error]**:工作流自動停止，無法重新啟動。 其狀態更改為 **[!UICONTROL Failed]**。

## 初始化指令碼 {#initialization-script}

此欄位用於初始化變數或修改活動屬性。 有關詳細資訊，請參閱： [JavaScript指令碼和模板](javascript-scripts-and-templates.md)。

## 注釋 {#comment}

的 **[!UICONTROL Comment]** 欄位是一個可用欄位，用於添加說明。
