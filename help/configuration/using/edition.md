---
product: campaign
title: 編輯Campaign Explorer導覽樹狀結構
description: 編輯Campaign Explorer導覽樹狀結構
feature: Application Settings
role: Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
TQID: https://experienceleague.adobe.com/k8LhZvPSYchAxnQew5eknkDbxHDznzPefl032auuYLc
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 131
ht-degree: 0%

---

# 編輯Campaign Explorer導覽樹狀結構{#edition}

可透過&#x200B;**[!UICONTROL Administration > Configuration > Navigation hierarchies]**&#x200B;節點存取用來建立和設定導覽階層組態檔案的畫面：

![](assets/d_ncs_integration_navigation_arbo.png)

導覽階層組態會分為數個XML檔案。 其運作原理與架構延伸類似：所有檔案會合併以產生包含整個設定的單一檔案。 此檔案無法編輯，並會透過「預覽」索引標籤顯示。

編輯欄位提供XML檔案的內容：

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>「名稱」編輯控制項可讓您輸入由名稱和名稱空間組成的檔案金鑰。 **`<navtree>`**&#x200B;專案的「名稱」和「名稱空間」屬性會在結構描述的XML編輯欄位中自動更新。

預覽會自動產生包含完整組態的合併檔案：

![](assets/d_ncs_integration_navigation_preview.png)
