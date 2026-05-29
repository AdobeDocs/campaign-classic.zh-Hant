---
product: campaign
title: 使用外部收件者表格
description: 使用外部收件者表格
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
TQID: https://experienceleague.adobe.com/Uq5yqNYkyDrFVtueUlkIOEC9XEUaYtBArNy8-t1rKAw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 91
ht-degree: 16%

---

# 使用外部收件者表格{#using-an-external-recipient-table}



如果傳送表格是外部表格，您將需要執行其他設定。 **[!UICONTROL nms:seedmember]**&#x200B;結構描述必須延伸。 種子地址會新增索引標籤，以定義適當的欄位，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

在這種情況下，若要將種子地址新增至傳遞，請直接在比對索引標籤中輸入適當的欄位，或匯入地址範本：

![](assets/s_ncs_user_seedlist_add_new_tab.png)

**nms:seedMember**&#x200B;結構描述延伸為[此區段](../../configuration/using/seed-addresses.md)。
