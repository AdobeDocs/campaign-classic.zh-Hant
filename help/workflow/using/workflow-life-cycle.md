---
title: 工作流程生命週期
description: 進一步瞭解工作流程的生命週期。
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# 工作流程生命週期 {#workflow-life-cycle}

工作流程週期有三個主要步驟。

* **正在編輯**

   這是初始設計階段： 建立新工作流程時，其狀態為「正在編輯」。 伺服器尚未處理工作流程，因此可以無風險地修改工作流程。

* **已開始**

   在初始設計階段完成後，就可以開始工作流程。 在此階段中，由伺服器處理實例，並執行各個任務。 工作流仍然可以用某些預防措施進行修改。

* **已完成**

   當不再進行任何工作或操作員明確停止實例時，工作流將為「完成」。

例如，開始和 **交付** (Start **)活動和交付(Delivery** )活動在下面 **** 的工作區閃爍。

![](assets/new-workflow-6.png)

這表示前兩項活動已成功執行，且正在進行核准，即已建立但尚未完成。

在 **Delivery** （傳送）活動後，轉場上方顯示的字元為574 -Ok **** ，表示傳送準備已鎖定574位收件者，且作業已順利完成。 執行轉場時會新增此資訊至轉場，由處理資料的活動計算。

工作流已啟動，正在等待屬於「批准」活動中指定的組的運 **算** 符做出決策。 會通知屬於該群組的營運商以及擁有電子郵件地址或行動電話號碼的營運商。

操作員管理在本節中有詳 [細說明](../../platform/using/access-management.md)。

如需如何監控工作流程的詳細資訊，請參閱 [本節](../../workflow/using/monitoring-workflow-execution.md)。
