---
product: campaign
title: 託管模型
description: 探索行銷活動託管模型
feature: Installation, Architecture, Deployment
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 2%

---

# 託管模型{#hosting-models}



Adobe Campaign提供三種託管模式供您選擇，讓您靈活且自由地選擇最佳模式，或選擇符合業務需求的模式。

>[!NOTE]
>
>對於Adobe託管環境，主要安裝和設定步驟只能由Adobe執行，例如設定伺服器和自訂執行個體設定檔案。 若要進一步瞭解部署模式之間的主要差異，請參閱 [此頁面](../../installation/using/capability-matrix.md).

## Managed Services /託管

Adobe Campaign可as a Managed Service部署：Adobe Campaign的所有元件（包括使用者介面、執行管理引擎和客戶的Campaign資料庫）都完全由Adobe託管，包括電子郵件執行、映象頁面、追蹤伺服器以及對外的Web元件（例如取消訂閱頁面/偏好設定中心和登陸頁面）。

![](assets/deployment_hosted.png)

作為託管客戶，大部分安裝和設定步驟都由Adobe執行。 您可以存取下列章節，自訂您的實作：

* 為每個品牌設定追蹤和映象頁面URL。 如需異動訊息，請參閱 [至本節](../../message-center/using/additional-configurations.md#configuring-multibranding).
* 安裝使用者端主控台：請參閱 [至本節](../../installation/using/installing-the-client-console.md).
* 閱讀以下內容，進一步瞭解傳遞能力工具和最佳實務 [詳細檔案](../../delivery/using/about-deliverability.md).
* 設定Campaign選項：請參閱 [至本節](../../installation/using/configuring-campaign-options.md).
* 設定CRM聯結器：請參閱 [至本節](../../platform/using/crm-connectors.md).

## 內部部署

Adobe Campaign可部署於內部部署：Adobe Campaign的所有元件（包括使用者介面、執行管理引擎和資料庫）都位於客戶資料中心的網站上。 在此部署模式中，客戶會管理所有軟體和硬體更新與升級，而專屬的資料庫管理員需要執行維護和最佳化工作，以確保Campaign執行個體管理。

![](assets/deployment_onpremise.png)

作為內部部署客戶，在開始部署Campaign Classic之前，請注意下列必要條件和建議：

* 閱讀 [相容性矩陣](../../rn/using/compatibility-matrix.md) 列出Adobe Campaign支援的所有系統和元件版本。
* 根據您的環境，閱讀 [Windows的必要條件](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) 和 [Linux的必要條件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* 瞭解與資料庫引擎相關的建議 [在本節中](../../installation/using/database.md).
* 檢查伺服器上是否已安裝必要的資料庫存取層，以及是否可從Adobe Campaign帳戶存取。 [了解更多](../../installation/using/application-server.md)。
* 根據某些程式需要與其他程式通訊或存取區域網路和網際網路來設定您的網路。 這表示有些TCP連線埠需要為這些處理序開啟。 [瞭解更多](../../installation/using/network-configuration.md) 關於網路組態需求。
* 讀出 [Campaign安全性與隱私權檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html).
* 檢視評估內部部署硬體需求的一般准則 [本文章](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html).

## 混合式

以混合模式部署時，Adobe Campaign解決方案軟體會常駐於客戶網站上，並以Adobe雲端服務的形式提供執行管理。 Adobe Campaign行銷執行個體安裝在客戶的防火牆內，因此個人識別資訊(PII)仍保留在內部結構，而且只有個人化電子郵件所需的資料才會傳送至雲端以執行電子郵件。 由雲端託管的執行執行個體會接收來自內部部署執行個體的請求，以傳遞電子郵件。 此執行個體會將所有電子郵件個人化並傳送。 雲端中不會永久儲存任何型別的資料。

![](assets/deployment_hybrid.png)

作為混合型客戶，大部分的安裝和設定步驟都由Adobe執行。 您可以存取下列章節，自訂您的實作：

* 設定異動訊息：請參閱 [至本節](../../message-center/using/transactional-messaging-architecture.md).
* 為每個品牌設定追蹤和映象頁面URL。 如需異動訊息，請參閱 [至本節](../../message-center/using/additional-configurations.md#configuring-multibranding).
* 安裝使用者端主控台：請參閱 [至本節](../../installation/using/installing-the-client-console.md).
* 安裝內建套件：請參閱 [至本節](../../installation/using/installing-campaign-standard-packages.md).
* 傳遞能力：設定 [MX規則](../../installation/using/email-deliverability.md#mx-configuration) 和 [電子郵件格式](../../installation/using/email-deliverability.md#managing-email-formats). 閱讀以下內容，進一步瞭解傳遞能力工具和最佳實務 [詳細檔案](../../delivery/using/about-deliverability.md).
* 設定Campaign選項：請參閱 [至本節](../../installation/using/configuring-campaign-options.md).
* 設定外部資料庫（同盟資料存取）：請參閱 [至本節](../../installation/using/about-fda.md).
* 設定CRM聯結器：請參閱 [至本節](../../platform/using/crm-connectors.md).
* 要瞭解更多關於中間來源部署原則，請參閱 [至本節](../../installation/using/mid-sourcing-deployment.md).
