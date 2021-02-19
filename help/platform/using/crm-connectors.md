---
solution: Campaign Classic
product: campaign
title: CRM 連接器
description: 開始使用Campaign中的CRM連接器
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 24%

---


# CRM 連接器{#crm-connectors}

## 開始使用CRM連接器{#about-crm-connectors}

Adobe Campaign 提供各種 CRM 連接器，用於將您的 Adobe Campaign 平台連結至您的協力廠商系統。透過這些 CRM 連接器，您可同步處理連絡人、帳戶、購買等。有了這些 CRM 連接器，您可以將您的應用程式與各協力廠商和企業應用程式輕鬆整合。

透過這些連接器，可快速且輕鬆地整合資料：Adobe Campaign 提供專用的精靈，用於從 CRM 中提供的表格進行收集和選取。並且可確保雙向同步處理，讓整個系統中的資料隨時保持最新。

>[!NOTE]
>
>此功能可透過&#x200B;**CRM連接器**&#x200B;專用套件在Adobe Campaign中使用。


### 相容系統{#compatible-crm-systems-and-limitations}

支援的CRM和版本詳見Campaign [相容性矩陣](../../rn/using/compatibility-matrix.md)。

>[!NOTE]
>
>CRM連接器僅能與安全URL(https)搭配運作。

### 實施步驟 {#crm-implementation-steps}

在本節](../../platform/using/crm-ms-dynamics.md)中瞭解連接Campaign和Microsoft Dynamics [的逐步程式

一般而言，若要在Adobe Campaign中使用CRM連接器，請遵循下列步驟：

1. 透過Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;節點建立新的外部帳戶。
1. 選擇您將Campaign連接至所需的CRM系統。
1. 輸入設定以啟用連接。
1. 運行配置嚮導以生成可用的CRM表：配置嚮導可讓您收集表並建立匹配的模式。

   **Salesforce**&#x200B;組態精靈的範例：

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >若要核准設定，您必須登出並返回Adobe Campaign主控台。

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;節點中檢查在Adobe Campaign中產生的結構。

   **Salesforce**&#x200B;結構範例：

   ![](assets/crm_connectors_sfdc_table.png)

1. 架構建立後，您就可以透過CRM自動同步枚舉至Adobe Campaign。

   若要這麼做，請按一下&#x200B;**[!UICONTROL Synchronizing enumerations...]**&#x200B;連結，然後選取符合CRM列舉的Adobe Campaign列舉。

   >[!NOTE]
   >
   >您可以將Adobe Campaign枚舉的所有值取代為CRM的值：若要這麼做，請在&#x200B;**[!UICONTROL Replace]**&#x200B;欄中選取&#x200B;**[!UICONTROL Yes]**。

   **Salesforce**&#x200B;枚舉範例：

   ![](assets/crm_connectors_sfdc_enum.png)

   按一下&#x200B;**[!UICONTROL Next]** ，然後按一下&#x200B;**[!UICONTROL Start]**&#x200B;開始導入清單。

1. 檢查&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;菜單中導入的值。

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > 不支援Salesforce中的多個選擇列舉。

1. 若要同步Adobe Campaign資料與CRM系統之間的資料，您必須建立工作流程並使用&#x200B;**[!UICONTROL CRM connector]**&#x200B;活動。

   ![](assets/crm_connectors_sfdc_wf.png)

   在本頁](../../platform/using/crm-data-sync.md)中進一步瞭解資料同步[。
