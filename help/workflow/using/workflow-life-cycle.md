---
product: campaign
title: 工作流程生命週期
description: 進一步瞭解工作流程的生命週期
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: fceb5752-dc73-4386-8c18-c4f3e6110ca5
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---

# 工作流程生命週期 {#workflow-life-cycle}



工作流程週期有三個主要步驟。

* **正在編輯**

   這是初始設計階段：建立新工作流程時，其狀態為「正在編輯」。 此工作流程尚未由伺服器處理，且可以修改而不會有風險。

* **已開始**

   完成初始設計階段後，即可開始工作流程。 在此階段中，執行個體由伺服器處理，而個別工作則會執行。 仍可按照某些預防措施來修改工作流程。

* **已完成**

   當沒有任何正在進行的任務或運運算元已明確停止執行個體時，工作流程為「已完成」。

例如， **開始** 和 **傳遞** 活動概述，而 **核准** 活動會在下方的工作流程中閃爍。

![](assets/new-workflow-6.png)

這表示前兩個活動已成功執行，且核准進行中，即已建立但尚未完成。

字元 **574 — 確定** 顯示在轉變上方，緊接在 **傳遞** 活動表示傳遞準備已鎖定目標574位收件者，且作業已成功完成。 此資訊在執行時新增至轉變，由處理資料的活動計算。

工作流程已啟動，且正在等候屬於中指定的群組的運運算元。 **核准** 進行決策的活動。 屬於群組且擁有電子郵件地址或行動電話號碼的運營商會收到通知。

操作員管理在此詳細說明 [區段](../../platform/using/access-management.md).

如需如何監視工作流程的詳細資訊，請參閱 [本節](monitoring-workflow-execution.md).
