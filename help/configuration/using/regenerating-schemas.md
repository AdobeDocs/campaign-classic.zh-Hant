---
solution: Campaign Classic
product: campaign
title: 重新生成結構
description: 重新生成結構
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# 重新生成結構{#regenerating-schemas}

當您修改架構並保存修改時，將自動生成擴展架構。 不過，您可能需要手動重新產生結構以套用修改。 操作步驟：

1. 選擇要重新生成的方案。
1. 按一下右鍵並選擇&#x200B;**[!UICONTROL Actions > Regenerate selected schemas...]**。
1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;確認並啟動進程。

然後，您可以在「預覽」和「文檔」頁籤中檢查生成的架構的結構。 有關詳細資訊，請參閱[Pricens](../../configuration/using/data-schemas.md#principles)部分。

>[!NOTE]
>
>如果您需要強制重新產生所有結構，例如為瞭解決反向連結中的某些相依性問題，您可以從Adobe Campaign應用程式伺服器啟動下列命令：
>
>**nlserver config -postupgrade -instance:&#39;&lt;instance_name>&#39; -force**
>
>然後，您必須重新啟動Adobe Campaign應用程式伺服器，並中斷連線／重新連線至用戶端主控台。
