---
product: campaign
title: 在Italia Online中斷後更新退信資格
description: 了解如何在Italia Online中斷後更新退信資格
feature: Deliverability
hide: true
hidefromtow: true
source-git-commit: 3cf6ffb2b69d44b56615492dd9db8965ae3cf4e1
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 在Italia Online中斷後更新不正確的硬退信 {#update-bounce-italia}

![](../../assets/common.svg)

## 內容{#outage-context}

自1月22日（當地時間）以來，Italia Online已經發生中斷，導致數次延遲和拒絕的電子郵件。 1月26日，該服務開始以有限的容量恢復。

受影響的網域包括： **libero.it**, **virgilio.it**, **inwind.it**, **iol.it**，和 **blu.it**.

此問題發生在1/22/2023到1/26/2023之間，但大部分的錯誤隔離發生在1月26日。

進一步了解官方通訊 [此處](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}。


## 影響{#outage-impact}

如果ISP中斷，透過Campaign傳送的電子郵件無法成功傳送給其收件者：這些電子郵件會錯誤標示為退信。 這不僅影響Adobe，還影響了所有試圖將電子郵件發送到義大利線上的人。

症狀為：

* **延遲退信** 包含訊息 `452 requested action aborted: try again later` 正在觀察 — 會自動重試，且不需要任何動作。 當ISP恢復滿容量時，應會改善。

* **硬跳出數** 包含訊息 `550 <email address> recipient rejected` 已於當地時間1月26日早8點至下午2點被ISP退回，以防止發件人繼續超載其伺服器。 如Italia Online Postmaster所確認，這些並非真正的硬退信，因此我們建議取消隔離因該訊息而於2023年1月26日排除的所有電子郵件地址。

## 更新流程{#outage-update}

根據標準退信處理邏輯，Adobe Campaign會使用 **[!UICONTROL Status]** 設定 **[!UICONTROL Quarantine]**. 若要修正此問題，您需要尋找和移除這些收件者，或變更其，以更新Campaign中的隔離表格 **[!UICONTROL Status]** to **[!UICONTROL Valid]** 以便夜間清理工作流程將其移除。

若要尋找受此問題影響的收件者，或若此情況再次發生於其他ISP，請參閱指示 [在本頁](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
