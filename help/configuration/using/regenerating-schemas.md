---
product: campaign
title: 重新產生方案
description: 瞭解如何重新產生Campaign綱要
feature: Custom Resources
role: Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
TQID: 'https://experienceleague.adobe.com/gkWtbp4Vw-wY5yHsd4xJbDx04u3aPhdg-8kB5OXZu94'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 2%
---
# 重新產生方案{#regenerating-schemas}

當您修改架構並儲存修改內容時，系統會自動產生擴充架構。 不過，您可能需要手動重新產生結構描述以套用修改。 操作步驟：

1. 選取您需要重新產生的結構描述。
1. 按一下滑鼠右鍵並選擇&#x200B;**[!UICONTROL Actions > Regenerate selected schemas...]** 。
1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;以確認並啟動程式。

然後，您可以在預覽和檔案索引標籤中檢查產生的結構描述的結構。 如需詳細資訊，請參閱[原則](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/create-schema){target="_blank"} （Campaign v8檔案）區段。

>[!NOTE]
>
>如果您需要強制重新產生所有結構描述，例如解決反向連結中的某些相依性問題，您可以從Adobe Campaign應用程式伺服器啟動下列命令：
>
> `nlserver config -postupgrade -instance:`&lt;執行個體名稱>` -force`
>
>接著，您必須重新啟動Adobe Campaign應用程式伺服器，並中斷使用者端主控台的連線/重新連線。
