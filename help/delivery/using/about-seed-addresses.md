---
product: campaign
title: 關於種子地址
description: 關於種子地址
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 9%

---

# 關於種子地址{#about-seed-addresses}

![](../../assets/common.svg)

種子地址用於鎖定不符合所定義的目標準則的收件者。這樣，超出傳遞範圍的收件者就可以收到傳遞，如同任何其他目標收件者一樣。

使用它們的主要原因之一是&#x200B;**您的郵件清單保護**。 在郵寄清單中插入種子地址可讓您在第三方使用時留意，因為其所包含的種子地址將接收發送到郵寄清單的傳送。

此外，種子地址可讓您透過傳送校樣，在傳送前&#x200B;**預覽並測試傳送個人化和呈現**（請參閱[使用種子地址作為校樣](steps-defining-the-target-population.md#using-seed-addresses-as-proof)）。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](steps-defining-the-target-population.md#seeds-and-proofs-video)

種子地址功能具有以下優點：

* 以從收件者設定檔擷取的資料隨機替代欄位：這可讓您僅輸入電子郵件地址，例如在種子地址區段中，並讓Campaign自動填入設定檔中的其他欄位(請參閱[使用案例：配置欄位替代](use-case--configuring-the-field-substitution.md))。
* 搭配資料管理功能使用工作流程時，可在種子地址層級輸入傳送中處理的其他資料，以強制執行值：這會繞過隨機值替代。
* 種子地址會自動排除在以下傳送統計資料的報表中：**[!UICONTROL Clicks]**、**[!UICONTROL Opens]**、**[!UICONTROL Unsubscriptions]**。

種子地址是透過匯入，或直接在傳遞或行銷活動中建立，而新增至傳遞的目標。

>[!NOTE]
>
>種子地址不屬於收件者表，它們將建立在單獨的表中。 如果使用新資料擴展收件者表，則必須擴展種子地址表以及使用相同資料擴展種子地址表。 否則，種子地址將不考慮這些擴展欄位。
>
>本節提供如何擴充種子地址表的範例：[使用案例：選擇條件](use-case--selecting-seed-addresses-on-criteria.md)上的種子地址

對於直接郵件傳送，種子地址會在提取期間新增，並在輸出檔案中混合。

>[!IMPORTANT]
>
>對於直接郵件傳送，解壓縮檔案格式必須符合下列限制：
>
>* 它不得使用&#x200B;**[!UICONTROL Handle groupings (GROUP BY+HAVING)]**&#x200B;選項。
>* 如果提取元素集合，則這些欄位的種子地址將具有空值，除非選擇了&#x200B;**[!UICONTROL Single row (expert user)]**&#x200B;選項。 如需詳細資訊，請參閱[本章節](../../platform/using/executing-export-jobs.md#step-7---data-formatting)。
>

