---
product: campaign
title: 資料方案結構
description: 資料方案結構
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
TQID: 'https://experienceleague.adobe.com/bp-x2YrBY5WzNVTXJjpzdZgG45vNPPG9-z339I9U5Lw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 10%
---
# 資料方案結構{#structure-of-a-data-schema}

資料結構描述的結構會以樹狀結構的形式顯示。 若要在Adobe Campaign使用者端主控台中以圖形方式檢視它，請選取目標結構描述，然後按一下「**[!UICONTROL Structure]**」子索引標籤。

![](assets/d_ncs_integration_schema_arbo.png)

作為標準，首先顯示欄位（「進行中」、「已啟動」等） 和的字母順序。 結構化元素排在後面（郵寄地址、位置），最後是連結（電子郵件資訊、資料夾等）。

主索引鍵以紅色索引鍵識別，而外來索引鍵以黃色索引鍵識別。

根據連結是否屬於表格，以圖形方式加以區分。 從表格開始的那些專案（即表格中有外部索引鍵）會先顯示（電子郵件資訊、資料夾、國家/地區）。 「反向」集合連結（訂閱、訂單等） 都會顯示在末端。
