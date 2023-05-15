---
product: campaign
title: 選擇退出個人資訊銷售
description: 瞭解關於個人資訊銷售選擇退出
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 8e308a9f-14a4-4a25-9fd0-8d4bdbcf74ce
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 100%

---

# 選擇退出個人資訊銷售 (CCPA) {#sale-of-personal-information-ccpa}



**加州消費者隱私保護法 (CCPA)** 為加州居民提供新的個資權利，並對在加州經營業務的特定實體賦予資料保護責任。

GDPR 和 CCPA 都很常使用存取及刪除要求的設定與使用情況。本節說明專屬於 CCPA 的選擇退出個人資訊銷售。

除了 Adobe Campaign 提供的[同意管理](privacy-management.md#consent-management)工具以外，您還可以追蹤消費者是否選擇退出個人資訊銷售。

聯絡人可以透過您的系統決定不允許將其個人資訊銷售給協力廠商。 您將可在 Adobe Campaign 中儲存及追蹤此資訊。

為了達到此目的，您需要延伸「設定檔」表格並新增&#x200B;**[!UICONTROL Opt-Out for CCPA]**&#x200B;欄位。

>[!IMPORTANT]
>
>您身為資料控制方，有責任接收資料主體的要求並追蹤 CCPA 的要求日期。身為技術提供者，我們只提供選擇退出的方式。有關您擔任資料控制方的詳細資訊，請參閱[個人資料和角色](privacy-and-recommendations.md#personal-data)。

## 先決條件 {#ccpa-prerequisite}

您需要在 Adobe Campaign Classic 中建立此欄位，才能善用此資訊。為此，您將向 **[!UICONTROL Recipient]** 表格新增一個布林欄位。 建立新欄位時，Campaign API 會自動支援該欄位。

如果您使用自訂收件者表格，您也需要執行此作業。

有關如何建立新欄位的詳細資訊，請參閱[架構版本文件](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>修改架構是敏感性作業，僅能由專家用戶執行。

1. 前往&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**，選擇&#x200B;**[!UICONTROL Recipients]**&#x200B;作為&#x200B;**[!UICONTROL Document type]**，然後按一下&#x200B;**[!UICONTROL Next]**。 如需了解將欄位新增到表格的詳細資訊，請參閱[本節](../../configuration/using/new-field-wizard.md)。

   ![](assets/privacy-ccpa-1.png)

1. 對於&#x200B;**[!UICONTROL Field type]**，選擇&#x200B;**[!UICONTROL SQL field]**。 對於標籤，請使用&#x200B;**[!UICONTROL Opt-Out for CCPA]**。 選擇 **[!UICONTROL 8-bit integer (boolean)]** 類型並定義以下唯一&#x200B;**[!UICONTROL Relative path]**：@OPTOUCCPA。 按一下 **[!UICONTROL Finish]**。

   ![](assets/privacy-ccpa-2.png)

   這將擴充或建立 **[!UICONTROL Recipient (cus)]** 架構。 按一下以驗證欄位，確認欄位已正確新增。

   ![](assets/privacy-ccpa-3.png)

1. 按一下瀏覽器的&#x200B;**[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**&#x200B;節點。 在&#x200B;**[!UICONTROL Recipient (nms)]**&#x200B;的「一般套件」下，新增 `<input>` 元素，並使用步驟 2 中定義的相對路徑作為 xpath 值。 如需定義表格的詳細資訊，請參閱[本節](../../configuration/using/identifying-a-form.md)。

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. 斷開連線並重新連線。 請依照下一節所述的步驟，確認收件者的詳細資料上有該欄位。

## 使用情況 {#usage}

資料控制方應負責填入欄位的值，並遵循關於資料銷售的 CCPA 準則和規則。

若要填入值，可使用數種方法：

* 編輯收件者的詳細資料，以使用 Campaign 的介面
* 使用 API
* 透過資料匯入工作流程

之後，您應該確保您絕對不會向已選擇退出之任何第三方銷售設定檔的個人資訊。

1. 若要變更選擇退出的狀態，請前往 **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]**&#x200B;並選取收件者。 在 **[!UICONTROL General]** 標籤中，您會看到在上一節中設定的欄位。

   ![](assets/privacy-ccpa-5.png)

1. 設定收件者清單以顯示選擇退出欄位。 如要瞭解如何設定清單，請參閱[詳細文件](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

   ![](assets/privacy-ccpa-6.png)

1. 您可以按一下該欄位，以依據選擇退出資訊來排序收件者。您也可以建立篩選，只顯示已選擇退出的收件者。 如需建立篩選的詳細資訊，請參閱[本節](../../platform/using/creating-filters.md)。

   ![](assets/privacy-ccpa-7.png)
