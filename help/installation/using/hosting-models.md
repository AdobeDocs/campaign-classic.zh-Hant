---
solution: Campaign Classic
product: campaign
title: 託管模型
description: Discover Campaign代管模型
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---


# 託管模型{#hosting-models}

Adobe Campaign提供三種代管模型的選擇，提供選擇最佳模型的靈活彈性和自由，或是符合業務需求的模型。

>[!NOTE]
>
>對於Adobe代管環境，主要安裝和設定步驟只能由Adobe執行，例如設定伺服器和自訂執行個體設定檔。 若要進一步瞭解部署模式之間的主要差異，請參閱[本頁](../../installation/using/capability-matrix.md)。

* **托管服務（托管）**

   Adobe Campaign可部署為受管理服務：Adobe完全托管Adobe Campaign的所有元件，包括使用者介面、執行管理引擎和客戶的Campaign資料庫，包括電子郵件執行、鏡像頁面、追蹤伺服器，以及對外的Web元件，例如取消訂閱頁面／偏好設定中心和登陸頁面。 Adobe在雲端最多可分配三個執行個體：開發、測試／階段和生產。 此代管模型的安裝和配置步驟在本節](../../installation/using/hosted-model.md)中介紹。[

   ![](assets/deployment_hosted.png)

* **內部部署**

   Adobe Campaign可部署在內部部署：Adobe Campaign的所有元件，包括使用者介面、執行管理引擎和資料庫都駐留在客戶的資料中心。 在此部署模型中，客戶管理所有軟體和硬體更新與升級，而專屬的資料庫管理員則需要執行維護與最佳化工作，以確保Campaign執行個體管理。 本節](../../installation/using/before-starting.md)將介紹現場客戶的部署指南。[

   ![](assets/deployment_onpremise.png)

* **混合**

   當部署為混合模型時，Adobe Campaign解決方案軟體會駐留在客戶網站的內部部署，而執行管理則會以雲端服務的形式提供。 Adobe Campaign行銷實例安裝在客戶的防火牆內，因此個人識別資訊(PII)仍在內部，而且只有個人化電子郵件所需的資料才會傳送至Cloud，以執行電子郵件。 執行例項（位於Cloud中）會收到On-Premise例項的傳送電子郵件要求。 此例項會個人化所有電子郵件，並傳送這些電子郵件。 雲端不會永久儲存任何類型的資料。 此代管模型的安裝和配置步驟在本節](../../installation/using/hybrid-model.md)中介紹。[

   ![](assets/deployment_hybrid.png)

