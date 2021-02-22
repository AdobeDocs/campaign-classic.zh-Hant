---
solution: Campaign Classic
product: campaign
title: 配置整合
description: 配置整合
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 2%

---


# 管線選項 NmsPipeline_Config {#nmspipeline_config}

一旦驗證生效，[!DNL pipelined]就可以檢索事件並處理它們。 它只會處理在Adobe Campaign中設定的觸發程式，而忽略其他觸發程式。 觸發器必須是從Analytics產生，並事先推送至管道。
也可以使用通配符配置該選項，以捕獲所有觸發器（無論名稱）。

觸發器的配置是在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;下的選項中完成的。 選項名稱為&#x200B;**[!UICONTROL NmsPipeline_Config]**。 資料類型是JSON格式的「長文字」。

此示例指定兩個觸發器。

從此範本將JSON代碼貼入選項值。 請確定移除注釋。

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
>Analytics介面中特定觸發器名稱的[!DNL Trigger] UID值，可在Triggers介面中作為URL查詢字串參數的一部分找到。 triggerType UID會傳遞至管線資料串流，而程式碼可寫入pipeline.JS，將觸發器UID對應至使用者友好標籤，此標籤可儲存在pipelineEvents架構的「觸發器名稱」欄中。

## consumer參數{#consumer-parameter}

該管道與「供應商和消費者」模式搭配使用。 同一佇列上可能有許多消費者。 消息僅「被使用」給單個消費者。 每個消費者都會收到自己的訊息「復本」。

「consumer」參數會將例項識別為其中一個使用者。 它是調用流水線的實例的標識。 您可以用例項名稱來填入。 流水線服務跟蹤每個消費者檢索的消息。 針對不同的例項使用不同的使用者，可確保每則訊息都會傳送至每個例項。

## 如何配置管線選項{#configure-pipeline-option}

在「觸發器」陣列下新增或編輯Experience Cloud觸發器；不要編輯其餘的。
請確定JSON在此[網站](http://jsonlint.com/)的協助下有效。

* &quot;name&quot;是觸發器ID。 萬用字元&quot;*&quot;會擷取所有觸發器。
* &quot;Consumer&quot;是唯一識別nlserver例項的任何唯一字串。 它通常可以是實例名稱本身。 對於多個環境(dev/stage/prod)，請確保每個環境都具有唯一性，以便每個實例都獲得消息的副本。
* [!DNL Pipelined] 也支援「別名」主題。

進行更改後重新啟動[!DNL pipelined]。
