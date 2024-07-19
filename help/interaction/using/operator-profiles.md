---
product: campaign
title: 運算子設定檔
description: 運算子設定檔
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 2%

---

# 運算子設定檔{#operator-profiles}



使用互動的運運算元有兩種型別：優惠方案管理員和傳遞管理員。 每個使用者都有特定許可權，僅可存取樹狀結構部分和平台。

* **[!UICONTROL Offer manager]** ：建立和維護優惠方案。 請注意，如果工作流程中使用選件，運運算元必須位於&#x200B;**[!UICONTROL Administrator]**&#x200B;或&#x200B;**[!UICONTROL Offer managers]**&#x200B;運運算元群組中，才能執行工作流程。
* **[!UICONTROL Delivery manager]** ：核准並使用優惠方案

建立「互動」專屬運運算元的步驟，與在Platform上建立所有其他運運算元所用的步驟相同。 如需詳細資訊，請參閱[本節](../../platform/using/access-management.md)。 許可權是在建立運運算元時設定的。

## 優惠方案管理員 {#offer-manager}

1. 建立新的運運算元。
1. 移至&#x200B;**[!UICONTROL Groups and named rights]**&#x200B;視窗，按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選取&#x200B;**[!UICONTROL Offer manager]**&#x200B;群組。

   ![](assets/offer_operators_create_001.png)

指派給優惠方案管理員的許可權可讓他們執行下列工作：

* 修改&#x200B;**[!UICONTROL Design]**&#x200B;環境。
* 檢視&#x200B;**[!UICONTROL Live]**&#x200B;環境。
* 設定管理功能（預先定義的空格和篩選器）。
* 建立和變更類別。
* 建立優惠方案。
* 設定優惠資格。
* 核准優惠方案。

  >[!NOTE]
  >
  >優惠方案管理員只能在兩種特定情況下核准優惠方案。 第一個是「如果沒有任何特定人員被指定為稽核者」，第二個是「如果負責建立範本的運運算元（有權指派稽核者）」將他們指定為優惠方案所依據之優惠方案範本中的稽核者」。

## 傳遞管理員 {#delivery-manager}

1. 建立新的運運算元。
1. 移至&#x200B;**[!UICONTROL Groups and named rights]**&#x200B;視窗，按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選取&#x200B;**[!UICONTROL Delivery manager]**&#x200B;群組。

   ![](assets/offer_operators_create_002.png)

指派給傳遞管理員的許可權可讓他們執行下列工作：

* 顯示&#x200B;**[!UICONTROL Live]**&#x200B;環境。
* 顯示和修改優惠方案類別。
* 如果將此傳遞管理員指定為其稽核者，則核准優惠方案。

  >[!NOTE]
  >
  >只有在優惠方案設定期間，傳遞管理員已定義為檢閱者，才能核准優惠方案。

## 根據運運算元重述權利 {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>選件管理員（正在編輯）</strong><br /> </td> 
   <td> <strong>優惠方案管理員（即時）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>樹狀結構層級</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在編輯的優惠/即時優惠<br /> </td> 
   <td> 讀取/寫入<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件者 — 環境<br /> </td> 
   <td> 讀取/寫入<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理<br /> </td> 
   <td> 讀取/寫入<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 空間<br /> </td> 
   <td> 讀取/寫入<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 預先定義的優惠篩選器<br /> </td> 
   <td> 讀取/寫入<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 型別<br /> </td> 
   <td> 讀取/寫入<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 型別規則<br /> </td> 
   <td> 讀取/寫入<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 優惠方案目錄<br /> </td> 
   <td> 讀取/寫入<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 優惠方案類別<br /> </td> 
   <td> 讀取/寫入<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>傳遞管理員（正在編輯）</strong><br /> </td> 
   <td> <strong>傳遞管理員（即時）</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>樹狀結構層級</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 正在編輯的優惠/即時優惠<br /> </td> 
   <td> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件者 — 環境<br /> </td> 
   <td> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 空間<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 預先定義的優惠篩選器<br /> </td> 
   <td> 讀取<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 型別<br /> </td> 
   <td> 讀取<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 型別規則<br /> </td> 
   <td> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 優惠方案目錄<br /> </td> 
   <td> 讀取<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 優惠方案類別<br /> </td> 
   <td> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
 </tbody> 
</table>
