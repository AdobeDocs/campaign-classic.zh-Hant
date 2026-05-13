---
product: campaign
title: 設定URL許可權
description: 瞭解如何設定URL許可權
feature: Installation, Instance Settings, Permissions
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
TQID: https://experienceleague.adobe.com/5F4SRt978KzXMI06t3rNt3YRnYI-EWwSkQIrAd0oDq8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2:
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
  - id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 380
ht-degree: 26%

---

# 設定URL許可權（內部部署）{#url-permissions}



可由JavaScript程式碼（工作流程等）呼叫的預設URL清單 有限。 這些是可讓您的執行個體正常運作的 URL。

依預設，執行個體不得連線到外部 URL。 不過，您可以將一些外部URL新增至授權URL清單，以便您的執行個體可以連結到這些URL。 這可讓您將 Campaign 執行個體連結到外部系統，例如 SFTP 伺服器或網站，以啟用檔案和/或資料傳輸。

>[!NOTE]
>
>此程式僅限於&#x200B;**內部部署**&#x200B;部署。
>
>身為&#x200B;**託管**&#x200B;客戶，若您可存取[Campaign控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)，則可使用URL許可權自助服務介面。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=zh-Hant)
>
>其他&#x200B;**混合/託管**&#x200B;客戶需要聯絡Adobe支援團隊，將IP新增至允許清單。
>

對於&#x200B;**混合式**&#x200B;和&#x200B;**內部部署**&#x200B;部署，管理員需要在&#x200B;**serverConf.xml**&#x200B;檔案中參考新的&#x200B;**urlPermission**。


有三種連線保護模式可供使用：

* **封鎖**：所有不屬於允許清單的URL都會遭到封鎖，並出現錯誤訊息。 這是升級後使用的預設模式。
* **允許**：允許不屬於允許清單的所有URL。
* **警告**：允許所有不屬於允許清單的URL，但JS解譯器會發出警告，以便管理員可以收集這些URL。 此模式會新增JST-310027警告訊息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>依預設，新實作會使用&#x200B;**封鎖**&#x200B;模式。
>
>作為來自移轉的現有客戶，您可以暫時使用&#x200B;**警告**&#x200B;模式。 在允許URL之前分析傳出流量。 一旦定義了允許的URL清單，您就可以將URL新增到允許清單並啟動&#x200B;**封鎖**&#x200B;模式。

如需詳細資訊，請參閱下列章節：

* [控制面板檔案](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)
* [託管模型](hosting-models.md)
* [Campaign 伺服器設定](configuring-campaign-server.md)
* [Campaign伺服器設定檔案引數](the-server-configuration-file.md)
* [安全性與隱私權檢查清單](get-started-security-privacy.md)
