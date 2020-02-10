---
title: 資料模式的結構
seo-title: 資料模式的結構
description: 資料模式的結構
seo-description: null
page-status-flag: never-activated
uuid: 83e3995d-fa31-4cb5-acf2-83f17329c99c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: a1a39eaa-6d6f-42c5-a36b-bd1cb3a77dcb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 資料模式的結構{#structure-of-a-data-schema}

資料模式的結構以樹結構的形式顯示。 若要在Adobe Campaign用戶端主控台中以圖形方式檢視它，請選取目標結構並按一下 **[!UICONTROL Structure]** 子標籤。

![](assets/d_ncs_integration_schema_arbo.png)

作為標準，欄位會先顯示（「活動」、「已啟動」等）按字母順序排列。 接著會出現結構元素（郵遞區號、位置），最後是連結（電子郵件資訊、資料夾等）。

主鍵由紅色鍵標識，外鍵由黃色鍵標識。

根據連結是否屬於表，以圖形方式區分連結。 首先顯示從表開始的表（即表中有外鍵）（電子郵件資訊、資料夾、國家）。 「反向」系列連結（訂閱、訂購等）的下界。
