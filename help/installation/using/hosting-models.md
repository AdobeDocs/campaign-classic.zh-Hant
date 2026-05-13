---
product: campaign
title: 託管模型
description: 探索行銷活動託管模型
feature: Installation, Architecture, Deployment
role: Developer
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
TQID: https://experienceleague.adobe.com/9pZQYt2gLVR94ZWsw21JCv7CL55KDRyiqocvuS54SbM
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2: id: ac9c0a9c-8a76-4419-bd64-9c34c5782666id: fb2a841f-c522-491f-9901-a1b939d252df
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 637
ht-degree: 3%

---

# 託管模型{#hosting-models}



Adobe Campaign提供三種託管模式供您選擇，讓您靈活且自由地選擇最佳模式，或選擇符合業務需求的模式。

>[!NOTE]
>
>對於Adobe託管環境，主要安裝和設定步驟只能由Adobe執行，例如設定伺服器和自訂執行個體設定檔案。 若要進一步瞭解部署模式之間的主要差異，請參閱[此頁面](../../installation/using/capability-matrix.md)。

## Managed Services /託管

Adobe Campaign可部署as a Managed Service： Adobe Campaign的所有元件（包括使用者介面、執行管理引擎和客戶的Campaign資料庫）皆完全由Adobe託管，包括電子郵件執行、映象頁面、追蹤伺服器以及對外的Web元件（例如取消訂閱頁面/偏好設定中心和登陸頁面）。

![](assets/deployment_hosted.png)

作為託管客戶，大部分安裝和設定步驟都由Adobe執行。 您可以存取下列章節，自訂您的實作：

* 為每個品牌設定追蹤和映象頁面URL。 如需異動訊息，請參考[此章節](../../message-center/using/additional-configurations.md#configuring-multibranding)。
* 安裝使用者端主控台：請參閱[本節內容](../../installation/using/installing-the-client-console.md)。
* 閱讀[詳細檔案](../../delivery/using/about-deliverability.md)，進一步瞭解傳遞工具及最佳實務。
* 設定Campaign選項：請參閱[本節內容](../../installation/using/configuring-campaign-options.md)。
* 設定CRM聯結器：請參閱[本節內容](../../platform/using/crm-connectors.md)。

## 內部部署

Adobe Campaign可部署於內部部署：Adobe Campaign的所有元件（包括使用者介面、執行管理引擎和資料庫）都位於客戶資料中心的網站上。 在此部署模式中，客戶會管理所有軟體和硬體更新與升級，而專屬的資料庫管理員需要執行維護和最佳化工作，以確保Campaign執行個體管理。

![](assets/deployment_onpremise.png)

身為內部部署客戶，在開始部署Campaign Classic之前，請注意下列必要條件和建議：

* 閱讀[相容性矩陣](../../rn/using/compatibility-matrix.md)，其中列出Adobe Campaign支援的所有系統和元件版本。
* 根據您的環境，閱讀Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)的[必要條件和Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)的[必要條件。
* 在本節](../../installation/using/database.md)中瞭解與資料庫引擎[相關的建議。
* 檢查伺服器上是否已安裝必要的資料庫存取層，以及是否可從Adobe Campaign帳戶存取。 [了解更多資訊](../../installation/using/application-server.md)。
* 根據某些程式需要與其他程式通訊或存取區域網路和網際網路來設定您的網路。 這表示有些TCP連線埠需要為這些處理序開啟。 [進一步瞭解](../../installation/using/network-configuration.md)網路組態需求。
* 閱讀[行銷活動安全性與隱私權檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)。
* 請參閱本文](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html)中評估內部部署硬體需求[的一般准則。

## 混合式

以混合模式部署時，Adobe Campaign解決方案軟體會常駐於客戶網站上，而Adobe會以雲端服務的形式提供執行管理。 Adobe Campaign行銷執行個體安裝在客戶的防火牆內，因此個人識別資訊(PII)仍保留在內部結構，而且只有個人化電子郵件所需的資料才會傳送至雲端以執行電子郵件。 由雲端託管的執行執行個體會接收來自內部部署執行個體的請求，以傳遞電子郵件。 此執行個體會將所有電子郵件個人化並傳送。 雲端中不會永久儲存任何型別的資料。

![](assets/deployment_hybrid.png)

身為混合型客戶，大部分安裝和設定步驟是由Adobe執行。 您可以存取下列章節，自訂您的實作：

* 設定異動訊息：請參考[本節內容](../../message-center/using/transactional-messaging-architecture.md)。
* 為每個品牌設定追蹤和映象頁面URL。 如需異動訊息，請參考[此章節](../../message-center/using/additional-configurations.md#configuring-multibranding)。
* 安裝使用者端主控台：請參閱[本節內容](../../installation/using/installing-the-client-console.md)。
* 安裝內建套件：請參閱[此章節](../../installation/using/installing-campaign-standard-packages.md)。
* 傳遞能力：設定[MX規則](../../installation/using/email-deliverability.md#mx-configuration)和[電子郵件格式](../../installation/using/email-deliverability.md#managing-email-formats)。 閱讀[詳細檔案](../../delivery/using/about-deliverability.md)，進一步瞭解傳遞工具及最佳實務。
* 設定Campaign選項：請參閱[本節內容](../../installation/using/configuring-campaign-options.md)。
* 設定外部資料庫（同盟資料存取）：請參考[此章節](../../installation/using/about-fda.md)。
* 正在設定CRM聯結器：請參閱[此章節](../../platform/using/crm-connectors.md)。
* 若要深入瞭解中間來源部署原則，請參閱本節](../../installation/using/mid-sourcing-deployment.md)中的[。
