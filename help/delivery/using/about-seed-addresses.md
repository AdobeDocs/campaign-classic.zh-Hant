---
solution: Campaign Classic
product: campaign
title: 關於種子地址
description: 關於種子地址
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 9237e11edec4114b2bd0932e6128775f36aad27c
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 9%

---


# 關於種子地址{#about-seed-addresses}

種子地址用於鎖定不符合所定義的目標準則的收件者。如此，超出傳送範圍的收件者就可以接收傳送，就像其他目標收件者一樣。

使用它們的主要原因之一是&#x200B;**您的郵件清單保護**。 將種子地址插入郵件清單中，可讓第三方在使用該種子地址時引起注意，因為其中包含的種子地址將接收發送到郵件清單的遞送。

此外，種子位址可讓您在傳送遞送個人化和轉換&#x200B;**之前，透過傳送校樣來預覽和測試遞送內容（請參閱[使用種子位址作為證明](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof)）。**

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video)

種子地址功能具有以下優點：

* 使用從收件者描述檔擷取的資料隨機取代欄位：這可讓您僅輸入電子郵件地址，例如在種子位址區段中，並讓促銷活動自動填入描述檔中的其他欄位(請參閱[使用案例：配置欄位替代](../../delivery/using/use-case--configuring-the-field-substitution.md))。
* 使用具有資料管理功能的工作流時，可以在種子地址級別輸入傳送中處理的附加資料，以強制執行值：這會迴避隨機值替代。
* 種子位址會自動從下列傳送統計資料的報表中排除：**[!UICONTROL Clicks]**、**[!UICONTROL Opens]**、**[!UICONTROL Unsubscriptions]**。

種子位址會透過匯入或直接在傳送或促銷活動中建立，新增至傳送的目標。

>[!NOTE]
>
>種子地址不屬於收件人表，它們是在單獨的表中建立的。 如果用新資料擴展收件者表，則必須使用相同的資料擴展種子地址表。 否則，將不考慮種子地址的擴展欄位。
>
>本節將介紹如何擴展種子地址表的示例：[使用案例：選擇條件](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)的種子地址

對於直接郵件傳送，在提取期間添加種子地址並在輸出文檔中混合。

>[!IMPORTANT]
>
>對於直接郵件傳送，解壓縮檔案格式必須符合下列限制：
>
>* 它不能使用&#x200B;**[!UICONTROL Handle groupings (GROUP BY+HAVING)]**&#x200B;選項。
>* 如果提取元素集合，則這些欄位的種子地址將具有空值，除非選擇了&#x200B;**[!UICONTROL Single row (expert user)]**&#x200B;選項。 如需詳細資訊，請參閱[本章節](../../platform/using/executing-export-jobs.md#step-7---data-formatting)。

>


