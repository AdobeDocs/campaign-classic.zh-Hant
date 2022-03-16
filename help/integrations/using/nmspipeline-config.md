---
product: campaign
title: 管線選項 NmsPipeline_Config
description: 管線選項 NmsPipeline_Config
audience: integrations
content-type: reference
source-git-commit: 36b10a49fe92853f98beeb9e7d2fea3f59b10b6f
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 3%

---


# 管線選項 NmsPipeline_Config {#nmspipeline_config}

![](../../assets/common.svg)

一旦驗證成功， [!DNL pipelined] 可以檢索事件並處理它們。 它只處理在Adobe Campaign配置的觸發器，而忽略其他觸發器。 觸發器必須是從Analytics生成的，並提前推入管道。
也可以使用通配符配置該選項，以捕獲所有觸發器，而不考慮名稱。

觸發器的配置在以下選項中完成 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**。 選項名為 **[!UICONTROL NmsPipeline_Config]**。 資料類型為JSON格式的「長文本」。

此示例指定兩個觸發器。

將此模板中的JSON代碼貼上到選項值中。 確保刪除注釋。

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

第二個示例捕獲所有觸發器。

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
>的 [!DNL Trigger] 在「分析」介面中，特定觸發器名稱的UID值可作為「觸發器」介面中URL查詢字串參數的一部分找到。 triggerType UID在管道資料流中傳遞，代碼可以寫入管道中。JS將觸發器UID映射到用戶友好標籤，該標籤可以儲存在pipelineEvents架構的「觸發器名稱」列中。

## 使用者參數 {#consumer-parameter}

該管道與「供應商和消費者」模型配合工作。 同一隊列中可能有許多使用者。 消息僅對單個用戶「使用」。 每個消費者都會得到自己的「副本」。

「consumer」參數將實例標識為這些使用者之一。 它是調用管道的實例的標識。 可以用實例名稱填充它。 管道服務跟蹤每個使用者檢索到的消息。 對不同實例使用不同的使用者可確保將每個消息發送到每個實例。

## 如何配置管道選項 {#configure-pipeline-option}

在「觸發器」陣列下添加或編輯Experience Cloud觸發器；不要編輯其餘內容。
確保JSON在此幫助下有效 [網站](https://jsonlint.com/)。

* &quot;name&quot;是觸發器ID。 通配符「*」可捕獲所有觸發器。
* &quot;Consumer&quot;是唯一標識nlserver實例的任何唯一字串。 它通常可以是實例名稱本身。 對於多個環境(dev/stage/prod)，請確保每個環境都具有唯一性，以便每個實例都獲得消息的副本。
* [!DNL Pipelined] 還支援「別名」主題。

重新啟動 [!DNL pipelined] 進行更改。
