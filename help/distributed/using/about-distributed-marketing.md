---
product: campaign
title: 行銷活動分散式行銷
description: 開始使用分散式行銷
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: c166409b-e040-491e-840a-a41310935d75
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---

# 開始使用分散式行銷{#about-distributed-marketing}

![](../../assets/v7-only.svg)

Adobe Campaign提供&#x200B;**Distributed Marketing**&#x200B;應用程式，用於實作中央實體（總部、行銷部門等）之間的合作行銷活動 和地方實體（銷售點、地區代理等）。 此合作以共用工作區為基礎（稱為&#x200B;**[!UICONTROL list of campaign packages]**），集中建立的行銷活動範本和執行個體可提供給當地實體。

中央實體提供本地實體可能使用的促銷活動。 促銷活動會以代表本機或協作促銷活動的套件來實化。 若要使用促銷活動，本機實體必須排序促銷活動，且必須核准訂單。

>[!CAUTION]
>
>「分佈式行銷」模組是&#x200B;**Campaign**&#x200B;選項。 請檢查您的授權合約。

## 術語 {#terminology}

* **中央實體**

   中央實體由負責指定通信和協助地方實體執行其營銷活動的營銷經營者組成。

   分散式行銷模組可讓中央實體：

   * 為本機實體設定行銷活動套件，
   * 提高本地實體在客戶/潛在客戶通信、目標定位、內容等選擇方面的自主性。
   * 管理和控製成本，
   * 處理一個機構網路。

* **本地實體**

   本地實體可以是特定本地運營商（國家或地區經理、品牌經理等）的代理、商店或組。

   分散式行銷可讓本地實體擁有更多自主權，同時最佳化執行成本。

* **本地化**

   本地化是本機實體修改促銷活動目標和內容的能力。 本地化的可能級別取決於促銷活動類型及其實施。

* **行銷活動套件清單**

   促銷活動套件清單包含本機實體可用的促銷活動。

* **行銷活動套件**

   由中央實體建立的範本（或促銷活動例項），並可供一組本機實體使用。

* **本機行銷活動**

   本機促銷活動是從&#x200B;**[!UICONTROL campaign packages]**&#x200B;清單中參考的範本，以&#x200B;**特定執行排程**&#x200B;建立的例項。 其目標是使用由中央實體設定和設定的行銷活動範本，來滿足本機通訊需求。

   地方實體的自治程度取決於所使用的實施。

   請參閱[建立本機促銷活動](creating-a-local-campaign.md)。

* **協作行銷活動**

   協作促銷活動是由中央實體定義&#x200B;**執行排程的促銷活動，本機實體可使用此中央實體。**&#x200B;每個本地實體的內容保持不變，但成本會共用。 若要參與，當地實體會訂閱協作促銷活動。

   * **[!UICONTROL Collaborative campaign (by form)]**:建議最多300個當地實體的促銷活動。本機實體可以輸入預先定義的參數，以在網路表單中鎖定目標和內容個人化。 表單可以是Adobe Campaign表單或外部表單（外聯網客戶端）。 功能管理員可以根據整合器定義的表單範本來定義和配置表單。 若要排序促銷活動，本機實體只需要Web存取權。
   * **[!UICONTROL Collaborative campaign (by campaign)]**:針對數十個地方實體的活動建議。此類型的促銷活動會為每個本機實體建立子促銷活動。 當中央實體核准&#x200B;**[!UICONTROL collaborative campaign (by campaign)]**&#x200B;後，該促銷活動便可供本機實體使用，供其修改。 執行會在父促銷活動和子促銷活動之間自動同步。 本機實體必須擁有執行個體的存取權，才能排序促銷活動並參與其中。
   * **[!UICONTROL Collaborative campaign (by target approval)]**:建議開展針對數千個地方實體的活動。本地實體接收由中央實體預定義的聯繫人清單。 本機實體會根據促銷活動內容，透過網路表單決定是否保留特定連絡人。 從所選接觸的清單中推導出局部圖元。 要參與此活動，本地實體只需要Web訪問。
   * **[!UICONTROL Collaborative campaign (simple)]**:此模式可確保與舊版的特定執行程式相容。

   請參閱[建立協作促銷活動](creating-a-collaborative-campaign.md)。

**訂購行銷活動套件**

如果本機實體註冊促銷活動，則會將此訂單重新分組與促銷活動本地化相關的所有資訊。

## 工作區 {#workspace}

可從&#x200B;**Campaigns**&#x200B;標籤存取促銷活動套件清單：按一下&#x200B;**[!UICONTROL Campaign packages]**&#x200B;連結。

![](assets/mkg_dist_home_local_op.png)

此視窗可讓所有當地營運商檢視其當地代理商可用的促銷活動。

對於中央機構，此窗口顯示促銷活動包清單中可用的所有包，並提供用於編輯清單的附加連結。

## 運算子和實體 {#operators-and-entities}

首先，通過&#x200B;**[!UICONTROL Access management]**&#x200B;資料夾指定中央實體和本地實體運算子。

![](assets/s_advuser_mkg_dist_tree.png)

### 運算子 {#operators}

您需要建立中央運算子和本機運算子。

中央運算子必須屬於&#x200B;**[!UICONTROL Central management]**&#x200B;運算子組，或具有名為&#x200B;**[!UICONTROL CENTRAL]**&#x200B;的權限。

本地運算子必須屬於&#x200B;**[!UICONTROL Local management]**&#x200B;運算子組，或具有名為&#x200B;**[!UICONTROL LOCAL]**&#x200B;的權限。 它們還必須與本地實體連結。

![](assets/s_advuser_mkg_dist_local_create.png)

### 組織實體 {#organizational-entities}

若要建立組織實體，請按一下&#x200B;**[!UICONTROL Administration > Access management > Organizational entities]**&#x200B;節點，然後按一下實體清單上方的&#x200B;**[!UICONTROL New]**&#x200B;圖示。

![](assets/s_advuser_mkg_dist_local_list.png)

每個組織實體都包含身分識別資訊（標籤、內部名稱、聯絡資訊等） 和訂單審批流程中涉及的組。 這些定義於&#x200B;**[!UICONTROL General]**&#x200B;標籤中的&#x200B;**[!UICONTROL Notifications and approvals]**&#x200B;區段中。

* 定義套件通知群組：每次將新套件新增至促銷活動套件清單時，以及每次有促銷活動可用時，此群組中的運算子都會收到通知。
* 選擇負責批准訂單的審核者組，即負責批准本地實體訂購的促銷活動的審核者。
* 最後，選擇負責批准本地促銷活動（目標、內容、預算等）的審核者組。 根據範本，在排序促銷活動時可將此群組新增至。

>[!NOTE]
>
>核准流程顯示在[核准流程](creating-a-local-campaign.md#approval-process)部分。

## 實作 {#implementation}

分散式行銷促銷活動是由中央實體建立和發佈。 地方實體和中央實體可視需要使用它們。

實施程式取決於所使用的促銷活動套件類型和本機實體委派層級。

### 整合商任務 {#integrator-side}

1. 建立本地實體。
1. 將收件者與管理本機實體的運算子連結。

   ![](assets/mkg_dist_local_entity_association.png)

1. 指定本機實體的權限和瀏覽規則
1. 指定促銷活動本地化所需的欄位集：

   * 目標定義和最大大小，
   * 內容定義，
   * 執行排程（聯繫日期和提取日期）,**僅針對本機運算子**,
   * 訂購架構的擴充功能以及所有必要的其他欄位。

1. 建立Web表單(Adobe或外聯網)，允許您顯示本地化參數、評估目標和預算，以及預覽內容並批准訂單。

   對於&#x200B;**協作促銷活動（依目標核准）**，建立將儲存每個本機實體核准的表格。

### 功能管理員任務 {#functional-administrator-side}

建立每個促銷活動時，必須執行這些步驟。

1. 使用用於促銷活動本地化的欄位更新表單。
1. 從適當的促銷活動範本（協作促銷活動）建立例項，或複製促銷活動範本（本機促銷活動）。
1. 使用本地化欄位和表單參考設定促銷活動。
1. 發佈促銷活動。

### 本地運算子任務 {#local-operator-side}

必須對每個促銷活動執行這些步驟。

1. 收到促銷活動套件可用性的通知後，請指定促銷活動的位置（選用）。
1. 評估目標、預算等。
1. 預覽促銷活動內容。
1. 排序促銷活動。
