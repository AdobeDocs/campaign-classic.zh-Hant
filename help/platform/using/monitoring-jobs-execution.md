---
product: campaign
title: 監控工作執行
description: 瞭解如何監視匯入和匯出作業執行
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 55%

---

# 監視作業執行 {#monitoring-job-execution}



您可以直接從匯入/匯出工作清單追蹤匯入和匯出工作的執行。

![](assets/s_ncs_user_export_list_and_details.png)

* 此 **[!UICONTROL Journal]** 索引標籤可讓您檢視有關執行的記錄訊息。
* 此 **[!UICONTROL Rejects]** 索引標籤包含拒絕的記錄。 請參閱[本節](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error)。

在 **[!UICONTROL General]** 標籤， **[!UICONTROL Status]** 欄位表示工作的目前狀態。

每個狀態都由一個特殊的圖示和標籤表示。狀態及其圖示如下：

![](assets/s_ncs_user_export_status.png)

* **正在編輯**

   正在建立工作。

* **正在執行**

   這項工作正在執行。

* **取消**

   按一下 **[!UICONTROL Cancel]** 按鈕：進行中的工作已取消。

* **取消正在進行中**

   取消命令已接收並且作業正在取消。

* **暫停進行中**

   按一下 **[!UICONTROL Pause]**：工作正在暫停。

* **已暫停**

   按一下 **[!UICONTROL Pause]**：工作已暫停。 按一下「 」即可重新啟動 **[!UICONTROL Start]**.

* **已完成**

   執行作業已完成。

* **完成出現錯誤**

   由於技術錯誤，該作業未執行。

* **伺服器正在關閉**

   正在進行的作業因 Adobe Campaign 伺服器已關閉而中斷。
