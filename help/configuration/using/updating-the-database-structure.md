---
product: campaign
title: 更新資料庫結構
description: 更新資料庫結構
feature: Configuration
role: Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
TQID: 'https://experienceleague.adobe.com/y4P6bZcEyVIdfI4LHMivPIRVzb1Z4sV7ewISWqk29F0'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 8%
---
# 更新資料庫結構{#updating-the-database-structure}

若要套用對結構描述所做的修改，請啟動資料庫更新小幫手（可透過&#x200B;**[!UICONTROL Tools > Advanced > Update database structure]**&#x200B;使用）。 在Campaign Classic v7中，助理也提供下列選項：

**[!UICONTROL Add stored procedures]**&#x200B;和&#x200B;**[!UICONTROL Import initialization data]**&#x200B;選項是用來啟動初始SQL指令碼以及建立資料庫時執行的資料套件。

您可以從外部資料包匯入一組資料。 若要這麼做，請選取&#x200B;**[!UICONTROL Import a package]**&#x200B;並輸入封裝的XML檔案。

作為從Campaign v7轉變到v8的一部分，Campaign Classic檔案集已簡化並重新組織。 Campaign v8檔案集中現在提供常見功能。 若要深入瞭解資料庫更新助理，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/developer/schemas-forms/update-database-structure){target=_blank}。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/developer/schemas-forms/update-database-structure){target=_blank}
