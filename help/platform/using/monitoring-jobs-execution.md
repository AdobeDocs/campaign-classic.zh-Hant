---
product: campaign
title: 監視工作執行
description: 瞭解如何監視匯入和匯出作業的執行
feature: Monitoring
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
TQID: 'https://experienceleague.adobe.com/g25R2WVJ2ULkITvhyNbvq87lxMdUNaHDJdm9rZNg-PA'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: 59d78c785d8984861fd537c2f64f82a7d2d77fbf
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 31%
---
# 監視作業執行 {#monitoring-job-execution}



您可以直接從匯入/匯出作業清單追蹤匯入和匯出作業的執行。

![](assets/s_ncs_user_export_list_and_details.png)

* **[!UICONTROL Journal]**&#x200B;索引標籤可讓您檢視有關執行的記錄訊息。
* **[!UICONTROL Rejects]**&#x200B;索引標籤包含拒絕的記錄。 請參閱[本節](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/data/import#behavior-in-the-event-of-an-error){target="_blank"} （Campaign v8檔案）。

在&#x200B;**[!UICONTROL General]**&#x200B;索引標籤中，**[!UICONTROL Status]**&#x200B;欄位表示工作的目前狀態。

每個狀態都由一個特殊的圖示和標籤表示。 狀態及其圖示如下：

![](assets/s_ncs_user_export_status.png)

* **正在編輯**

  正在建立工作。

* **執行進行中**

  這項工作正在執行。

* **取消**

  按一下&#x200B;**[!UICONTROL Cancel]**&#x200B;按鈕：正在進行的工作已取消。

* **正在取消**

  取消命令已接收並且作業正在取消。

* **暫停進行中**

  按一下&#x200B;**[!UICONTROL Pause]**：工作已暫停。

* **已暫停**

  按一下&#x200B;**[!UICONTROL Pause]**：工作已暫停。 按一下&#x200B;**[!UICONTROL Start]**&#x200B;即可重新啟動。

* **已完成**

  執行作業已完成。

* **已完成，錯誤為**

  由於技術錯誤，該作業未執行。

* **伺服器正在關閉**

  正在進行的作業因 Adobe Campaign 伺服器已關閉而中斷。
