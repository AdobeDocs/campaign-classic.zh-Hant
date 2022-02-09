---
product: campaign
title: 關於種子地址
description: 開始使用種子地址
feature: Seed Address
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 8%

---

# 關於種子地址{#about-seed-addresses}

![](../../assets/common.svg)

種子地址用於鎖定不符合所定義的目標準則的收件者。這樣，超出傳遞範圍的收件人可以接收傳遞，就像任何其他目標收件人一樣。

使用它們的一個主要原因是 **您的郵件清單保護**。 將種子地址插入郵件清單時，如果第三方正在使用它，則會留意您，因為它包含的種子地址將接收發送到您的郵件清單的遞送。

此外，種子地址 **預覽和test交付個性化和呈現** 在發送前，通過發送證據(請參閱 [將種子地址用作證明](steps-defining-the-target-population.md#using-seed-addresses-as-proof))。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](steps-defining-the-target-population.md#seeds-and-proofs-video)

種子地址功能具有以下優點：

* 使用從收件人配置檔案獲取的資料隨機替換欄位：這樣，您只能輸入電子郵件地址，例如，在種子地址部分，並允許「市場活動」自動填寫配置檔案中的其它欄位(請參閱 [用例：配置欄位替代](use-case--configuring-the-field-substitution.md))。
* 當使用具有資料管理功能的工作流時，可以在種子地址級別輸入交付中處理的附加資料以強制執行以下值：這避免了隨機值替換。
* 種子地址將自動排除在有關以下傳遞統計資訊的報告之外： **[!UICONTROL Clicks]**。 **[!UICONTROL Opens]**。 **[!UICONTROL Unsubscriptions]**。

種子地址通過導入或直接在交貨或市場活動中建立而添加到交貨目標。

>[!NOTE]
>
>種子地址不屬於收件人表，它們在單獨的表中建立。 如果用新資料擴展收件人表，則必須同時擴展種子地址表，並使用相同的資料。 否則，種子地址將不考慮這些擴展欄位。
>
>本節介紹了如何擴展種子地址表的示例： [用例：選擇標準中的種子地址](use-case--selecting-seed-addresses-on-criteria.md)。

對於直郵遞送，種子地址在提取期間被添加並混合在輸出文檔中。

>[!IMPORTANT]
>
>對於直郵遞送，抽取檔案格式必須符合以下限制：
>
>* 它不得使用 **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**。
>* 如果提取了元素集合，則這些欄位的種子地址值為空，除非 **[!UICONTROL Single row (expert user)]** 的雙曲餘切值。 如需詳細資訊，請參閱[本章節](../../platform/using/executing-export-jobs.md#step-7---data-formatting)。
>

