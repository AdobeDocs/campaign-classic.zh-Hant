---
product: campaign
title: 載入 (SOAP)
description: 載入 (SOAP)
feature: Workflows
exl-id: 20414e73-2ba9-44f9-8e16-cb6604933ee0
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---

# 載入 (SOAP){#loading-soap}

![](../../assets/common.svg)

>[!CAUTION]
>
>的 **載入(SOAP)** 活動僅在您 **FDA（聯合資料存取）** 已安裝模組。 請檢查您的授權合約。

的 **載入(SOAP)** 除 **資料載入(RDBMS)** 當無法通過外部資料庫中的FDA直接收集資料時，將執行活動。

操作如下：

1. 選擇使用XML示例或WSDL。

   以下示例來自消息中心模組的技術工作流。

   ![](assets/load_soap_002.png)

1. 對於XML示例，選擇示例檔案。 分析檔案以建立結果示例。

   對於WSDL，輸入匹配訪問URL，然後生成骨骼代碼。 選定的服務和呼叫將自動更新並顯示。

   ![](assets/soap_load_003.png)

1. 選擇 **[!UICONTROL Click here to view and edit analysis results]** 指定每個標識列。

   ![](assets/soap_load_001.png)

   如果要更新示例，請選擇 **[!UICONTROL Re-analyze the example]**。

   您還可以通過 **[!UICONTROL Advanced parameters]** 的子菜單。 有關格式化導入資料的詳細資訊，請參閱此 [節](../../platform/using/executing-import-jobs.md)。

1. 您可以將行號用作標識符和/或指定SOAP調用返回多個元素。
1. 根據頁籤指令碼的功能輸入以下頁籤指令碼：

   * **[!UICONTROL Initialization]**:建立SOAP連接。
   * **[!UICONTROL Iteration]**:執行對SOAP服務的調用。 此函式的返回必須是與示例或WSDL的說明相容的XML對象。

      此頁籤的代碼將由Adobe Campaign在循環中調用，直到返回空XML對象。

   * **[!UICONTROL Finalization]**:關閉連接和/或釋放處理過程中建立的其他資源。
