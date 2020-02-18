---
title: 重新生成結構
seo-title: 重新生成結構
description: 重新生成結構
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 重新生成結構{#regenerating-schemas}

當您修改架構並保存修改時，將自動生成擴展架構。 不過，您可能需要手動重新產生結構以套用修改。 操作步驟：

1. 選擇要重新生成的方案。
1. 按一下滑鼠右鍵並選擇 **[!UICONTROL Actions > Regenerate selected schemas...]** 。
1. 按一下 **[!UICONTROL OK]** 確認並啟動進程。

然後，您可以在「預覽」和「文檔」頁籤中檢查生成的架構的結構。 For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>如果您需要強制重新產生所有結構，例如為瞭解決反向連結中的某些相依性問題，您可以從Adobe Campaign應用程式伺服器啟動下列命令：
>
>**nlserver config -postupgrade -instance:`&lt;instance_name>&#39; -force**
>
>然後，您必須重新啟動Adobe Campaign應用程式伺服器，並中斷連線／重新連線至用戶端主控台。
