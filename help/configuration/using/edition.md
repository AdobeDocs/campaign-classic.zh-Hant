---
product: campaign
title: 版本
description: 版本
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 1%

---

# 編輯促銷活動總管導覽樹{#edition}

![](../../assets/v7-only.svg)

建立和配置導航層次結構配置文檔的螢幕可通過 **[!UICONTROL Administration > Configuration > Navigation hierarchies]** 節點：

![](assets/d_ncs_integration_navigation_arbo.png)

導航層次結構配置被劃分為多個XML文檔。 其運作方式與綱要擴充功能類似：所有文檔都合併，以生成包含整個配置的單個文檔。 無法編輯此文檔，並通過「預覽」頁簽顯示。

編輯欄位提供XML文檔的內容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>「名稱」編輯控制項可讓您輸入由名稱和命名空間組成的檔案索引鍵。 的「name」和「namespace」屬性 **`<navtree>`** 元素會在架構的XML編輯欄位中自動更新。

預覽會自動生成包含完整配置的合併文檔：

![](assets/d_ncs_integration_navigation_preview.png)
