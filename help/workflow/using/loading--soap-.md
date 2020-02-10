---
title: 載入(SOAP)
seo-title: 載入(SOAP)
description: 載入(SOAP)
seo-description: null
page-status-flag: never-activated
uuid: 80597892-e363-48f6-8633-faad161064a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 94178104-f8ba-4c17-8ff9-928c5d2df1b7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 載入(SOAP){#loading-soap}

>[!CAUTION]
>
>只有在 **安裝了** FDA(Federated Data Access)模組時，才可使用Loading(SOAP)活動 **** 。 請檢查您的授權合約。

當無 **法在外部資料庫中透過FDA直接收集資料時，除了資料載入(****** RDBMS)活動外，還會使用「載入(SOAP)」活動。

操作如下：

1. 在使用XML示例或WSDL之間進行選擇。

   以下示例來自消息中心模組的技術工作流。

   ![](assets/load_soap_002.png)

1. 對於XML示例，請選擇一個示例檔案。 分析該檔案以建立結果示例。

   對於WSDL，輸入匹配的訪問URL，然後生成框架代碼。 所選的服務和呼叫會自動更新並顯示。

   ![](assets/soap_load_003.png)

1. 選擇 **[!UICONTROL Click here to view and edit analysis results]** 以指定每個標識的列。

   ![](assets/soap_load_001.png)

   如果要更新示例，請選擇 **[!UICONTROL Re-analyze the example]**。

   您也可以透過連結個人化欄資料的 **[!UICONTROL Advanced parameters]** 格式。 有關格式化導入資料的詳細資訊，請參 [閱](../../platform/using/importing-data.md#import-wizard)。

1. 您可以使用行號作為識別碼，並／或指定SOAP呼叫傳回數個元素。
1. 根據頁籤指令碼的函式輸入以下頁籤指令碼：

   * **[!UICONTROL Initialization]**:建立SOAP連線。
   * **[!UICONTROL Iteration]**:執行對SOAP服務的調用。 此函式的傳回必須是與範例或WSDL說明相容的XML物件。

      Adobe Campaign會循環呼叫此標籤的程式碼，直到傳回空的XML物件。

   * **[!UICONTROL Finalization]**:關閉連接和／或釋放處理過程中建立的其他資源。

