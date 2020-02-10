---
title: 運算元描述檔
seo-title: 運算元描述檔
description: 運算元描述檔
seo-description: null
page-status-flag: never-activated
uuid: cd718d20-79cb-40ed-b2ae-23186387e2db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 9a3f1dc9-71ef-4039-94b4-a217996f6a80
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 運算元描述檔{#operator-profiles}

使用「互動」的運算子有兩種類型：選件經理和交付經理。 他們每個人都有特定的權限，只能讓他們存取樹狀結構和平台的某些部分。

* **[!UICONTROL Offer manager]** :建立和維護選件
* **[!UICONTROL Delivery manager]** :核准和使用選件

建立「互動」特定運算子的步驟與建立平台上所有其他運算子的步驟相同。 如需詳細資訊，請參閱[本小節](../../platform/using/access-management.md#creating-an-operator)。在建立操作員期間配置權限。

## 選件管理員 {#offer-manager}

1. 建立新運算子。
1. 前往視窗 **[!UICONTROL Groups and named rights]** ，按一下並 **[!UICONTROL Add]** 選取 **[!UICONTROL Offer manager]** 群組。

   ![](assets/offer_operators_create_001.png)

指派給選件管理員的權限可讓他們執行下列工作：

* 修改 **[!UICONTROL Design]** 環境。
* 檢視 **[!UICONTROL Live]** 環境。
* 設定管理函式（預先定義的空格和篩選器）。
* 建立和變更類別。
* 建立選件。
* 設定優惠資格。
* 核准選件。

   >[!NOTE]
   >
   >選件管理員只能在兩種特定情況下核准選件。 第一個是，如果沒有人特別指定為審核者，第二個是，負責建立模板（有權指派審核者）的操作員在選件模板中指定他／她作為審核者。

## 傳送管理員 {#delivery-manager}

1. 建立新運算子。
1. 前往視窗 **[!UICONTROL Groups and named rights]** ，按一下並 **[!UICONTROL Add]** 選取 **[!UICONTROL Delivery manager]** 群組。

   ![](assets/offer_operators_create_002.png)

分配給交付管理員的權限可／使其執行以下任務：

* 顯示 **[!UICONTROL Live]** 環境。
* 顯示和修改選件類別。
* 如果指定選件為其審核者之一，請核准選件。

   >[!NOTE]
   >
   >傳送管理員只有在選件設定期間已定義為審核者時，才可核准選件。

## 根據經營者重新審查權利 {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>選件管理員（編輯）</strong><br /> </td> 
   <td> <strong>選件管理員（即時）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>樹結構層</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在編輯的選件／即時選件<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件者——環境<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 空格<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 預先定義的選件篩選<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型學<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型學規則<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 選件目錄<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 選件類別<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>傳送管理員（編輯）</strong><br /> </td> 
   <td> <strong>傳送管理員（即時）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>樹結構層</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在編輯的選件／即時選件<br /> </td> 
   <td> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件者——環境<br /> </td> 
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
   <td> 預先定義的選件篩選<br /> </td> 
   <td> 閱讀<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型學<br /> </td> 
   <td> 閱讀<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型學規則<br /> </td> 
   <td> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 選件目錄<br /> </td> 
   <td> 閱讀<br /> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
  <tr> 
   <td> 選件類別<br /> </td> 
   <td> </td> 
   <td> 閱讀<br /> </td> 
  </tr> 
 </tbody> 
</table>

