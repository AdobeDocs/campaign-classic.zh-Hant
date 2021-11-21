---
product: campaign
title: 重新產生方案
description: 重新產生方案
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 7%

---

# 重新產生方案{#regenerating-schemas}

![](../../assets/v7-only.svg)

修改架構並儲存修改時，會自動產生擴充架構。 不過，您可能需要手動重新產生結構以套用修改。 操作步驟：

1. 選取要重新產生的架構。
1. 按一下右鍵並選擇 **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. 按一下 **[!UICONTROL OK]** 以確認並啟動程式。

然後，您可以在「預覽」和「檔案」標籤中檢查所產生結構。 有關詳細資訊，請參閱 [原則](../../configuration/using/data-schemas.md#principles) 區段。

>[!NOTE]
>
>如果需要強制重新生成所有架構，例如為了解決反向連結中的某些相關性問題，可以從Adobe Campaign應用程式伺服器啟動以下命令：
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>然後，您必須重新啟動Adobe Campaign應用程式伺服器，並中斷用戶端主控台的連線/重新連線至用戶端主控台。
