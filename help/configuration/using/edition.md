---
solution: Campaign Classic
product: campaign
title: 版本
description: 版本
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: d6993725ed4060f2affce98c4a8a5211bda03bdf
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 1%

---


# 編輯促銷活動檔案總管導覽樹{#edition}

可通過&#x200B;**[!UICONTROL Administration > Configuration > Navigation hierarchies]**&#x200B;節點訪問用於建立和配置導航層次配置文檔的螢幕：

![](assets/d_ncs_integration_navigation_arbo.png)

導覽階層組態會分為數個XML檔案。 它的運作方式與模式擴展類似：所有文檔都會合併，以生成包含整個配置的單個文檔。 此檔案無法編輯，並透過「預覽」標籤顯示。

編輯欄位提供XML文檔的內容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>「名稱」編輯控制項可讓您輸入由名稱和名稱空間組成的檔案索引鍵。 **`<navtree>`**&#x200B;元素的&quot;name&quot;和&quot;namespace&quot;屬性會在架構的XML編輯欄位中自動更新。

預覽會自動產生包含完整組態的合併檔案：

![](assets/d_ncs_integration_navigation_preview.png)

