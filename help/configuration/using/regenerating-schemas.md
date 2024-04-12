---
product: campaign
title: 重新產生方案
description: 瞭解如何重新產生Campaign綱要
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 2%

---

# 重新產生方案{#regenerating-schemas}

當您修改架構並儲存修改內容時，系統會自動產生擴充架構。 不過，您可能需要手動重新產生結構描述以套用修改。 操作步驟：

1. 選取您需要重新產生的結構描述。
1. 按一下滑鼠右鍵並選擇 **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. 按一下 **[!UICONTROL OK]** 以確認並啟動程式。

然後，您可以在預覽和檔案索引標籤中檢查產生的結構描述的結構。 有關詳細資訊，請參閱 [原則](../../configuration/using/data-schemas.md#principles) 區段。

>[!NOTE]
>
>如果您需要強制重新產生所有結構描述，例如解決反向連結中的某些相依性問題，您可以從Adobe Campaign應用程式伺服器啟動下列命令：
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>接著，您必須重新啟動Adobe Campaign應用程式伺服器，並中斷使用者端主控台的連線/重新連線。
