---
product: campaign
title: 版本
description: 編輯
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# 編輯市場活動瀏覽器導航樹{#edition}

![](../../assets/v7-only.svg)

可通過 **[!UICONTROL Administration > Configuration > Navigation hierarchies]** 節點：

![](assets/d_ncs_integration_navigation_arbo.png)

導航層次結構配置被劃分到多個XML文檔上。 它遵循與模式擴展類似的原則：合併所有文檔以生成包含整個配置的單個文檔。 此文檔無法編輯，並通過「預覽」頁籤顯示。

編輯欄位提供XML文檔的內容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>「名稱」編輯控制項允許您輸入由名稱和命名空間組成的文檔密鑰。 的「name」和「namespace」屬性 **`<navtree>`** 元素將在架構的XML編輯欄位中自動更新。

預覽將自動生成包含完整配置的合併文檔：

![](assets/d_ncs_integration_navigation_preview.png)
