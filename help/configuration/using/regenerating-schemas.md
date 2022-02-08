---
product: campaign
title: 重新生成方案
description: 瞭解如何重新生成市場活動方案
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 2%

---

# 重新生成方案{#regenerating-schemas}

![](../../assets/v7-only.svg)

修改方案並保存修改後，將自動生成擴展方案。 不過，您可能需要手動重新生成方案以應用修改。 操作步驟：

1. 選擇要重新生成的架構。
1. 按一下右鍵並選擇 **[!UICONTROL Actions > Regenerate selected schemas...]** 。
1. 按一下 **[!UICONTROL OK]** 確認並啟動進程。

然後，可以在「預覽」和「文檔」頁籤中檢查生成的架構的結構。 有關詳細資訊，請參閱 [原則](../../configuration/using/data-schemas.md#principles) 的子菜單。

>[!NOTE]
>
>如果需要強制重新生成所有架構，例如，要解決反向連結中的某些依賴關係問題，可以從Adobe Campaign應用程式伺服器啟動以下命令：
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>然後，必須重新啟動Adobe Campaign應用程式伺服器並斷開連接/重新連接到客戶端控制台。
