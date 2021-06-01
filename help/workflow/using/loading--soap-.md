---
product: campaign
title: 載入 (SOAP)
description: 載入 (SOAP)
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 20414e73-2ba9-44f9-8e16-cb6604933ee0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---

# 載入 (SOAP){#loading-soap}

>[!CAUTION]
>
>**載入(SOAP)**&#x200B;活動僅在您已安裝&#x200B;**FDA（同盟資料存取）**&#x200B;模組時才可用。 請檢查您的授權合約。

當無法透過外部資料庫中的FDA直接收集資料時，除了&#x200B;**資料載入(RDBMS)**&#x200B;活動外，還會使用&#x200B;**載入(SOAP)**&#x200B;活動。

操作如下：

1. 在使用XML示例或WSDL之間選擇。

   以下示例來自消息中心模組的技術工作流。

   ![](assets/load_soap_002.png)

1. 對於XML示例，請選擇一個示例檔案。 分析該檔案以建立結果示例。

   對於WSDL，輸入匹配的訪問URL，然後生成框架代碼。 系統會自動更新並顯示選取的服務和呼叫。

   ![](assets/soap_load_003.png)

1. 選擇&#x200B;**[!UICONTROL Click here to view and edit analysis results]**&#x200B;以指定每個已標識列。

   ![](assets/soap_load_001.png)

   如果要更新該示例，請選擇&#x200B;**[!UICONTROL Re-analyze the example]**。

   您也可以透過&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;連結個人化欄資料的格式。 有關格式化導入資料的詳細資訊，請參閱此[節](../../platform/using/executing-import-jobs.md)。

1. 您可以使用行號做為識別碼，和/或指定SOAP呼叫傳回數個元素。
1. 根據其函式輸入以下Tab指令碼：

   * **[!UICONTROL Initialization]**:建立SOAP連接。
   * **[!UICONTROL Iteration]**:執行對SOAP服務的調用。此函式的返回必須是與示例或WSDL的說明相容的XML對象。

      Adobe Campaign會在回圈中呼叫此標籤的程式碼，直到傳回空的XML物件為止。

   * **[!UICONTROL Finalization]**:關閉連接和/或釋放處理期間建立的其他資源。
