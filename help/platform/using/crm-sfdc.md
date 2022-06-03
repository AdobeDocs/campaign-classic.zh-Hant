---
product: campaign
title: 市場活動 — Salesforce CRM連接器
description: 瞭解如何連接市場活動和銷售人員
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
source-git-commit: 9a6010d824794b01224f40bb2912a9a80fc0fb88
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 連接市場活動和Salesforce.com{#connect-to-sfdc}

![](../../assets/v7-only.svg)

在此頁中，您將學習如何將Campaign Classic連接到 **Salesforce**。

資料同步通過專用工作流活動執行。 [了解更多資訊](../../platform/using/crm-data-sync.md)。


外部帳戶允許您將Salesforce資料導入和導出到Adobe Campaign。
要為Salesforce配置CRM Connector，請執行以下步驟：

1. 通過 **[!UICONTROL Administration > Platform > External accounts]** Adobe Campaign樹的節點。
1. 選取 **[!UICONTROL Salesforce.com]**。
1. 輸入設定以啟用連接。

   ![](assets/ext_account_17.png)

   要配置Salesforce CRM外部帳戶以與Adobe Campaign協作，您需要提供以下詳細資訊：

   * **[!UICONTROL Account]**
用於登錄Salesforce CRM的帳戶。

   * **[!UICONTROL Password]**
用於登錄Salesforce CRM的密碼。

   * **[!UICONTROL Client identifier]**
要知道在何處查找客戶端標識符，請參閱 [頁](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

   * **[!UICONTROL Security token]**
要瞭解在何處查找安全令牌，請參閱此 [頁](https://help.salesforce.com/articleView?id=000205876&amp;type=1)。

   * **[!UICONTROL API version]**
選擇API的版本。
1. 運行配置嚮導以生成可用的CRM表：使用配置嚮導可以收集表並建立匹配的架構。

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >要批准該設定，您需要註銷並重新登錄到Adobe Campaign控制台。

1. 檢查在中的Adobe Campaign中生成的架構 **[!UICONTROL Administration > Configuration > Data schemas]** 的下界。

   示例 **Salesforce** 架構：

   ![](assets/crm_connectors_sfdc_table.png)

1. 建立架構後，可以自動將枚舉從Salesforce同步到Adobe Campaign。

   要執行此操作，請按一下 **[!UICONTROL Synchronizing enumerations...]** 連結並選擇與Salesforce枚舉匹配的Adobe Campaign枚舉。



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >可以將Adobe Campaign枚舉的所有值替換為CRM的值：要執行此操作，請選擇 **[!UICONTROL Yes]** 的 **[!UICONTROL Replace]** 的雙曲餘切值。


   按一下 **[!UICONTROL Next]** 然後 **[!UICONTROL Start]** 開始導入清單。

1. 檢查 **[!UICONTROL Administration > Platform > Enumerations]** 的子菜單。

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > 不支援多個選擇枚舉。

市場活動和Salesforce.com現在已連接。 可以設定兩個系統之間的資料同步。

要在Adobe Campaign資料和SFDC之間同步資料，您需要建立工作流並使用 **[!UICONTROL CRM connector]** 的子菜單。

![](assets/crm_connectors_sfdc_wf.png)

瞭解有關資料同步的詳細資訊 [此頁](../../platform/using/crm-data-sync.md)。
