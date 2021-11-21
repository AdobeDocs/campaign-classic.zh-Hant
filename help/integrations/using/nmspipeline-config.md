---
product: campaign
title: 配置整合
description: 配置整合
audience: integrations
content-type: reference
source-git-commit: c6d5e597a02a1210507b0c6d84ab7d170e877eb1
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 2%

---


# 管線選項 NmsPipeline_Config {#nmspipeline_config}

![](../../assets/common.svg)

驗證一旦運作， [!DNL pipelined] 可以擷取事件並加以處理。 它只會處理在Adobe Campaign中設定的觸發器，而忽略其他觸發器。 觸發器必須從Analytics產生，並預先推送至管道。
選項也可以設定萬用字元來擷取所有觸發器（無論名稱為何）。

觸發器的設定是在下方的選項中完成 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. 選項名稱為 **[!UICONTROL NmsPipeline_Config]**. 資料類型為JSON格式的「長文字」。

此範例指定兩個觸發器。

將此範本的JSON程式碼貼入選項值。 請務必移除備注。

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
>此 [!DNL Trigger] 在Analytics介面中，特定觸發器名稱的UID值可作為觸發器介面中URL查詢字串參數的一部分找到。 triggerType UID會傳入管道資料流，且程式碼可寫入pipeline.JS中，以將觸發器UID對應至使用者易記標籤，該標籤可儲存在pipelineEvents架構的「觸發器名稱」欄中。

## 消費者參數 {#consumer-parameter}

管道與「供應商和消費者」模式搭配使用。 同一隊列中可能有許多消費者。 訊息只會「使用」給個別消費者。 每個消費者都有自己的訊息「副本」。

「消費者」參數會將執行個體識別為其中一個消費者。 此為呼叫管道之執行個體的身分。 您可以以執行個體名稱填入。 管道服務可追蹤每個消費者擷取的訊息。 針對不同的例項使用不同的使用者，可確保將每則訊息傳送至每個例項。

## 如何配置管道選項 {#configure-pipeline-option}

在「觸發器」陣列下新增或編輯Experience Cloud觸發器；請勿編輯其餘內容。
在此協助下，確認JSON有效 [網站](https://jsonlint.com/).

* &quot;name&quot;是觸發器ID。 萬用字元「*」會擷取所有觸發器。
* &quot;Consumer&quot;是唯一識別nlserver例項的任何唯一字串。 通常可以是例項名稱本身。 對於多個環境(dev/stage/prod)，請確定每個環境都是唯一的，以便每個執行個體都能收到訊息的副本。
* [!DNL Pipelined] 也支援「別名」主題。

重新啟動 [!DNL pipelined] 進行變更後才會執行。
