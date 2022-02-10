---
product: campaign
title: 排除ACS連接器故障
description: 排除ACS連接器故障
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# 排除ACS連接器故障{#troubleshooting-the-acs-connector}

![](../../assets/v7-only.svg)

根據您的實施情況，您可能會面臨幾個常見問題。

* **Campaign Standard與市場活動v7之間的UI區別是什麼？**

   Campaign Standard和營銷活動v7的工作方式非常相似。 大多數概念是相同的，但在某些情況下，方法可能略有不同。 以下是ACS連接器上下文中可能不同的一些概念：

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 收件人（或任何其他配置檔案維）<br /> </td> 
   <td> 配置檔案<br /> </td> 
  </tr> 
  <tr> 
   <td> 清單<br /> </td> 
   <td> 觀眾<br /> </td> 
  </tr> 
  <tr> 
   <td> 活動工作流，目標工作流<br /> </td> 
   <td> 工作流<br /> </td> 
  </tr> 
  <tr> 
   <td> 操作<br /> </td> 
   <td> 行銷活動<br /> </td> 
  </tr> 
  <tr> 
   <td> Web應用<br /> </td> 
   <td> 登錄頁<br /> </td> 
  </tr> 
  <tr> 
   <td> 自定義表和架構擴展<br /> </td> 
   <td> 定制資源和資源擴展<br /> </td> 
  </tr> 
  <tr> 
   <td> 種子成員<br /> </td> 
   <td> test配置檔案<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **「我的市場活動v7」實例的收件人不同步或對Campaign Standard可見。**

   此案可能因不同原因而發生：

   * 收件人剛剛在「市場活動7」中建立或更新。 同步每15分鐘觸發一次。 這意味著在下次同步後，更新的或新建立的收件人將在Campaign Standard中可見。
   * 您的實現可以設定為僅同步特定資料夾中的收件人。 未同步來自其他資料夾的收件人。
   * 收件人可以同步，但在Campaign Standard中不可見。 檢查資料夾權限映射。

* **我找不到需要基於查詢的配置檔案欄位，請使用Campaign Standard。**

   預設情況下， nms:recipient表中的20個欄位與Campaign Standard同步。 請參閱已同步欄位的詳細清單。 您需要在Campaign Standard中檢索的任何附加欄位都必須由顧問進行映射和配置。

   要確保要使用的欄位可用，可從中檢查配置檔案資源定義 **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**。

   此外，預設情況下，附加到收件人並儲存在與nms:recipients相關的表中的所有資料不會與Campaign Standard同步。

   為了仍然能夠使用相關資料，您可以在市場活動v7中執行目標，並添加其他資料，如 [同步受眾](../../integrations/using/synchronizing-audiences.md) 或者，您可以咨詢顧問以探討自定義的可能性。

* **我使用的配置檔案維度不是市場活動v7中的預設nms:recipient，如何將它們與Campaign Standard同步？**

   Campaign Standard使用唯一的目標資源，該資源名為 **配置檔案**。 「Campaign Standard連接」功能的基本實現提供了市場活動v7收件人和Campaign Standard配置檔案之間的預設映射。

   如果您在市場活動v7中使用了另一個配置檔案維，或者您使用了多個配置檔案維，則必須用Campaign Standard配置檔案映射這些配置檔案。 請咨詢顧問以滿足此特定需求。

* **我想通過工作流與Campaign Standard共用配置檔案清單，但找不到我的受眾在Campaign Standard中**。

   在 **[!UICONTROL Audiences]** 的子菜單。 它們在 **[!UICONTROL List update]** 活動v7工作流中的活動。 它們受實施期間定義的資料夾映射的約束。

   首先要檢查的是工作流是否已完成且無錯誤。 如果您在 **[!UICONTROL List update]** 活動，這意味著與Campaign Standard的同步可能已失敗。 若要查看有關出錯的詳細資訊，請轉到 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**。 此資料夾包含由 **[!UICONTROL List update]** 活動執行。

   另外，確保 **[!UICONTROL Share with ACS]** 選項 **[!UICONTROL List update]** 已正確執行工作流。

   請注意，清單中包含的收件人配置檔案必須在工作流執行之前與Campaign Standard同步。 與Campaign Standard共用後，清單的收件人將與Campaign Standard配置檔案進行協調，這意味著它們必須存在於該配置檔案中。 無法與Campaign Standard中的配置檔案協調的清單中的收件人將被忽略。

   如果您共用由配置檔案組成的清單，並且沒有配置檔案與Campaign Standard同步，則它會在Campaign Standard中建立一個無法使用的空查詢訪問群體。

* **我收到通知，通知我同步工作流處於錯誤狀態。 我該怎麼辦？**

   通過測試連接，在Campaign Standard和市場活動v7中檢查外部帳戶配置：

   * **[!UICONTROL acsDefaultRelayAccount]** Campaign Standard。
   * **[!UICONTROL acsDefaultAccount]** 第7版促銷活動。

* **在Campaign v7和Campaign Standard之間映射資料夾時，我沒有可用的安全組。**

   您需要首先從 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**。 此操作將檢查Campaign Standard中可用的安全組。 同步後，可以在配置資料夾映射時找到安全組。

* **我無法在Campaign Standard中編輯個人資料、受眾或登錄頁。 什麼意思？**

   從市場活動v7同步的資源處於只讀模式Campaign Standard，以確保資料一致性。 如果需要編輯其中一個元素，可以在「市場活動7」中進行編輯，然後複製Campaign Standard中的更改。
