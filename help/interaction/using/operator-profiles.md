---
product: campaign
title: 運算子設定檔
description: 運算子設定檔
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 9%

---

# 運算子設定檔{#operator-profiles}



使用「互動」的運算子類型有兩種：優惠方案經理和傳遞經理。 它們每個都具有特定權限，只允許它們訪問樹和平台的某些部分。

* **[!UICONTROL Offer manager]** :建立和維護選件。 請注意，如果工作流程中使用選件，運算子必須位於 **[!UICONTROL Administrator]** 或 **[!UICONTROL Offer managers]** 運算元群組，以執行工作流程。
* **[!UICONTROL Delivery manager]** :核准和使用優惠方案

建立「互動」專用運算子的步驟與建立平台上所有其他運算子的步驟相同。 如需詳細資訊，請參閱[本章節](../../platform/using/access-management.md)。權限是在建立運算子期間設定的。

## 優惠方案管理員 {#offer-manager}

1. 建立新運算子。
1. 前往 **[!UICONTROL Groups and named rights]** 按一下 **[!UICONTROL Add]** ，然後選取 **[!UICONTROL Offer manager]** 群組。

   ![](assets/offer_operators_create_001.png)

指派給優惠方案管理員的權限可讓他們執行下列工作：

* 修改 **[!UICONTROL Design]** 環境。
* 檢視 **[!UICONTROL Live]** 環境。
* 配置管理函式（預定義的空格和篩選器）。
* 建立和更改類別。
* 建立優惠.
* 設定優惠方案資格。
* 核准優惠方案。

   >[!NOTE]
   >
   >優惠方案管理員只能在兩種情況下核准優惠方案。 第一個是沒有人特別指定為審核者，第二個是負責建立範本（有權指派審核者）的運算子在選件所依據的選件範本中將其指定為審核者。

## 傳送管理員 {#delivery-manager}

1. 建立新運算子。
1. 前往 **[!UICONTROL Groups and named rights]** 按一下 **[!UICONTROL Add]** ，然後選取 **[!UICONTROL Delivery manager]** 群組。

   ![](assets/offer_operators_create_002.png)

指派給傳送管理員的權限可讓他們執行下列工作：

* 顯示 **[!UICONTROL Live]** 環境。
* 顯示和修改優惠方案類別。
* 如果此傳遞管理員指定為其審核者之一，則核准優惠方案。

   >[!NOTE]
   >
   >傳送管理員只有在在選件設定期間定義為審核者時，才能核准選件。

## 根據操作員重新評估權利 {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>優惠方案管理員（編輯）</strong><br /> </td> 
   <td> <strong>優惠方案管理員（正式啟用）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>樹結構級別</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在編輯的選件/即時選件<br /> </td> 
   <td> 讀/寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件者 — 環境<br /> </td> 
   <td> 讀/寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理<br /> </td> 
   <td> 讀/寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 空格<br /> </td> 
   <td> 讀/寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 預先定義的優惠篩選器<br /> </td> 
   <td> 讀/寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型<br /> </td> 
   <td> 讀/寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型規則<br /> </td> 
   <td> 讀/寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 優惠方案目錄<br /> </td> 
   <td> 讀/寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 優惠方案類別<br /> </td> 
   <td> 讀/寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>傳送管理員（編輯）</strong><br /> </td> 
   <td> <strong>傳送管理員（正式啟用）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>樹結構級別</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在編輯的選件/即時選件<br /> </td> 
   <td> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件者 — 環境<br /> </td> 
   <td> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 空格<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 預先定義的優惠篩選器<br /> </td> 
   <td> 閱讀<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型<br /> </td> 
   <td> 閱讀<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型規則<br /> </td> 
   <td> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 優惠方案目錄<br /> </td> 
   <td> 閱讀<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 優惠方案類別<br /> </td> 
   <td> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
 </tbody> 
</table>
