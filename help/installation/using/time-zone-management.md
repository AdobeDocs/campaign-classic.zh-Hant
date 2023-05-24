---
product: campaign
title: 時區管理
description: 時區管理
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---

# 時區管理{#time-zone-management}



## 操作原則 {#operating-principle}

Adobe Campaign可讓您將日期表示為其時區的函式：這可讓國際使用者在不同的時區在全球各地工作。 每個使用相同執行個體的國家/地區都可以管理行銷活動的執行、追蹤、封存等。 視當地時間而定。

為了能在國際規模上使用Adobe Campaign平台，系統使用的所有日期都必須可連結至時區。 因此，時區已知的日期可以匯入到任何其他時區中，或者不考慮時區。

Adobe Campaign可讓您以UTC （國際標準時間）格式儲存日期/時間。 當資料公開時，會轉換為運運算元的本機日期/時間。 當資料庫設定為UTC時，會自動執行轉換(請參閱 [設定](#configuration))。 如果資料庫未以UTC設定，則平台中日期的時區資訊會儲存在選項中。

與時區管理相關的主要平台功能包括：匯入/匯出資料、操作員及工作流程管理。 此 **繼承概念** 可用於匯入/匯出或工作流程。 預設會針對資料庫伺服器時區設定時區，但您可以為工作流程甚至單一活動重新定義新時區。

**運運算元** 可以在以下期間修改時區： **傳遞設定** 和可以指定執行傳送的特定時區。

>[!IMPORTANT]
>
>如果資料庫未管理多個時區，則對於所有資料篩選操作，必須在資料庫伺服器的時區執行SQL查詢。

每個Adobe Campaign運運算元都會連結至時區：這項資訊會在其設定檔中設定。 有關詳細資訊，請參閱 [本檔案](../../platform/using/access-management.md).

當Adobe Campaign平台不需要時區管理時，您可以使用特定的連結時區，以本機格式保留儲存模式。

## 建議 {#recommendations}

時區結合多種現實：此運算式可描述與UTC日期之間恆定的時間延遲，或是區域每年可能變更兩次的時間（日光節約時間）。

例如，在postgreSQL中， **設定&#39;歐洲/巴黎&#39;時區；** 命令會考量夏季和冬季時間：日期會根據一年中的時間以UTC+1或UTC+2表示。

不過，如果您使用 **設定時區0200；** 命令，則時間延遲將一律為UTC+2。

## 設定 {#configuration}

日期與時間的儲存模式是在建立資料庫時選取的(請參閱 [建立新執行個體](#creating-a-new-instance))。 若是移轉，與日期連結的時數會轉換為當地日期和時數(請參閱 [移轉](#migration))。

從技術角度來看，有兩種儲存方式 **日期+時間** 在資料庫中輸入資訊：

1. 時區格式的時間戳記：資料庫引擎會以UTC格式儲存日期。 每個開啟的工作階段都會有一個時區，日期會根據時區進行轉換。
1. 本機格式+本機時區：所有日期都會以本機格式儲存（無時間延遲管理），並為它們指派單一時區。 時區儲存在 **WdbcTimeZone** Adobe Campaign選項進行變更，可透過 **[!UICONTROL Administration > Platform > Options]** 樹狀結構的功能表。

>[!IMPORTANT]
>
>請注意，此修改可能會導致資料一致性和同步問題。

### 建立新執行個體 {#creating-a-new-instance}

為了讓多位國際使用者在相同例項上工作，您需要在建立例項時設定時區，以管理國家/地區之間的時差。 在建立執行個體期間，選取 **[!UICONTROL Time zone]** 資料庫組態階段的區段。

檢查 **[!UICONTROL UTC database (date fields with time zone)]** 以UTC格式儲存所有含日期和時間的資料（SQL欄位和XML欄位）的選項。

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>如果您使用 **oracle**，Oracle使用者端層的時區檔案(.dat)必須與伺服器上安裝的時區檔案相容。

如果資料庫不是UTC，您可以選取下拉式清單中提供的其中一個時區。 您也可以使用伺服器的時區，或選取UTC （國際標準時間）選項。

![](assets/install_wz_unselect_utc_option.png)

當 **[!UICONTROL UTC Database (date fields with time zone)]** 選項時，SQL欄位會以TIMESTAMP WITH TIMEZONE格式儲存。

否則，它們會以本機格式儲存，而且您必須選取要套用至資料庫的時區。

### 移轉 {#migration}

移轉至較舊版本（沒有時區管理）時，您需要在資料庫中定義日期儲存模式。

為確保與存取Adobe Campaign資料庫的外部工具相容， **日期+時間** 型別SQL欄位預設會保留為本機格式。

包含日期的XML欄位現在以UTC儲存。 在載入期間，非UTC格式的欄位會使用伺服器的時區自動轉換。 這表示所有XML欄位將逐步轉換為UTC格式。

若要使用現有例項，請新增 **WdbcTimeZone** 選項並輸入執行個體的時區。

>[!IMPORTANT]
>
>請確定已為WdbcTimeZone選項設定正確的值：稍後進行的變更可能會導致不一致。

可能值的範例：

* 歐洲/巴黎，
* 歐洲/倫敦,
* 美洲/紐約等

   這些值取自tz (Olson)資料庫。 如需詳細資訊，請參閱 [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
