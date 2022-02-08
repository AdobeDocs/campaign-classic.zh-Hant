---
product: campaign
title: 市場活動分佈式營銷
description: 開始分佈式營銷
feature: Distributed Marketing
exl-id: c166409b-e040-491e-840a-a41310935d75
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---

# 開始分佈式營銷{#about-distributed-marketing}

![](../../assets/v7-only.svg)

Adobe Campaign提供 **分佈式營銷** 中央單位（總部、營銷部門等）開展合作活動的申請 地方實體（銷售點、地區代理等）。 此協作基於共用工作區，稱為 **[!UICONTROL list of campaign packages]**，其中集中建立的市場活動模板和實例將提供給本地實體。

中央實體提供本地實體可能使用的市場活動。 市場活動由代表本地市場活動或協作市場活動的包實現。 要使用市場活動，本地實體必須訂購該市場活動，並且必須批准該訂單。

>[!CAUTION]
>
>分佈式營銷模組是 **活動** 的雙曲餘切值。 請檢查您的授權合約。

## 術語 {#terminology}

* **中央實體**

   中央單位由負責指定通信和協助地方單位開展營銷活動的營銷經營者組成。

   分佈式營銷模組允許中心實體：

   * 為本地實體設定市場營銷活動包，
   * 提高本地實體在客戶/潛在客戶溝通、目標、內容等方面的自主性。
   * 管理和控製成本，
   * 處理一個機構網路。

* **本地實體**

   當地實體可以是特定當地運營商（國家或地區經理、品牌經理等）的代理、商店或組。

   分佈式市場營銷使本地實體在優化執行成本的同時擁有更大的自主權。

* **本地化**

   本地化是本地實體修改市場活動目標和內容的能力。 本地化的可能級別取決於活動類型及其實施。

* **市場活動包清單**

   市場活動包清單包含可用於本地實體的市場活動。

* **市場活動包**

   由中央實體建立的模板（或市場活動實例），可用於一組本地實體。

* **本地活動**

   本地市場活動是根據清單中引用的模板建立的實例 **[!UICONTROL campaign packages]** 帶 **特定執行計畫**。 其目的是使用由中央實體設定和配置的活動模板來滿足本地通信需求。

   地方實體的自治程度取決於所採用的實施。

   請參閱 [建立本地市場活動](creating-a-local-campaign.md)。

* **協作活動**

   協作活動是指 **定義執行計畫** 中央實體確認，而本地實體可使用。 對於每個本地實體，內容保持不變，但成本是共用的。 要參與，本地實體將訂閱協作市場活動。

   * **[!UICONTROL Collaborative campaign (by form)]**:建議開展多達300個地方實體的活動。 本地實體可以在Web表單中輸入用於目標和內容個性化的預定義參數。 表單可以是Adobe Campaign表單或外部表單（外聯網客戶端）。 功能管理員可以根據整合商定義的表單模板來定義和配置表單。 要訂購該活動，本地實體只需要訪問Web即可。
   * **[!UICONTROL Collaborative campaign (by campaign)]**:建議開展針對數十個地方實體的活動。 此類市場活動為每個本地實體建立子市場活動。 一旦 **[!UICONTROL collaborative campaign (by campaign)]** 由中央實體批准，市場活動可供本地實體使用，而本地實體可以對其進行修改。 執行在父市場活動和子市場活動之間自動同步。 本地實體必須有權訪問實例以訂購市場活動並參與其中。
   * **[!UICONTROL Collaborative campaign (by target approval)]**:建議開展針對數千個地方實體的活動。 本地實體接收已由中心實體預定義的聯繫人清單。 本地實體通過網路表單根據活動內容決定是否保留某些聯繫人。 從所選接觸清單中推導局部圖元。 為了參與該活動，本地實體只需要訪問Web即可。
   * **[!UICONTROL Collaborative campaign (simple)]**:此模式確保與早期版本的特定執行進程相容。

   請參閱 [建立協作市場活動](creating-a-collaborative-campaign.md)。

**訂購市場活動包**

如果本地實體註冊市場活動，則系統會將其編入一個訂單，該訂單將重新組織與市場活動本地化相關的所有資訊。

## 工作區 {#workspace}

可以從 **市場活動** 頁籤：按一下 **[!UICONTROL Campaign packages]** 的子菜單。

![](assets/mkg_dist_home_local_op.png)

此窗口允許所有本地操作員查看其本地代理可用的市場活動。

對於中央機構，此窗口顯示市場活動包清單中可用的所有包，並提供用於編輯清單的附加連結。

## 運算子和實體 {#operators-and-entities}

開始，通過 **[!UICONTROL Access management]** 的子菜單。

![](assets/s_advuser_mkg_dist_tree.png)

### 運算子 {#operators}

您需要建立中心運算子和本地運算子。

中心運算子必須屬於 **[!UICONTROL Central management]** 運算子組或 **[!UICONTROL CENTRAL]** 名字正確。

本地運算子必須屬於 **[!UICONTROL Local management]** 運算子組或 **[!UICONTROL LOCAL]** 名字正確。 他們還必須與當地實體聯繫。

![](assets/s_advuser_mkg_dist_local_create.png)

### 組織實體 {#organizational-entities}

要建立組織實體，請按一下 **[!UICONTROL Administration > Access management > Organizational entities]** ，然後按一下 **[!UICONTROL New]** 表徵圖。

![](assets/s_advuser_mkg_dist_local_list.png)

每個組織實體都包含標識資訊（標籤、內部名稱、聯繫資訊等） 以及訂單審批流程中涉及的組。 這些定義於 **[!UICONTROL Notifications and approvals]** 中 **[!UICONTROL General]** 頁籤。

* 定義包通知組：每次將新包添加到市場活動包清單以及市場活動變為可用時，此組中的操作員將收到通知。
* 選擇負責批准訂單的審核者組，即負責批准由本地實體訂購的市場活動的審核者組。
* 最後，選擇負責批准本地市場活動（目標、內容、預算等）的審核者組。 訂購市場活動時，可以根據模板將此組添加到。

>[!NOTE]
>
>審批流程在 [審批流程](creating-a-local-campaign.md#approval-process) 的子菜單。

## 實施 {#implementation}

分佈式市場營銷活動由中央實體建立和發佈。 可根據需要由本地和中央實體使用。

實施過程取決於使用的促銷活動包類型和本地實體委派級別。

### 整合商任務 {#integrator-side}

1. 建立本地實體。
1. 將收件人與管理本地實體的運算子連結。

   ![](assets/mkg_dist_local_entity_association.png)

1. 指定本地實體的權限和瀏覽規則
1. 指定市場活動本地化所需的欄位集：

   * 目標定義和最大大小，
   * 內容定義，
   * 執行計畫（聯繫日期和提取日期）, **僅用於本地運算子**。
   * 序架構的擴展，包含所有必要的附加欄位。

1. 建立一個Web表單(Adobe或外聯網)，允許您顯示本地化參數、評估目標和預算，以及預覽內容和批准訂單。

   對於 **協作市場活動（按目標批准）**，建立保存每個本地實體的批准的表。

### 功能管理員任務 {#functional-administrator-side}

建立每個市場活動時必須執行這些步驟。

1. 使用用於市場活動本地化的欄位更新表單。
1. 從相應的市場活動模板（協作市場活動）建立實例或複製市場活動模板（本地市場活動）。
1. 使用本地化欄位和表單引用配置市場活動。
1. 發佈市場活動。

### 本地操作員任務 {#local-operator-side}

每次活動都必須採取這些步驟。

1. 收到市場活動包可用性通知後，指定市場活動的位置（可選）。
1. 評估目標、預算等。
1. 預覽市場活動內容。
1. 訂購市場活動。
