---
product: campaign
title: 關於種子地址
description: 開始使用種子地址
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Seed Address
role: User
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 9%

---

# 關於種子地址{#about-seed-addresses}

種子地址用於鎖定不符合所定義的目標準則的收件者。如此一來，不在傳遞範圍的收件者可以像任何其他目標收件者一樣接收傳遞。

使用它們的主要原因之一是 **您的郵寄清單保護**. 將種子地址插入您的郵寄清單中可讓您注意到，它是否由第三方使用，因為它包含的種子地址將接收傳送至您的郵寄清單的傳遞。

此外，種子地址可讓您 **預覽和測試傳遞個人化與呈現** 在傳送前，透過傳送校樣給他們(請參閱 [使用種子地址作為證明](steps-defining-the-target-population.md#using-seed-addresses-as-proof))。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](steps-defining-the-target-population.md#seeds-and-proofs-video)

種子地址功能具有以下優點：

* 以從收件者設定檔取得的資料隨機替代欄位：例如，您可以在種子地址區段中僅輸入電子郵件地址，並讓Campaign自動填寫設定檔的其他欄位(請參閱 [使用案例：設定欄位替代](use-case--configuring-the-field-substitution.md))。
* 使用具有資料管理功能的工作流程時，可在種子地址層級輸入傳送中處理的其他資料，以強制執行值：這可作為隨機值替代的另一做法。
* 系統會自動從下列傳遞統計資料的報表中排除種子地址： **[!UICONTROL Clicks]**， **[!UICONTROL Opens]**， **[!UICONTROL Unsubscriptions]**.

種子地址會透過匯入或直接在傳遞或行銷活動中建立來新增到傳遞的目標中。

>[!NOTE]
>
>種子地址不屬於收件者表格，而是在單獨的表格中建立。 如果您使用新資料擴充收件者表格，則必須使用相同資料擴充種子地址表格。 否則，種子地址不會考慮這些擴展欄位。
>
>本節中顯示了如何擴充種子地址表格的範例： [使用案例：依條件選取種子地址](use-case--selecting-seed-addresses-on-criteria.md).

如果是直接郵件傳遞，種子地址會在提取期間新增，並在輸出檔案中進行混合。

>[!IMPORTANT]
>
>如果是直接郵件傳送，解壓縮檔案格式必須符合下列限制：
>
>* 不得使用選項 **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* 如果擷取元素集合，則這些欄位的種子地址將具有空值，除非 **[!UICONTROL Single row (expert user)]** 已選取選項。 如需詳細資訊，請參閱[本章節](../../platform/using/executing-export-jobs.md#step-7---data-formatting)。
>
