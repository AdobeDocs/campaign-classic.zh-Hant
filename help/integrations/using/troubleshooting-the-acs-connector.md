---
title: 診斷ACS連接器
seo-title: 診斷ACS連接器
description: 診斷ACS連接器
seo-description: null
page-status-flag: never-activated
uuid: aef85b74-0388-44f8-b864-21db136a692c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 538d3b48-ff39-463f-878d-ebe085057129
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 診斷ACS連接器{#troubleshooting-the-acs-connector}

視您的實作而定，您可能會面臨幾個常見問題。

* **Campaign standard和Campaign v7之間的UI差異為何？**

   「促銷活動標準」和「促銷活動v7」的運作方式非常類似。 大部分概念都相同，但在某些情況下，方法可能略有不同。 以下是ACS連接器上下文中可能不同的一些概念：

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 收件者（或任何其他描述檔維度）<br /> </td> 
   <td> 描述檔<br /> </td> 
  </tr> 
  <tr> 
   <td> 清單<br /> </td> 
   <td> audience<br /> </td> 
  </tr> 
  <tr> 
   <td> 促銷活動工作流程，鎖定工作流程<br /> </td> 
   <td> 工作流程<br /> </td> 
  </tr> 
  <tr> 
   <td> 營運<br /> </td> 
   <td> 促銷活動<br /> </td> 
  </tr> 
  <tr> 
   <td> 網路應用程式<br /> </td> 
   <td> landing pages<br /> </td> 
  </tr> 
  <tr> 
   <td> 自訂表格和架構擴充功能<br /> </td> 
   <td> 自訂資源與資源擴充<br /> </td> 
  </tr> 
  <tr> 
   <td> 種子成員<br /> </td> 
   <td> 測試描述檔<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **我的Campaign v7例項的收件者不會同步化，也不會顯示在Campaign Standard中。**

   此案的發生有不同的原因：

   * 收件者剛在Campaign v7中建立或更新。 同步每15分鐘觸發一次。 這表示更新或新建立的收件者在下次同步後，將會顯示在Campaign standard中。
   * 您的實作可設為僅同步特定資料夾的收件者。 其他資料夾的收件者不會同步化。
   * 收件者可以同步，但在「促銷活動標準」中看不到。 檢查資料夾權限映射。

* **在Campaign standard中找不到我要依據的描述檔欄位。**

   依預設， nms:recipient表中的20個欄位會與Campaign Standard同步。 請參閱已同步欄位的詳細清單。 您需要在Campaign Standard中擷取的任何其他欄位，都必須由顧問進行映射和設定。

   要確保要使用的欄位可用，您可以從中檢查配置檔案資源定義 **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**。

   此外，依預設，附加至收件者並儲存在與nms：收件者相關的表格中的所有資料不會同步至Campaign Standard。

   若要仍能使用相關資料，您可以在Campaign v7中執行定位並新增其他資料，如「同步觀眾 [](../../integrations/using/synchronizing-audiences.md) 」一節所述，或請諮詢您的顧問以探索自訂可能性。

* **我在Campaign v7中使用的是不同於預設nms:recipient的其他描述檔維度，我要如何將它們與Campaign Standard同步？**

   Campaign standard使用唯一的定位資源，名為 **描述檔**。 「促銷活動標準連線」功能的基本實作提供Campaign v7收件者與「促銷活動標準」設定檔之間的預設對應。

   如果您在Campaign v7中使用其他描述檔維度，或者您使用數個維度，則必須將這些維度與Campaign standard描述檔對應。 請洽詢您的顧問以解決此特殊需求。

* **我想要透過工作流程與Campaign standard共用設定檔清單，但無法在Campaign Standard中找到我的對象**。

   您可在Campaign Standard的功能表 **[!UICONTROL Audiences]** 中找到觀眾。 這些標籤在您的Campaign v7工 **[!UICONTROL List update]** 作流程中的活動中指定。 它們受實作期間定義的資料夾對應所約束。

   首先要檢查的是工作流程是否已完成而無錯誤。 如果您注意到活動發生錯 **[!UICONTROL List update]** 誤，表示與「促銷活動標準」的同步可能失敗。 若要查看有關問題的詳細資訊，請前往 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**。 此資料夾包含由活動執行觸發的同 **[!UICONTROL List update]** 步工作流。

   此外，請確定選 **[!UICONTROL Share with ACS]** 項已勾選至活 **[!UICONTROL List update]** 動，且工作流程已正確執行。

   請注意，清單中包含的收件者描述檔必須在工作流程執行之前已與Campaign Standard同步。 與Campaign standard共用後，清單的收件者會與Campaign standard設定檔進行協調，這表示這些收件者必須存在於其中。 清單中無法與Campaign Standard中的設定檔協調的收件者會被忽略。

   如果您共用由設定檔所組成的清單，且如果沒有與Campaign Standard同步，則會在Campaign Standard中建立無法使用的空查詢對象。

* **我收到通知，通知我同步工作流處於錯誤狀態。 我該怎麼辦？**

   透過測試連線，檢查Campaign Standard和Campaign v7中的外部帳戶設定：

   * **[!UICONTROL acsDefaultRelayAccount]** 在Campaign standard中。
   * **[!UICONTROL acsDefaultAccount]** 在Campaign v7中。

* **在Campaign v7和Campaign standard之間對應資料夾時，我沒有可用的安全性群組。**

   您必須先從中同步您的安全組 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**。 此動作會檢查Campaign standard中可用的安全性群組。 同步後，在配置資料夾映射時可以找到安全組。

* **我無法在Campaign standard中編輯個人檔案、對象或登陸頁面。 這意味著什麼？**

   從Campaign v7同步化的資源在Campaign standard中處於唯讀模式，以確保資料一致性。 如果您需要編輯其中一個元素，可以在Campaign v7中進行，然後在Campaign Standard中複製變更。

