---
product: campaign
title: 資料結構描述中的金鑰管理
description: 瞭解資料結構中的金鑰管理
feature: Configuration, Instance Settings
role: Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
TQID: 'https://experienceleague.adobe.com/dErbfzRabMls-5x1S3eRZO94Kqcz9LRh3PaUhVD5zAU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 1%
---
# 結構描述中的金鑰管理 {#management-of-keys}

每個與資料結構描述關聯的表格必須至少有一個索引鍵來識別表格中的記錄。 本頁說明Campaign Classic v7表格中使用的自動增量索引鍵。

作為從Campaign v7轉變到v8的一部分，Campaign Classic檔案集已簡化並重新組織。 Campaign v8檔案集中現在提供常見功能。 若要深入瞭解金鑰管理，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}

## 自動增量索引鍵 {#auto-incremental-key}

大部分Adobe Campaign表格的主要索引鍵是由資料庫引擎自動產生的32位元長整數。 索引鍵值的計算取決於產生在整個資料庫中唯一數字的序列（預設為&#x200B;**XtkNewId** SQL函式）。 插入記錄時會自動輸入金鑰的內容。

增量索引鍵的優點在於，它提供不可修改的技術索引鍵用於表格之間的聯結。 此外，此索引鍵使用雙位元組整數，因此不會佔用太多記憶體。

您可以在來源結構描述中指定要與&#x200B;**pkSequence**&#x200B;屬性搭配使用的序列名稱。 如果來源結構描述中未指定此屬性，則會使用&#x200B;**XtkNewId**&#x200B;預設序列。 應用程式會針對&#x200B;**nms:broadLog**&#x200B;和&#x200B;**nms:trackingLog**&#x200B;結構描述使用專用序列（分別為&#x200B;**NmsBroadLogId**&#x200B;和&#x200B;**NmsTrackingLogId**），因為這些表格包含的記錄最多。

從ACC 18.10開始，**XtkNewId**&#x200B;不再是現成可用結構描述中順序的預設值。 您現在可以使用專用序列來建置方案或擴充現有方案。

>[!IMPORTANT]
>
>建立新結構描述或在結構描述擴充期間，您需要為整個結構描述保留相同的主要索引鍵序列值(@pkSequence)。

在Adobe Campaign結構描述中參考的序列（例如&#x200B;**NmsTrackingLogId**）必須與SQL函式相關聯，該函式會傳回引數中的識別碼數目（以逗號分隔）。 此函式必須稱為&#x200B;**GetNew** XXX **Ids**，其中&#x200B;**XXX**&#x200B;是序列的名稱（例如&#x200B;**GetNewNmsTrackingLogIds**）。 檢視&#x200B;**datakit/nms/eng/sql/**&#x200B;目錄中的應用程式所提供的&#x200B;**postgres-nms.sql**、**mssql-nms.sql**&#x200B;或&#x200B;**oracle-nms.sql**&#x200B;檔案，以復原每個資料庫引擎的&#39;NmsTrackingLogId&#39;序列建立範例。

若要宣告唯一金鑰，請在資料結構描述的主要元素上填入&#x200B;**autopk**&#x200B;屬性（值為「true」）。

**範例**：

在來源結構描述中宣告增量金鑰：

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

產生的結構描述：

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

除了索引鍵及其索引的定義外，名為「id」的數值欄位已新增至擴充架構，以包含自動產生的主要索引鍵。

>[!IMPORTANT]
>
>主鍵設為0的記錄會在建立表格時自動插入。 此記錄用於避免外部聯結，這些外部聯結在磁碟區表格上無效。 依預設，所有外部索引鍵都是以值0初始化，如此一來，當資料專案未填入時，就可以在聯結上傳回結果。


## 了解更多

瀏覽以下連結以瞭解更多資訊：

* [開始使用結構描述](about-schema-reference.md)
* [方案結構](schema-structure.md)
* [資料庫對應](database-mapping.md)
* [連結管理](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"} （Campaign v8檔案）
* [Campaign資料模型](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/developer/datamodel){target="_blank"} （Campaign v8檔案）
