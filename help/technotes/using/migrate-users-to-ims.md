---
title: 將Campaign運運算元移轉至Adobe Identity Management系統(IMS)
description: 瞭解如何將Campaign運運算元移轉至Adobe Identity Management系統(IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
TQID: 'https://experienceleague.adobe.com/drpNkA9cj7Prid--GixHMQ48CO7ZC9qqX4w5fnTiD88'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 4bc1e76d129c6a6aa15b7e3915232043bd6f4286
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 2%
---
# 將Campaign運運算元移轉至Adobe Identity Management系統(IMS) {#migrate-users-to-ims}

為了強化安全性和驗證程式，Adobe Campaign強烈建議將一般使用者驗證模式從登入/密碼原生驗證移轉至Adobe Identity Management系統(IMS)。 所有運運算元都應該實作[Adobe Identity Management System (IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}以連線至Campaign。

在[此頁面](ac-ims.md)中進一步瞭解此移轉。

## 哪些部分有所變更？ {#move-to-ims-changes}

透過Campaign Classic，所有一般使用者都已能使用其Adobe ID，透過Adobe Campaign Identity Management System (IMS)，連線至Adobe使用者端主控台。 但是，使用者/密碼連線仍然可用。 Campaign v8將不再允許此行為。

此外，為了強化安全性和驗證程式，Adobe Campaign使用者端應用程式現在直接使用IMS技術帳戶權杖呼叫Campaign API。 技術運運算元的移轉作業在專用文章中有詳細說明，可在[此頁面](ims-migration.md)取得。

此變更已適用於Campaign Classic v7，且&#x200B;**強制性**&#x200B;才能移至Campaign v8。

Adobe可協助您進行這項移轉工作。 您可在下文中找到詳細的上下文和逐步指引。

## 您有受到影響嗎？{#migrate-ims-impacts}

此程式適用於尚未使用Adobe ID連線至Campaign的所有Campaign使用者。

如果貴組織中的操作員使用其登入/密碼（亦即）連線至Campaign使用者端主控台， 原生驗證)，您會受到影響，應將這些運運算元移轉至Adobe IMS，如下所述。

移轉至[Adobe Identity Management System (IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}是安全性必要條件，可讓您的環境安全且標準化，因為其他大多數Adobe Experience Cloud解決方案和應用程式都已安裝在IMS上。

此變更適用於Campaign Classic v7.4.1 （和最新的[IMS移轉相容版本](ac-ims.md#ims-versions)）開始，且&#x200B;**必須**&#x200B;才能移至Adobe Campaign v8。

>[!IMPORTANT]
>
>**控制面板存取影響**
>
>將使用者移轉至IMS後，請注意Adobe Admin Console中名稱包含「管理員」字樣的任何產品設定檔（例如「管理員」、「管理員」、「管理員」、「核准管理員」等） 會自動授與「Campaign控制面板」的存取權。 「控制面板」是自助式工具，可讓您對Campaign執行個體進行重大變更。
>
>請仔細檢閱您的產品設定檔命名慣例，以確保只有授權使用者才能存取「控制面板」。 在[控制面板檔案](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html){target="_blank"}中進一步瞭解如何管理控制面板許可權。


## 如何移轉混合及內部部署環境？ {#ims-migration-procedure-on-prem}

以下列出此移轉的關鍵步驟：

1. 將您的環境升級至Campaign v7.4.1 （或[與IMS移轉相容的版本](#ims-versions)）。
1. 升級後，您仍然可以透過兩種方法建立新使用者，以原生使用者身分或透過IMS。
1. 您的內部Campaign管理員必須設定Adobe IMS，如[本節](../../integrations/using/configuring-ims.md)所述。
1. 然後新增唯一電子郵件至Campaign使用者端主控台上的所有原生使用者。 此步驟在[本節](https://experienceleague.adobe.com/en/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-id){target="_blank"}中詳細說明（Campaign v8檔案）。
1. 在Adobe Admin Console中建立使用者和產品設定檔，如[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}中所述。
1. 為所有運運算元啟用&#x200B;**與Adobe ID連線**&#x200B;選項。
1. 實作您連線的Adobe IMS，如[此頁面](../../integrations/using/implementing-ims.md)所詳述。

您也可以將技術操作員移轉至Adobe Developer Console，如[此技術檔案](ims-migration.md)中所述。

## 常見問題集 {#ims-migration-faq}

如需移轉相關常見問題的解答（移轉後建立使用者、為原生使用者新增電子郵件、透過IMS登入、停機時間、已使用IMS的組織、檢視操作員的驗證型別），請參閱[Campaign v8技術檔案](https://experienceleague.adobe.com/en/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-faq){target=_blank} （Campaign v8檔案）。

>[!MORELIKETHIS]
>
>* [將技術使用者移轉至Adobe Developer主控台](ims-migration.md)
>* [Adobe Campaign Classic v7發行說明](../../rn/using/latest-release.md)
>* [什麼是Adobe Identity Management System (IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}
