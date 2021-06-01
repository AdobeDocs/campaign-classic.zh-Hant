---
product: campaign
title: 疑難排解ACS連接器
description: 疑難排解ACS連接器
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# 疑難排解ACS連接器{#troubleshooting-the-acs-connector}

視您的實作而定，您可能會面臨數個常見問題。

* **Campaign Standard和Campaign v7之間的UI差異為何？**

   Campaign Standard和Campaign v7的運作方式非常類似。 大部分的概念都相同，但在某些情況下，方法可能會稍有不同。 以下是一些在ACS連接器上下文中可能不同的概念：

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 收件者（或任何其他設定檔維度）<br /> </td> 
   <td> profiles<br /> </td> 
  </tr> 
  <tr> 
   <td> list<br /> </td> 
   <td> audience<br /> </td> 
  </tr> 
  <tr> 
   <td> 行銷活動工作流程，鎖定工作流程<br /> </td> 
   <td> workflows<br /> </td> 
  </tr> 
  <tr> 
   <td> 操作<br /> </td> 
   <td> 行銷活動<br /> </td> 
  </tr> 
  <tr> 
   <td> Web應用程式<br /> </td> 
   <td> 登錄頁面<br /> </td> 
  </tr> 
  <tr> 
   <td> 自定義表和方案擴展<br /> </td> 
   <td> 自定義資源和資源擴展<br /> </td> 
  </tr> 
  <tr> 
   <td> 種子成員<br /> </td> 
   <td> 測試設定檔<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **我的Campaign v7執行個體的收件者不會同步，或是不會顯示給Campaign Standard。**

   此情況的發生原因不同：

   * 收件者是剛在Campaign v7中建立或更新。 每15分鐘會觸發一次同步。 這表示下次同步後，更新的或新建立的收件者將顯示在Campaign Standard中。
   * 您的實作可設為僅同步特定資料夾中的收件者。 其他資料夾的收件者不會同步。
   * 收件者可以同步，但無法顯示在Campaign Standard中。 檢查資料夾權限對應。

* **找不到需要以Campaign Standard為查詢基礎的設定檔欄位。**

   依預設， nms:recipient表格中的20個欄位會與Campaign Standard同步。 請參閱已同步欄位的詳細清單。 您的顧問必須對應並設定您在Campaign Standard中擷取所需的任何其他欄位。

   若要確定您要使用的欄位可用，您可以從&#x200B;**[!UICONTROL Administration > Development > Diagnosis > Data schemas]**&#x200B;檢查設定檔資源定義。

   此外，預設情況下，與收件者連結並儲存在與nms:recipients相關的表格中的所有資料不會同步到Campaign Standard。

   若要仍能使用相關資料，您可以在Campaign v7中執行目標定位，並新增其他資料，如[同步對象](../../integrations/using/synchronizing-audiences.md)區段所述，或者您可以洽詢您的顧問，探索自訂的可能性。

* **我在Campaign v7中使用的是預設nms:recipient以外的其他設定檔維度，如何將其與Campaign Standard同步？**

   Campaign Standard使用名為&#x200B;**profiles**&#x200B;的唯一目標定位資源。 「Campaign Standard連線」功能的基本實作提供Campaign v7收件者與Campaign Standard設定檔之間的預設對應。

   如果您在Campaign v7中使用其他設定檔維度，或使用數個維度，則所有設定檔都必須與Campaign Standard設定檔對應。 請洽詢您的顧問，以解決此特定需求。

* **我想透過工作流程與Campaign Standard共用設定檔清單，但無法在Campaign Standard中找到我的對象**。

   您可以在&#x200B;**[!UICONTROL Audiences]**&#x200B;功能表的Campaign Standard中找到對象。 在您的Campaign v7工作流程的&#x200B;**[!UICONTROL List update]**&#x200B;活動中指定標籤。 它們受實施期間定義的資料夾對應所限制。

   首先要檢查的是工作流程是否已完成，並無錯誤。 如果您注意到&#x200B;**[!UICONTROL List update]**&#x200B;活動出現錯誤，表示與Campaign Standard的同步可能已失敗。 若要查看關於發生錯誤的詳細資訊，請前往&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**。 此資料夾包含&#x200B;**[!UICONTROL List update]**&#x200B;活動執行所觸發的同步工作流程。

   同時，請確定&#x200B;**[!UICONTROL Share with ACS]**&#x200B;活動中已勾選&#x200B;**[!UICONTROL List update]**&#x200B;選項，且工作流程已正確執行。

   請注意，清單中包含的收件者設定檔必須在工作流程執行前與Campaign Standard同步。 與Campaign Standard共用後，清單的收件者會與Campaign Standard設定檔調解，這表示他們必須存在於該處。 清單中無法與Campaign Standard中的設定檔調解的收件者會遭忽略。

   如果您共用由設定檔組成的清單，而且如果沒有與Campaign Standard同步，則會在Campaign Standard中建立無法使用的空白「查詢」對象。

* **我收到通知，通知我同步工作流處於錯誤狀態。我該做什麼？**

   透過測試連線，檢查Campaign Standard和Campaign v7中的外部帳戶設定：

   * **[!UICONTROL acsDefaultRelayAccount]** Campaign Standard。
   * **[!UICONTROL acsDefaultAccount]** 在Campaign v7中。

* **在Campaign v7和Campaign Standard之間對應資料夾時，沒有可用的安全性群組。**

   您需要先從&#x200B;**[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**&#x200B;同步安全組。 此動作會檢查Campaign Standard中可用的安全性群組。 同步後，在配置資料夾映射時可以找到安全組。

* **我無法編輯Campaign Standard中的設定檔、對象或登錄頁面。這是什麼意思？**

   從Campaign v7同步的資源處於Campaign Standard的唯讀模式，以確保資料一致性。 如果您需要編輯其中一個元素，可以在Campaign v7中執行，然後在Campaign Standard中複製變更。
