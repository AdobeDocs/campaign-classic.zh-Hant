---
product: campaign
title: 重新產生結構描述
description: 瞭解如何重新產生行銷活動結構描述
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 2%

---

# 重新產生結構描述{#regenerating-schemas}

當您修改方案並儲存修改內容時，擴充方案會自動產生。 不過，您可能需要手動重新產生結構描述才能套用修改。 操作步驟：

1. 選取您需要重新產生的結構描述。
1. 按一下滑鼠右鍵並選擇 **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. 按一下 **[!UICONTROL OK]** 以確認並啟動程式。

然後，您可以在「預覽」和「檔案」標籤中檢查產生的結構描述的結構。 如需詳細資訊，請參閱 [原則](../../configuration/using/data-schemas.md#principles) 區段。

>[!NOTE]
>
>如果您需要強制重新產生所有結構描述（例如，為了解決反向連結中的特定相依性問題），您可以從Adobe Campaign應用程式伺服器啟動以下命令：
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>接著，您必須重新啟動Adobe Campaign應用程式伺服器，並中斷使用者端主控台的連線/重新連線。
