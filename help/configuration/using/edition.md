---
title: 版本
seo-title: 版本
description: 版本
seo-description: null
page-status-flag: never-activated
uuid: df9298fc-5f62-4afb-8118-ca7e3987e81f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: 820be231-af76-44ce-8f4d-cd5eae1eb169
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 版本{#edition}

可通過節點訪問用於建立和配置導航層次結構配置文檔的 **[!UICONTROL Administration > Configuration > Navigation hierarchies]** 螢幕：

![](assets/d_ncs_integration_navigation_arbo.png)

導覽階層組態會分為數個XML檔案。 它的運作方式與模式擴展類似：所有文檔都會合併，以生成包含整個配置的單個文檔。 此檔案無法編輯，並透過「預覽」標籤顯示。

編輯欄位提供XML文檔的內容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>「名稱」編輯控制項可讓您輸入由名稱和名稱空間組成的檔案索引鍵。 元素的「name」和「namespace」屬性 **`<navtree>`** 會在架構的XML編輯欄位中自動更新。

預覽會自動產生包含完整組態的合併檔案：

![](assets/d_ncs_integration_navigation_preview.png)

