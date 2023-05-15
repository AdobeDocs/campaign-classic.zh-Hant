---
product: campaign
title: 與Adobe Campaign和Adobe Target合作
description: 了解如何整合Adobe Campaign與Adobe Target
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# 使用Campaign與Target{#integrating-with-adobe-target}



透過Adobe Target使用Adobe Campaign來最佳化電子郵件內容。

若要最佳化您的電子郵件內容，您可以在Adobe Target中建立重新導向選件，然後使用Adobe Campaign管理電子郵件選件。 例如，您可以為男性和女性收件者顯示不同的選件。

整合會在開啟電子郵件時進行。 當客戶開啟電子郵件時，會呼叫Target並顯示內容的動態版本。 內容包含所有瀏覽器支援的靜態影像。 Target會追蹤對象或工作階段層級對選件的反應，且該資料可在Target報表中使用。 [進一步了解Adobe Target檔案](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).


>[!NOTE]
>
>整合僅支援靜態影像。 其餘內容無法個人化。

Adobe Target可使用數種資料：

* 來自Adobe Campaign資料庫的資料
* 連結至Adobe Target中訪客ID的區段（如果使用的資料不受法律限制）
* Adobe Target資料：使用者代理， IP位址，地理位置資料
