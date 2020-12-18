---
solution: Campaign Classic
product: campaign
title: 工作流程生命週期
description: 進一步瞭解工作流程的生命週期
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---


# 工作流程生命週期 {#workflow-life-cycle}

工作流程週期有三個主要步驟。

* **正在編輯**

   這是初始設計階段：建立新工作流程時，其狀態為「正在編輯」。 伺服器尚未處理工作流程，因此可以無風險地修改工作流程。

* **已開始**

   在初始設計階段完成後，就可以開始工作流程。 在此階段中，由伺服器處理實例，並執行各個任務。 工作流仍然可以用某些預防措施進行修改。

* **已完成**

   當不再進行任何工作或操作員明確停止實例時，工作流將為「完成」。

例如，**Start**&#x200B;和&#x200B;**Delivery**&#x200B;活動概述在下方的工作區中閃爍。****

![](assets/new-workflow-6.png)

這表示前兩項活動已成功執行，且正在進行核准，即已建立但尚未完成。

在&#x200B;**傳送**&#x200B;活動後的轉換上方顯示的字元&#x200B;**574 -Ok**&#x200B;表示傳送準備已鎖定574個收件者，且已成功完成作業。 執行轉場時會新增此資訊至轉場，由處理資料的活動計算。

工作流開始，並等待屬於&#x200B;**Approval**&#x200B;活動中指定的組的運算子做出決策。 會通知屬於該群組的營運商以及擁有電子郵件地址或行動電話號碼的營運商。

操作員管理在[節](../../platform/using/access-management.md)中有詳細說明。

有關如何監控工作流的詳細資訊，請參閱[本節](../../workflow/using/monitoring-workflow-execution.md)。
