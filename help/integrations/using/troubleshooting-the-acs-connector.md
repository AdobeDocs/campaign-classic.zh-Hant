---
product: campaign
title: 疑難排解ACS聯結器
description: 疑難排解ACS聯結器
feature: ACS Connector, Troubleshooting
audience: integrations
content-type: reference
topic-tags: acs-connector
hide: true
hidefromtoc: true
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 0%

---

# 疑難排解ACS聯結器{#troubleshooting-the-acs-connector}



根據您的實作，您可能會遇到幾個常見問題。

* **Campaign Standard和Campaign v7之間的UI差異為何？**

  Campaign Standard和Campaign v7的運作方式非常類似。 大部分的概念都相同，但在某些情況下，方法可能會稍有不同。 以下是一些在ACS Connector內容中可能不同的概念：

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
   <td> 設定檔<br /> </td> 
  </tr> 
  <tr> 
   <td> 清單<br /> </td> 
   <td> 對象<br /> </td> 
  </tr> 
  <tr> 
   <td> 行銷活動工作流程，目標定位工作流程<br /> </td> 
   <td> 工作流程<br /> </td> 
  </tr> 
  <tr> 
   <td> 作業<br /> </td> 
   <td> 行銷活動<br /> </td> 
  </tr> 
  <tr> 
   <td> 網頁應用程式<br /> </td> 
   <td> 登陸頁面<br /> </td> 
  </tr> 
  <tr> 
   <td> 自訂資料表和結構描述延伸<br /> </td> 
   <td> 自訂資源與資源延伸<br /> </td> 
  </tr> 
  <tr> 
   <td> 種子成員<br /> </td> 
   <td> 測試設定檔<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **我的Campaign v7執行個體的收件者未同步處理或對Campaign Standard不可見。**

  發生此情形可能有不同的原因：

   * 收件者已在Campaign v7中建立或更新。 同步每15分鐘觸發一次。 這表示在下次同步後，更新的或新建立的收件者會顯示在Campaign Standard中。
   * 您的實作可設為僅同步特定資料夾中的收件者。 來自其他資料夾的收件者不會同步。
   * 收件者可以同步，但在Campaign Standard中看不到。 檢查資料夾許可權對應。

* **我在Campaign Standard中找不到查詢所依據的設定檔欄位。**

  根據預設，nms：recipient表格中的20個欄位會與Campaign Standard同步。 請參閱已同步欄位的詳細清單。 您需要在Campaign Standard中擷取的任何其他欄位，都必須由您的顧問對應和設定。

  若要確定您要使用的欄位可用，您可以從&#x200B;**[!UICONTROL Administration > Development > Diagnosis > Data schemas]**&#x200B;檢查設定檔資源定義。

  此外，依預設，附加到收件者並儲存在與nms：recipients相關之表格中的所有資料不會同步到Campaign Standard。

  若要仍然能夠使用相關資料，您可以在Campaign v7中執行目標定位，並新增其他資料，如[同步對象](../../integrations/using/synchronizing-audiences.md)區段中所述，或者您可以諮詢顧問以探索自訂可能性。

* **我在Campaign v7中使用另一個設定檔維度（而不是預設的nms：recipient），如何將其與Campaign Standard同步？**

  Campaign Standard使用名為&#x200B;**設定檔**&#x200B;的唯一目標定位資源。 Campaign Standard連線功能的基本實施提供Campaign v7收件者與Campaign Standard設定檔之間的預設對應。

  如果您在Campaign v7中使用其他設定檔維度，或如果您使用數個設定檔維度，則所有維度都必須與Campaign Standard設定檔對應。 請洽詢您的顧問，以解決此特定需求。

* **我想透過工作流程與Campaign Standard共用設定檔清單，但在Campaign Standard**&#x200B;中找不到我的對象。

  您可以在Campaign Standard的&#x200B;**[!UICONTROL Audiences]**&#x200B;功能表中找到對象。 他們已在Campaign v7工作流程的&#x200B;**[!UICONTROL List update]**&#x200B;活動中指定標籤。 它們須受實施期間定義的資料夾對應約束。

  首先要檢查的工作流程是否已順利完成。 如果您在&#x200B;**[!UICONTROL List update]**&#x200B;活動上發現錯誤，則表示與Campaign Standard的同步可能已失敗。 若要檢視發生問題的詳細資訊，請前往「**[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**」。 此資料夾包含由&#x200B;**[!UICONTROL List update]**&#x200B;活動執行觸發的同步工作流程。

  此外，請確定已在&#x200B;**[!UICONTROL List update]**&#x200B;活動中勾選&#x200B;**[!UICONTROL Share with ACS]**&#x200B;選項，且工作流程已正確執行。

  請注意，清單中包含的收件者設定檔必須在工作流程執行前與Campaign Standard同步。 在與Campaign Standard共用後，清單的收件者會與Campaign Standard設定檔進行調解，這表示他們必須存在於那裡。 清單中無法與Campaign Standard中的設定檔進行調解的收件者會被忽略。

  如果您共用由設定檔組成的清單，而且沒有任何設定檔與Campaign Standard同步，則會在Campaign Standard中建立無法使用的空查詢對象。

* **我收到通知，告知我同步工作流程處於錯誤狀態。 我應該怎麼做？**

  透過測試連線檢查Campaign Standard和Campaign v7中的外部帳戶設定：

   * **[!UICONTROL acsDefaultRelayAccount]** Campaign Standard。
   * Campaign v7中的&#x200B;**[!UICONTROL acsDefaultAccount]**。

* **我在Campaign v7和Campaign Standard之間對應資料夾時沒有可用的安全性群組。**

  您必須先從&#x200B;**[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**&#x200B;同步處理您的安全性群組。 此動作會檢查Campaign Standard中可用的安全性群組。 同步之後，您可以在設定資料夾對應時找到安全性群組。

* **我無法在Campaign Standard中編輯設定檔、對象或登陸頁面。 這是什麼意思？**

  從Campaign v7同步的資源在Campaign Standard中處於唯讀模式，以確保資料一致性。 如果您需要編輯其中一個元素，可以在Campaign v7中進行編輯，然後在Campaign Standard中複製變更。

* **在[ACS]設定檔傳遞記錄復寫工作流程中發生錯誤。 我應該怎麼做？**

  如果Campaign Classic和Campaign Standard執行個體都用於傳送包含追蹤URL的電子郵件，則在同步期間可能會發生重複URL tagId的問題。 在此情況下，**[ACS]設定檔傳遞記錄復寫** (newRcpDeliveryLogReplication)工作流程仍會失敗，並出現下列錯誤：

  ```PGS-220000 PostgreSQL error: ERROR: duplicate key value violates unique constraint "nmstrackingurl_tagid" DETAIL: Key (stagid) = (1c7bdec2) already exists.```

  若要解決問題並防止再次發生，請更新工作流程中的&#x200B;**更新追蹤URL** (writerTrackingUrls)活動，並將「ACS」首碼新增至@tagId料來源運算式。
