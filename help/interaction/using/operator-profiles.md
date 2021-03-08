---
solution: Campaign Classic
product: campaign
title: 運算元用戶檔案
description: 運算元用戶檔案
audience: interaction
content-type: reference
topic-tags: managing-environments
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 5%

---


# 運算元用戶檔案{#operator-profiles}

使用「互動」的運算子有兩種類型：選件經理和交付經理。 他們每個人都有特定的權限，只能讓他們存取樹狀結構和平台的某些部分。

* **[!UICONTROL Offer manager]** :建立和維護選件。請注意，如果選件用於工作流程中，運算元必須位於&#x200B;**[!UICONTROL Administrator]**&#x200B;或&#x200B;**[!UICONTROL Offer managers]**&#x200B;運算元群組中，才能執行工作流程。
* **[!UICONTROL Delivery manager]** :核准和使用選件

建立「互動」特定運算子的步驟與建立平台上所有其他運算子的步驟相同。 如需詳細資訊，請參閱[本章節](../../platform/using/access-management.md)。在建立操作員期間配置權限。

## 選件管理員{#offer-manager}

1. 建立新運算子。
1. 轉至&#x200B;**[!UICONTROL Groups and named rights]**&#x200B;窗口，按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選擇&#x200B;**[!UICONTROL Offer manager]**&#x200B;組。

   ![](assets/offer_operators_create_001.png)

指派給選件管理員的權限可讓他們執行下列工作：

* 修改&#x200B;**[!UICONTROL Design]**&#x200B;環境。
* 查看&#x200B;**[!UICONTROL Live]**&#x200B;環境。
* 設定管理函式（預先定義的空格和篩選器）。
* 建立和變更類別。
* 建立選件。
* 設定優惠資格。
* 核准選件。

   >[!NOTE]
   >
   >選件管理員只能在兩種特定情況下核准選件。 第一個是，如果沒有人特別指定為審核者，第二個是，負責建立模板（有權指派審核者）的操作員在選件模板中指定他／她作為審核者。

## 傳送管理器{#delivery-manager}

1. 建立新運算子。
1. 轉至&#x200B;**[!UICONTROL Groups and named rights]**&#x200B;窗口，按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選擇&#x200B;**[!UICONTROL Delivery manager]**&#x200B;組。

   ![](assets/offer_operators_create_002.png)

分配給交付管理員的權限可／使其執行以下任務：

* 顯示&#x200B;**[!UICONTROL Live]**&#x200B;環境。
* 顯示和修改選件類別。
* 如果指定選件為其審核者之一，請核准選件。

   >[!NOTE]
   >
   >傳送管理員只有在選件設定期間已定義為審核者時，才可核准選件。

## 根據運算子{#recap-of-rights-according-to-operator}重新查看權利

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
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人——環境<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理員<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 空格<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 預先定義的選件篩選器<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型學<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型規則<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 選件目錄<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 選件類別<br /> </td> 
   <td> 讀／寫<br /> </td> 
   <td> 讀取<br /> </td> 
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
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人——環境<br /> </td> 
   <td> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 管理員<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 空格<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 預先定義的選件篩選器<br /> </td> 
   <td> 讀取<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型學<br /> </td> 
   <td> 讀取<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 類型規則<br /> </td> 
   <td> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 選件目錄<br /> </td> 
   <td> 讀取<br /> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
  <tr> 
   <td> 選件類別<br /> </td> 
   <td> </td> 
   <td> 讀取<br /> </td> 
  </tr> 
 </tbody> 
</table>

