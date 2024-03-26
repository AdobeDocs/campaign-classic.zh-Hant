---
product: campaign
title: 管線選項NmsPipeline_Config
description: 管線選項NmsPipeline_Config
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# 管線選項NmsPipeline_Config {#nmspipeline_config}



驗證作業完成後， [!DNL pipelined] 可以擷取事件並進行處理。 它只會處理在Adobe Campaign中設定的觸發器，忽略其他觸發器。 觸發器必須預先從Analytics產生並推送至管道。
也可以使用萬用字元設定選項，以擷取所有觸發程式，不論名稱為何。

觸發器的設定是在下的選項中完成 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. 選項名稱為 **[!UICONTROL NmsPipeline_Config]**. 資料型別是JSON格式的「長文字」。

此範例指定兩個觸發程式。

將此範本的JSON程式碼貼入選項值中。 請確定移除註解。

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
            "triggers": [ // Array of triggers. 
                {
                    "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                    "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
                }, {
                    "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                    "jsConnector": "cus:triggers.js" // Can use the same JS for all.
                },
            ]
        }
    ]
}
```

第二個範例會擷取所有觸發器。

```
{
 "topics": [
    {
      "name": "triggers",
      "consumer":  "customer_dev",
      "triggers": [
        {
          "name": "*",
          "jsConnector": "cus:pipeline.js"
        }
      ]
    }
 ]
 }
```

>[!NOTE]
>
>此 [!DNL Trigger] Analytics介面中特定觸發程式名稱的UID值，可作為觸發程式介面中的URL查詢字串引數的一部分找到。 triggerType UID會傳入管道資料流中，而程式碼可寫入pipeline.JS中，以將觸發程式UID對應至使用者易記標籤，該標籤可儲存在pipelineEvents架構的「觸發程式名稱」欄中。

## 取用者引數 {#consumer-parameter}

此管道可與「供應商和消費者」模型搭配使用。 相同佇列上可能有許多消費者。 訊息僅「使用」給個別消費者。 每個消費者都會取得其專屬的訊息「復本」。

「consumer」引數會將執行個體識別為以下其中一個consumer。 這是呼叫管道之執行個體的身分。 您可以使用實體名稱來填入。 管道服務會追蹤每個取用者擷取的訊息。 針對不同的執行個體使用不同的取用者，可確保將每則訊息都傳送至每個執行個體。

## 如何設定管道選項 {#configure-pipeline-option}

在「觸發程式」陣列下新增或編輯Experience Cloud觸發程式；請勿編輯其餘的觸發程式。
透過此說明，確認JSON有效 [網站](https://jsonlint.com/).

* &quot;name&quot;是觸發程式ID。 萬用字元「*」會攔截所有觸發器。
* 「消費者」是任何可唯一識別nlserver執行個體的唯一字串。 它通常可以是例項名稱本身。 針對多個環境（開發/舞台/prod），請確定每個環境都具有唯一性，以便每個例項都能取得訊息的副本。
* [!DNL Pipelined] 也支援「別名」主題。

重新啟動 [!DNL pipelined] 進行變更之後。
