---
product: campaign
title: 分佈式架構
description: 分佈式架構
feature: Interaction, Offers, Architecture
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 083be073-aad4-4c81-aff2-77f5ef3e80db
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1014'
ht-degree: 1%

---

# 分佈式架構{#distributed-architectures}



## 原則 {#principle}

若要能夠支援擴充能力並在傳入頻道上提供全年無休的服務，您可以使用與分散式架構的互動。 此型別的架構已與Message Center搭配使用，並且由多個例項組成：

* 專用於傳出頻道並包含行銷和環境設計基礎的一個或多個控制例項
* 專用於傳入頻道的一或多個執行例項

![](assets/interaction_powerbooster_schema.png)

>[!NOTE]
>
>控制例項專用於傳入頻道，並包含目錄的線上版本。 每個執行例項都是獨立的，並且專用於一個聯絡區段（例如，每個國家/地區一個執行例項）。 優惠方案引擎呼叫必須直接在執行上執行（每個執行執行例項一個特定URL）。 由於執行個體之間的同步不是自動的，來自相同連絡人的互動必須透過相同執行個體傳送。

## 主張同步 {#proposition-synchronization}

選件同步會透過套件執行。 在執行例項上，所有目錄物件都以外部帳戶名稱為前置詞。 這表示在同一個執行例項上可以支援數個控制例項（例如開發和生產例項）。

>[!IMPORTANT]
>
>建議您使用簡短且明確的內部名稱。

選件會自動部署，然後發佈在執行和控制執行個體上。

所有線上執行個體都會停用在設計環境中刪除的選件。 在清除期間（在每個執行個體的部署精靈中指定）和滑動期間（在傳入主張的型別規則中指定）之後，所有執行個體上都會自動刪除過時的主張和優惠方案。

![](assets/interaction_powerbooster_schema2.png)

系統會為每個環境及外部帳戶建立工作流程，以進行主張同步。 同步頻率可以根據每個環境和外部帳戶進行調整。

## 限制 {#limitations}

* 如果您從匿名環境使用回溯函式至已識別的環境，則這兩個環境必須在同一個執行例項上。
* 數個執行例項之間的同步不會即時執行。 相同連絡人的互動必須傳送至相同執行個體。 控制例項必須專用於傳出頻道（非即時）。
* 行銷資料庫不會自動同步。 權重和適用性規則中使用的行銷資料在執行例項上必須重複。 此程式並非標準流程，您必須在整合期間進行開發。
* 主張同步僅由FDA連線執行。
* 如果您在相同執行個體上使用互動和訊息中心，則在這兩種情況下都將透過FDA通訊協定進行同步。

## 套件設定 {#packages-configuration}

任何直接連結至&#x200B;**互動**&#x200B;的結構描述延伸模組（選件、主張、收件者等）都必須部署在執行例項上。

Interaction套件必須安裝在所有執行個體（控制和執行）上。 另外兩個套件可供使用：一個套件將安裝在控制執行個體上，另一個將安裝在每個執行個體上。

>[!NOTE]
>
>安裝套件時，**nms：proposition**&#x200B;資料表的&#x200B;**long**&#x200B;型別欄位（例如主張ID）會變成&#x200B;**int64**&#x200B;型別欄位。 此型別的資料在[此區段](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data)中有詳細說明。

必須在每個執行個體上設定資料保留期間（透過部署精靈中的&#x200B;**[!UICONTROL Data purge]**&#x200B;視窗）。 在執行例項上，此期間必須對應於要計算的型別規則（滑動期間）和適用性規則所需的歷史深度。

在控制例項上：

1. 依執行例項建立外部帳戶：

   ![](assets/interaction_powerbooster1.png)

   * 完成標籤並新增簡短且明確的內部名稱。
   * 選取 **[!UICONTROL Execution instance]**。
   * 核取 **[!UICONTROL Enabled]** 選項。
   * 完成執行例項的連線引數。
   * 每個執行例項都必須連結至ID。 此ID是在您按一下&#x200B;**[!UICONTROL Initialize connection]**&#x200B;按鈕時指派。
   * 檢查使用的應用程式型別： **[!UICONTROL Message Center]**、**[!UICONTROL Interaction]**&#x200B;或兩者。
   * 輸入使用的FDA帳戶。 必須在執行例項上建立運運算元，且必須在相關例項的資料庫上擁有下列讀取和寫入許可權：

     ```
     grant SELECT ON nmspropositionrcp, nmsoffer, nmsofferspace, xtkoption, xtkfolder TO user;
     grant DELETE, INSERT, UPDATE ON nmspropositionrcp TO user;
     ```

   >[!NOTE]
   >
   >必須在執行例項上授權控制例項的IP位址。

1. 設定環境：

   ![](assets/interaction_powerbooster2.png)

   * 新增執行個體清單。
   * 針對每一個專案，指定同步化期間和篩選條件（例如，依國家/地區）。

     >[!NOTE]
     >
     >如果發生錯誤，您可以參閱同步工作流程並提供通知。 您可在應用程式的技術工作流程中找到這些內容。

如果基於最佳化理由，只有部分行銷資料庫在執行例項上重複，您可以指定連結至環境的受限制綱要，以允許使用者僅使用執行例項上可用的資料。 您可以使用執行個體上無法取得的資料來建立選件。 若要這麼做，您必須藉由限制傳出頻道（**[!UICONTROL Taken into account if]**&#x200B;欄位）上的此規則，在其他頻道上停用該規則。

![](assets/ita_filtering.png)

## 維護選項 {#maintenance-options}

以下是控制例項上可用的維護選項清單：

>[!IMPORTANT]
>
>這些選項只能用於特定的維護案例。

* **`NmsInteraction_LastOfferEnvSynch_<offerEnvId>_<executionInstanceId>`**：環境在指定執行個體上同步的最後日期。
* **`NmsInteraction_LastPropositionSynch_<propositionSchema>_<executionInstanceIdSource>_<executionInstanceIdTarget>`**：指定結構描述的建議從一個執行個體同步到另一個執行個體的上次日期。
* **`NmsInteraction_MapWorkflowId`**：包含所有已產生同步工作流程清單的選項。

以下選項可用於執行例項：

**NmsExecutionInstanceId**：包含執行個體識別碼的選項。

## 套件安裝 {#packages-installation}

如果您的執行個體先前沒有互動套件，則不需要移轉。 依預設，安裝套件後，主張表格將為64位元。

>[!IMPORTANT]
>
>根據您執行個體中現有主張的量，此操作可能需要一些時間。

* 如果您的執行個體只有很少的建議或沒有建議，就不需要手動修改建議表格。 修改會在安裝套件時完成。
* 如果您的執行個體有許多主張，最好在安裝控制套件並執行它們之前變更主張表結構。 我們建議在低活動期間執行查詢。

>[!NOTE]
>
>如果您在主張表中執行了特定配置，請相應地調整查詢。

### PostgreSQL {#postgresql}

方法有兩種。 第一個（使用工作表）的速度稍快。

**工作表**

```
CREATE TABLE NmsPropositionRcp_tmp AS SELECT * FROM nmspropositionrcp WHERE 0=1;
ALTER TABLE nmspropositionrcp_tmp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
INSERT INTO nmspropositionrcp_tmp SELECT * FROM nmspropositionrcp;
DROP TABLE nmspropositionrcp;
CREATE INDEX proposition_id ON NmsPropositionRcp (ipropositionid);
CREATE INDEX nmspropositionrcp_deliveryid ON NmsPropositionRcp (ideliveryid);
CREATE INDEX nmspropositionrcp_lastmodified ON NmsPropositionRcp (tslastmodified);
CREATE INDEX nmspropositionrcp_offerid ON NmsPropositionRcp (iofferid);
CREATE INDEX nmspropositionrcp_offerspaceid ON NmsPropositionRcp (iofferspaceid);
CREATE INDEX nmspropositionrcp_recipientidid ON NmsPropositionRcp (irecipientid);
ALTER TABLE nmspropositionrcp_tmp RENAME TO nmspropositionrcp;
```

**變更資料表**

```
ALTER TABLE nmspropositionrcp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
```

### Oracle {#oracle}

編輯&#x200B;**Number**&#x200B;型別的大小不會導致值或重新寫入索引。 因此，它會立即生效。

要執行的查詢如下：

```
ALTER TABLE nmspropositionrcp MODIFY (
ipropositionid NUMBER(19, 0),
iinteractionid NUMBER(19, 0)
);
```

### MSSQL {#mssql}

要執行的查詢如下：

```
SELECT * INTO NmsPropositionRcp_tmp FROM NmsPropositionRcp WHERE 1 = 0;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN ipropositionid BIGINT;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN iinteractionid BIGINT;
GO
INSERT INTO NmsPropositionRcp_tmp SELECT * FROM NmsPropositionRcp;
GO
DROP TABLE NmsPropositionRcp;
GO
sp_rename 'NmsPropositionRcp_tmp', NmsPropositionRcp
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR dWeight
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iDeliveryId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iEngineType
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iInteractionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferSpaceId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iPropositionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRank
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRecipientId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iStatus
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_deliveryId ON NmsPropositionRcp (iDeliveryId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_eventDate ON NmsPropositionRcp (tsEvent)
GO
CREATE UNIQUE NONCLUSTERED INDEX NmsPropositionRcp_id ON NmsPropositionRcp (iPropositionId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_lastModified ON NmsPropositionRcp (tsLastModified)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerId ON NmsPropositionRcp (iOfferId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerSpaceI ON NmsPropositionRcp (iOfferSpaceId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_recipientId ON NmsPropositionRcp (iRecipientId)
GO
```
