---
title: 隱私權管理
seo-title: 隱私權管理
description: 隱私權管理
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
translation-type: tm+mt
source-git-commit: b8548e8d609ed099433b97b4c0704d27234e81c0
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 1%

---


# 隱私權管理 {#privacy-management}

Adobe Campaign提供一套工具，可協助您遵守隱私權法規（包括GDPR、CCPA、PDPA、LGPD）。

* 本節提供有關隱私權管理的一般資訊，以及Adobe Campaign為管理存取權和被遺 [忘權所提供的功能](#right-access-forgotten)。

* 此外，還包含管理隱私權(同意、資[料保留和使用者角色](#consent-retention-roles))的重要功能，以及使用Adobe Campaign時協助您符合隱私權規範的最佳實務。

## 隱私權管理法規 {#privacy-management-regulations}

Adobe Campaign的功能可協助您遵守下列法規：

* **GDPR** ([通用資料保護規則](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en))是歐盟(EU)的隱私權法，協調並現代化歐盟國家的資料保護要求。
* **CCPA** ([California Consumer Privacy Act](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5。&amp;part=4。&amp;chapter=&amp;article=))為加州居民提供個人資訊的新權利，並對在加州經營業務的特定實體規定資料保護責任。
* **PDPA** ([個人資料保護法](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/))是一項新的隱私權法，協調並現代化泰國的資料保護要求。
* **LGPD** ([Lei Geral de Proteção de Dados](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf))將於2021年初生效，適用於巴西所有收集或處理個人資料的公司。

所有這些規定皆適用於持有上述地區或國家（歐盟、加州、泰國、巴西）資料主體資料的Adobe Campaign客戶。

<!--Several Privacy capabilities are available in Adobe Campaign, including consent management, data retention settings, and rights management. See [Consent, Retention and Roles](#consent-retention-roles). In addition to this, Adobe Campaign helps facilitate your readiness as Data Controller for certain Privacy requests. See [Right to Access and Right to be Forgotten](#right-access-forgotten).-->

>[!NOTE]
>
>如需有關個人資料以及管理資料的不同實體（資料控制者、資料處理者和資料主體）的詳細資訊，請參 [閱個人資料和人員](../../platform/using/privacy-and-recommendations.md#personal-data)。

## 存取權與被遺忘權 {#right-access-forgotten}

為協助您做好隱私權準備，Adobe Campaign可讓您處理存取 **和****刪除請求** 。

* 存 **取權是** 「資料主體」有權從資料掌控者取得有關其個人資料是否正在處理、地點及用途的確認。 資料掌控者應免費提供電子格式的個人資料副本。

* 也稱為「資料擦除」的「被遺忘權 **** （刪除請求）」賦予「資料主體」權利，讓資料掌控者清除其個人資料、停止進一步散發資料，並可能讓第三方停止處理資料。

如要瞭解如何建立 **Access** 和 **Delete請求，以及Adobe Campaign如何處理這些請求，請參** 閱實作步驟 [](../../platform/using/privacy-requests.md)。

<!--Tutorials on Privacy management in Campaign Standard are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).
https://experienceleague.corp.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html?lang=en-->

## 同意、保留和角色 {#consent-retention-roles}

除了最新的存取權 **和被遺忘權** , **** Adobe Campaign還提供其他對隱私權至關重要的功能：

* [許可管理](#consent-management):偏好設定管理的訂閱功能
* [資料保留](#data-retention):所有標準日誌表上的資料保留期，可以使用工作流設定附加保留期
* [權限管理](#rights-management):指名權限管理的資料存取

### 許可管理 {#consent-management}

同意表示資料主體同意處理與資料主體相關的個人資料。 資料掌控者應負責取得該項處理的任何必要同意。 雖然Adobe Campaign可能會提供一些功能來協助客戶管理與服務相關的同意，但Adobe不負責同意。 客戶應與自己的法律部門合作，以決定自己的流程和做法，以取得任何必要的同意。

Adobe Campaign自始至終都採用有助於管理同意部分的功能。 透過訂閱管理程式，客戶可以追蹤哪些收件者已選擇訂閱類型，不論是電子報、每日或每週促銷或任何其他類型的行銷方案。

![](assets/privacy-consent-management.png)

有關「同意管理」的更多資訊，請參閱詳 [細檔案](../../delivery/using/managing-subscriptions.md)。

除了Adobe Campaign提供的「同意管理」工具外，您還可以追蹤消費者是否選擇退出個人資訊的銷售。 請參閱[本區段](../../platform/using/privacy-requests.md#sale-of-personal-information)。

### 資料保留 {#data-retention}

關於保留，Campaign中的內建記錄表有預先設定的保留期，通常將其資料儲存時間限制在六個月或更短。

以下是內置表的預設保留值。 請注意，保留設定是由Adobe技術管理員在實施期間設定的，每個實施的值可能會因客戶需求而有所不同。

* **整合追蹤**:1年
* **傳送記錄**:6個月
* **追蹤記錄**:1年
* **已刪除傳送**:1週
* **匯入拒絕**:6個月
* **訪客資料**:1個月
* **提供的建議**:1年
* **事件**:1個月
* **事件處理統計資料**:1年
* **封存事件**:1年
* **忽略的管線事件**:1個月

與刪除類似，使用標準工作流功能，可以設定任何自定義表的保留期。

請洽詢Adobe顧問或技術管理員，以進一步瞭解保留或您是否需要為自訂表格設定保留。

### 權限管理 {#rights-management}

Adobe Campaign可讓您透過不同的預先建立或自訂角色，管理指派給各種Campaign運算子的權限。

其中一項好處是，您可以管理公司內哪些人可以存取不同類型的資料。 例如，您可能有不同的行銷人員涵蓋不同的地域，而每個行銷人員只能存取其地域的資料。

同樣地，此功能也可讓您為每個使用者設定不同的功能，例如限制哪些人可以傳送傳送，或限制哪些人可以修改或匯出資料與隱私權管理更相關。

![](assets/privacy-user-management.png)

有關訪問管理的詳細資訊，請參閱詳 [細文檔](../../platform/using/access-management.md)。