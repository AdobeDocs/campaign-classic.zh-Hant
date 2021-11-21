---
product: campaign
title: Campaign - Salesforce CRM連接器
description: 連接Campaign和Salesforce.com
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# 連接Campaign和Salesforce.com{#connect-to-sfdc}

![](../../assets/common.svg)

在本頁面中，您將學習如何將Campaign Classic連結至 **Salesforce**.

資料同步是透過專用的工作流程活動執行。 [深入瞭解](../../platform/using/crm-data-sync.md)。


外部帳戶可讓您將Salesforce資料匯入和匯出至Adobe Campaign。
要配置Salesforce的CRM連接器，請執行以下步驟：

1. 透過 **[!UICONTROL Administration > Platform > External accounts]** Adobe Campaign樹的節點。
1. 選取 **[!UICONTROL Salesforce.com]**。
1. 輸入啟用連接的設定。

   ![](assets/ext_account_17.png)

   若要設定Salesforce CRM外部帳戶以搭配Adobe Campaign運作，您需要提供下列詳細資訊：

   * **[!UICONTROL Account]**
用於登入Salesforce CRM的帳戶。

   * **[!UICONTROL Password]**
用於登入Salesforce CRM的密碼。

   * **[!UICONTROL Client identifier]**
若要了解在何處尋找用戶端識別碼，請參閱 [頁面](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL Security token]**
若要了解在何處尋找您的安全代號，請參閱 [頁面](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL API version]**
選取API的版本。
1. 運行配置嚮導以生成可用的CRM表：配置嚮導允許您收集表並建立匹配的架構。

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >若要核准設定，您必須註銷並返回Adobe Campaign主控台。

1. 檢查在Adobe Campaign中產生的結構 **[!UICONTROL Administration > Configuration > Data schemas]** 節點。

   範例 **Salesforce** 方案：

   ![](assets/crm_connectors_sfdc_table.png)

1. 建立結構後，您就可以自動將列舉從Salesforce同步至Adobe Campaign。

   若要這麼做，請按一下 **[!UICONTROL Synchronizing enumerations...]** 連結，並選取符合Salesforce分項的Adobe Campaign分項清單。



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >您可以將Adobe Campaign分項清單的所有值取代為CRM的值：要執行此操作，請選取 **[!UICONTROL Yes]** 在 **[!UICONTROL Replace]** 欄。


   按一下 **[!UICONTROL Next]** 然後 **[!UICONTROL Start]** 以開始導入清單。

1. 檢查 **[!UICONTROL Administration > Platform > Enumerations]** 功能表。

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > 不支援多個選擇枚舉。

Campaign和Salesforce.com現已連接。 您可以在兩個系統之間設定資料同步。

若要同步Adobe Campaign資料和SFDC之間的資料，您需要建立工作流程，並使用 **[!UICONTROL CRM connector]** 活動。

![](assets/crm_connectors_sfdc_wf.png)

深入了解資料同步 [在本頁](../../platform/using/crm-data-sync.md).
