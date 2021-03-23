---
solution: Campaign Classic
product: campaign
title: 託管模型
description: Discover Campaign代管模型
feature: 概觀
role: 架構師
level: 初學者
translation-type: tm+mt
source-git-commit: 09bd634142f643206c38ac5f881302a5d489ecaf
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 2%

---


# 託管模型{#hosting-models}

Adobe Campaign提供三種代管模式選擇，提供選擇最佳模式的靈活彈性和自由，或者選擇符合商業需求的模式。

>[!NOTE]
>
>對於Adobe托管環境，主要安裝和配置步驟只能通過Adobe執行，如配置伺服器和自定義實例配置檔案。 若要進一步瞭解部署模式之間的主要差異，請參閱[本頁](../../installation/using/capability-matrix.md)。

## Managed Services/代管

Adobe Campaign可部署為受管理服務：Adobe Campaign的所有元件，包括使用者介面、執行管理引擎和客戶的促銷活動資料庫，都完全由Adobe托管，包括電子郵件執行、鏡像頁面、追蹤伺服器，以及對外的Web元件，例如取消訂閱頁面／偏好設定中心和登陸頁面。

![](assets/deployment_hosted.png)

身為代管客戶，大部分的安裝和設定步驟都由Adobe執行。 您可以存取下列章節來自訂您的實作：

* 依品牌設定追蹤和鏡像頁面URL。 有關事務性消息，請參閱[至本節](../../message-center/using/configuring-multibranding.md)。
* 安裝客戶機控制台：請參閱[至本節](../../installation/using/installing-the-client-console.md)。
* 閱讀[詳細說明檔案](../../delivery/using/about-deliverability.md)，進一步瞭解可傳遞性工具和最佳實務。
* 設定促銷活動選項：請參閱[至本節](../../installation/using/configuring-campaign-options.md)。
* 設定CRM連接器：請參閱[至本節](../../platform/using/crm-connectors.md)。

## 內部部署

Adobe Campaign可部署在現場：Adobe Campaign的所有元件，包括用戶介面、執行管理引擎和資料庫駐留在客戶資料中心內。 在此部署模型中，客戶管理所有軟體和硬體更新與升級，而專屬的資料庫管理員則需要執行維護與最佳化工作，以確保Campaign執行個體管理。

![](assets/deployment_onpremise.png)

身為內部部署客戶，在開始部署Campaign Classic之前，請先處理下列先決條件和建議：

* 閱讀[相容性矩陣](../../rn/using/compatibility-matrix.md)，其中列出了Adobe Campaign支援的所有系統和元件版本。
* 根據您的環境，請閱讀Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)和Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)的[先決條件。[
* 瞭解本節](../../installation/using/database.md)中與資料庫引擎[相關的建議。
* 檢查伺服器上是否安裝了所需的資料庫訪問層，並可從Adobe Campaign帳戶訪問。 [進一步瞭解](../../installation/using/application-server.md)。
* 根據某些進程需要與其他進程通信或訪問LAN和Internet時，配置您的網路。 這意味著某些TCP埠需要為這些進程開啟。 [進一步](../../installation/using/network-configuration.md) 瞭解網路組態需求。
* 閱讀[促銷活動安全性和隱私權檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)。
* 請查看本文](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html)中有關評估內部部署[硬體需求的一般准則。

## 混合

當部署為混合模型時，Adobe Campaign解決方案軟體會駐留在客戶現場，而執行管理則會以雲端服務的形式由Adobe提供。 Adobe Campaign行銷實例安裝在客戶的防火牆內，因此個人識別資訊(PII)仍在內部，而且只有個人化電子郵件所需的資料才會傳送至雲端，以執行電子郵件。 執行例項（位於Cloud中）會收到On-Premise例項的傳送電子郵件要求。 此例項會個人化所有電子郵件，並傳送這些電子郵件。 雲端不會永久儲存任何類型的資料。

![](assets/deployment_hybrid.png)

身為混合型客戶，大部分的安裝和設定步驟都由Adobe執行。 您可以存取下列章節來自訂您的實作：

* 配置事務性消息：請參閱[至本節](../../message-center/using/transactional-messaging-architecture.md)。
* 依品牌設定追蹤和鏡像頁面URL。 有關事務性消息，請參閱[至本節](../../message-center/using/configuring-multibranding.md)。
* 安裝客戶機控制台：請參閱[至本節](../../installation/using/installing-the-client-console.md)。
* 安裝內置軟體包：請參閱[至本節](../../installation/using/installing-campaign-standard-packages.md)。
* 可傳遞性：設定[MX規則](../../installation/using/email-deliverability.md#mx-configuration)和[電子郵件格式](../../installation/using/email-deliverability.md#managing-email-formats)。 閱讀[詳細說明檔案](../../delivery/using/about-deliverability.md)，進一步瞭解可傳遞性工具和最佳實務。
* 設定促銷活動選項：請參閱[至本節](../../installation/using/configuring-campaign-options.md)。
* 配置外部資料庫（同盟資料存取）:請參閱[至本節](../../installation/using/about-fda.md)。
* 設定CRM連接器：請參閱[至本節](../../platform/using/crm-connectors.md)。
* 要瞭解有關中間採購部署原則的詳細資訊，請參閱本節](../../installation/using/mid-sourcing-deployment.md)。[
