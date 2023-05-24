---
product: campaign
title: 等待
description: 進一步瞭解等待工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# 等待{#wait}



A **等待** 活動會在延遲數秒到幾個月之間的任何時間後啟動其轉變。 等待任務不會阻止執行其他任務；當此任務擱置時，工作流程可以並行執行任務。

您可以使用編輯器輸入標籤和等待時間，如以下範例所示：

![](assets/edit_wait.png)

在 **[!UICONTROL Duration]** 欄位，值可以您選擇的單位表示：（根據運運算元的地區設定）：

* 如果未指定地區設定： **s** 幾秒鐘， **m** 分鐘， **h** 若為小時， **d** 天數， **y** 數年。 在核準時，值會自動轉換為最易讀的單位。

   預設單位是日(**d**)。

* 反之，舉例來說，如果區域設定設為「Français」： **s** 幾秒鐘， **mn** 分鐘， **h** 若為小時， **j** 天數， **m** 幾個月， **a** 數年。 在核準時，值會自動轉換為最易讀的單位，如上述範例所示 **90年代** 已轉換為 **1mn 30s**.

   預設單位是日(**d**)。
