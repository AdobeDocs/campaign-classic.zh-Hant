---
solution: Campaign Classic
product: campaign
title: Campaign - Salesforce CRM連接器
description: Connect Campaign和Salesforce.com
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
translation-type: tm+mt
source-git-commit: 3e3a5250f165677026557a4e2249fc683aa23d57
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Connect Campaign和Salesforce.com{#connect-to-sfdc}

在本頁中，您將學習如何將Campaign Classic連接至&#x200B;**Salesforce**。

資料同步通過專用的工作流活動執行。 [了解更多](../../platform/using/crm-data-sync.md)。


外部帳戶可讓您將Salesforce資料匯入並匯出至Adobe Campaign。
若要設定Salesforce的CRM Connector，請遵循下列步驟：

1. 通過Adobe Campaign樹的&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;節點建立新的外部帳戶。
1. 選取 **[!UICONTROL Salesforce.com]**。
1. 輸入設定以啟用連接。

   ![](assets/ext_account_17.png)

   若要設定Salesforce CRM外部帳戶以搭配Adobe Campaign使用，您必須提供下列詳細資訊：

   * **[!UICONTROL Account]**
用來登入Salesforce CRM的帳戶。

   * **[!UICONTROL Password]**
用於登入Salesforce CRM的密碼。

   * **[!UICONTROL Client identifier]**
若要知道在何處找到您的客戶識別碼，請參閱本 [頁](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

   * **[!UICONTROL Security token]**
若要瞭解在何處找到您的安全Token，請參閱本 [頁](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

   * **[!UICONTROL API version]**
選擇API的版本。
1. 運行配置嚮導以生成可用的CRM表：配置嚮導可讓您收集表並建立匹配的模式。

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >若要核准設定，您必須登出並返回Adobe Campaign主控台。

1. 在&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;節點中檢查在Adobe Campaign生成的模式。

   **Salesforce**&#x200B;結構範例：

   ![](assets/crm_connectors_sfdc_table.png)

1. 架構建立後，您就可以自動將枚舉從Salesforce同步至Adobe Campaign。

   若要這麼做，請按一下&#x200B;**[!UICONTROL Synchronizing enumerations...]**&#x200B;連結，並選取符合Salesforce列舉的Adobe Campaign列舉。



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >您可以將Adobe Campaign枚舉的所有值替換為CRM的值：若要這麼做，請在&#x200B;**[!UICONTROL Replace]**&#x200B;欄中選取&#x200B;**[!UICONTROL Yes]**。


   按一下&#x200B;**[!UICONTROL Next]** ，然後按一下&#x200B;**[!UICONTROL Start]**&#x200B;開始導入清單。

1. 檢查&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;菜單中導入的值。

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > 不支援多個選擇枚舉。

Campaign和Salesforce.com現在已連接。 您可以在兩個系統之間設定資料同步。

要同步Adobe Campaign資料和SFDC之間的資料，您需要建立工作流並使用&#x200B;**[!UICONTROL CRM connector]**&#x200B;活動。

![](assets/crm_connectors_sfdc_wf.png)

在本頁](../../platform/using/crm-data-sync.md)中進一步瞭解資料同步[。
