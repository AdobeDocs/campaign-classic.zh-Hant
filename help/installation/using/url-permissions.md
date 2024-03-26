---
product: campaign
title: 設定URL許可權
description: 瞭解如何設定URL許可權
feature: Installation, Instance Settings, Permissions
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 25%

---

# 設定URL許可權（內部部署）{#url-permissions}



可由您的 Campaign Classic 執行個體的 JavaScript 程式碼 (工作流程等等) 呼叫之預設 URL 清單有限。這些是可讓您的執行個體正常運作的 URL。

依預設，執行個體不得連線到外部 URL。不過，您可以將一些外部URL新增至授權URL清單，以便您的執行個體可以連結到這些URL。 這可讓您將 Campaign 執行個體連結到外部系統，例如 SFTP 伺服器或網站，以啟用檔案和/或資料傳輸。

>[!NOTE]
>
>此程式僅限於 **內部部署** 部署。
>
>作為 **託管** 客戶，如果您可存取 [Campaign控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)，您可以使用URL許可權自助服務介面。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=zh-Hant)
>
>其他 **混合/託管** 客戶需要聯絡Adobe支援團隊，將IP新增至允許清單。
>

的 **混合式** 和 **內部部署** 部署，管理員需要參考新的 **urlPermission** 在 **serverConf.xml** 檔案。


有三種連線保護模式可供使用：

* **封鎖**：所有不屬於允許清單的URL都會遭到封鎖，並顯示錯誤訊息。 這是升級後使用的預設模式。
* **許可**：允許所有不屬於允許清單的URL。
* **警告**：允許所有不屬於允許清單的URL，但JS解譯器會發出警告，讓管理員可以收集。 此模式會新增JST-310027警告訊息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>根據預設，新的實作會使用 **封鎖** 模式。
>
>作為來自移轉的現有客戶，您可以暫時使用 **警告** 模式。 在允許URL之前分析傳出流量。 一旦定義了允許的URL清單，您就可以將URL新增到允許清單並啟動 **封鎖** 模式。

如需詳細資訊，請參閱下列章節：

* [控制面板文件](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)
* [託管模型](hosting-models.md)
* [Campaign 伺服器設定](configuring-campaign-server.md)
* [Campaign伺服器設定檔案引數](the-server-configuration-file.md)
* [安全性與隱私權檢查清單](get-started-security-privacy.md)
