---
title: 關於種子地址
seo-title: 關於種子地址
description: 關於種子地址
seo-description: null
page-status-flag: never-activated
uuid: 80ab5abc-3ae0-484d-88c0-be039aac360d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: b49acfd0-b601-4694-88e3-cc0a169cb866
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3641e438784d40aa097f8c89ca19bdbb52f4bc7d

---


# 關於種子地址{#about-seed-addresses}

種子地址用於鎖定不符合所定義的目標準則的收件者。如此，超出傳送範圍的收件者就可以接收傳送，就像其他目標收件者一樣。

使用郵件的主要原因之一，就是您 **的郵件清單保護**。 將種子地址插入郵件清單中，可讓第三方在使用該種子地址時引起注意，因為其中包含的種子地址將接收發送到郵件清單的遞送。

此外，種子位址可讓您在傳送 **傳送個人化內容和轉譯之前** ，先預覽並測試傳送的個人化內容，方法是傳送校樣(請 [參閱使用種子位址做為證明](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof))。

種子地址功能具有以下優點：

* 使用從收件者描述檔擷取的資料隨機取代欄位：這可讓您僅輸入電子郵件地址，例如在種子位址區段中，並讓促銷活動自動填入描述檔中的其他欄位(請參閱使 [用案例：配置欄位替代](../../delivery/using/use-case--configuring-the-field-substitution.md))。
* 使用具有資料管理功能的工作流時，可以在種子地址級別輸入傳送中處理的附加資料，以強制執行值：這會迴避隨機值替代。
* 種子位址會自動從下列傳送統計資料的報表中排除： **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**。

種子位址會透過匯入或直接在傳送或促銷活動中建立，新增至傳送的目標。

>[!NOTE]
>
>種子地址不屬於收件人表，它們是在單獨的表中建立的。 如果用新資料擴展收件者表，則必須使用相同的資料擴展種子地址表。 否則，將不考慮種子地址的擴展欄位。
>
>本節將介紹如何擴展種子地址表的示例：使 [用案例：選擇條件中的種子地址](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

對於直接郵件傳送，在提取期間添加種子地址並在輸出文檔中混合。

>[!CAUTION]
>
>對於直接郵件傳送，解壓縮檔案格式必須符合下列限制：
>
>* 它不能使用選項 **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**。
>* 如果提取元素集合，則這些欄位的種子地址將具有空值，除非選 **[!UICONTROL Single row (expert user)]** 擇了該選項。 如需詳細資訊，請參閱[本小節](../../platform/using/exporting-data.md#step-7---data-formatting)。
>


