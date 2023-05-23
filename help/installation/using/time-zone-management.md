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

Adobe Campaign允許您根據其時區來表達日期：這使國際用戶能夠在不同的時區工作。 使用同一實例的每個國家/地區都可以管理市場活動、跟蹤、歸檔等的執行。 取決於當地時間。

為使Adobe Campaign平台能夠在國際範圍內使用，系統使用的所有日期必須可連結到一個時區。 因此，可以將其時區已知的日期導入任何其他時區，或者不考慮時區。

Adobe Campaign允許您以UTC（協調通用時間）格式儲存日期/時間。 當資料被公開時，它被轉換為運算子的本地日期/時間。 當以UTC配置資料庫時，將自動執行轉換(請參閱 [配置](#configuration))。 如果資料庫未以UTC配置，則有關平台中日期的時區的資訊將儲存在選項中。

有關時區管理的主要平台功能包括：導入/導出資料以及操作員和工作流管理。 的 **繼承概念** 可用於導入/導出或工作流。 預設情況下，它們是為資料庫伺服器時區配置的，但您可以為工作流甚至單個活動重新定義新時區。

**運算子** 可在 **交付配置** 並可以指定執行傳遞的特定時區。

>[!IMPORTANT]
>
>如果資料庫不管理多個時區，則對於所有資料篩選操作，必須在資料庫伺服器的時區中執行SQL查詢。

每個Adobe Campaign操作員都連結到一個時區：此資訊在其配置檔案中配置。 有關此內容的詳細資訊，請參閱 [此文檔](../../platform/using/access-management.md)。

當Adobe Campaign平台不需要時區管理時，您可以使用特定連結的時區保持本地格式的儲存模式。

## 建議 {#recommendations}

時區結合了幾個現實：表達式可以用UTC日期描述恆定的時差，或用某個區域的時間描述，該時間可以每年更改兩次（夏令時）。

例如，在postgreSQL中， **設定時區「歐洲/巴黎」；** 命令將考慮夏季和冬季的時間：日期將根據年份時間以UTC+1或UTC+2表示。

但是，如果您使用 **設定時區0200;** 命令，時差將始終為UTC+2。

## 設定 {#configuration}

在資料庫建立期間選擇日期和時間的儲存模式(請參閱 [建立新實例](#creating-a-new-instance))。 在遷移時，連結到日期的小時數將轉換為本地日期和時間(請參閱 [遷移](#migration))。

從技術角度看，儲存有兩種方法 **日期+時間** 在資料庫中鍵入資訊：

1. TIMESTAMP WITH TIMEZONE格式：資料庫引擎以UTC形式儲存日期。 每個開啟的會話都將有一個時區，並根據時區轉換日期。
1. 本地格式+本地時區：所有日期都以本地格式儲存（無時差管理），並為它們分配一個時區。 時區儲存在 **Wdbc時區** 選項，可通過 **[!UICONTROL Administration > Platform > Options]** 的子菜單。

>[!IMPORTANT]
>
>請注意，此修改可能導致資料一致性和同步問題。

### 建立新實例 {#creating-a-new-instance}

為了使多個國際用戶在同一實例上工作，您需要在建立實例時配置時區，以管理國家/地區之間的時差。 在實例建立過程中，在 **[!UICONTROL Time zone]** 資料庫配置階段的部分。

檢查 **[!UICONTROL UTC database (date fields with time zone)]** 選項，以UTC格式（SQL欄位和XML欄位）儲存所有日期和時間的資料。

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>如果您使用 **Oracle**,Oracle客戶端層的時區檔案(.dat)必須與伺服器上安裝的時區檔案相容。

如果資料庫不是UTC，則可以選擇下拉清單中提供的時區之一。 您還可以使用伺服器的時區或選擇UTC（協調通用時間）選項。

![](assets/install_wz_unselect_utc_option.png)

當 **[!UICONTROL UTC Database (date fields with time zone)]** 選項， SQL欄位以TIMESTAMP WITH TIMEZONE格式儲存。

否則，它們將以本地格式儲存，您需要選擇要應用於資料庫的時區。

### 遷移 {#migration}

遷移到早期版本（不進行時區管理）時，需要在資料庫中定義日期儲存模式。

為確保與訪問Adobe Campaign資料庫的外部工具相容， **日期+時間** 預設情況下，類型SQL欄位仍以本地格式儲存。

包含日期的XML欄位現在以UTC儲存。 在載入期間，使用伺服器的時區自動轉換非UTC格式的欄位。 這意味著所有XML欄位將逐步轉換為UTC格式。

要使用現有實例，請添加 **Wdbc時區** 選項並輸入實例的時區。

>[!IMPORTANT]
>
>請確保為WdbcTimeZone選項配置了正確的值：稍後進行的更改可能會導致不一致。

可能值的示例：

* 歐洲/巴黎，
* 歐洲/倫敦,
* 美國/紐約等

   這些值是從tz(Olson)資料庫中提取的。 有關詳細資訊，請參閱 [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)。
