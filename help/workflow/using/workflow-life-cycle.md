---
product: campaign
title: 工作流程生命週期
description: 深入了解工作流程的生命週期
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: fceb5752-dc73-4386-8c18-c4f3e6110ca5
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# 工作流程生命週期 {#workflow-life-cycle}

![](../../assets/common.svg)

工作流程週期有三個主要步驟。

* **正在編輯**

   這是初始設計階段：建立新工作流程時，其狀態為「正在編輯」。 伺服器尚未處理工作流程，可以無風險修改。

* **已開始**

   完成初始設計階段後，即可啟動工作流程。 在此階段中，執行個體由伺服器處理，且個別任務會執行。 您仍可以修改工作流程，並採取某些預防措施。

* **已完成**

   當不再進行任何任務或運算子明確停止執行個體時，工作流程為「已完成」。

例如， **開始** 和 **傳送** 活動列出時 **核准** 活動會在以下工作流程中閃爍。

![](assets/new-workflow-6.png)

這表示前兩個活動已成功執行，且正在進行核准，亦即已建立但尚未完成。

字元 **574 -Ok** 顯示於 **傳送** 活動表示傳送準備已鎖定574個收件者，且操作已成功完成。 這些資訊會在執行時新增至轉變，由處理資料的活動計算。

工作流已啟動，正在等待屬於 **核准** 決策活動。 系統會通知屬於該群組、擁有電子郵件地址或行動電話號碼的營運商。

運算子管理在此中有詳細說明 [節](../../platform/using/access-management.md).

如需如何監視工作流程的詳細資訊，請參閱 [本節](monitoring-workflow-execution.md).
