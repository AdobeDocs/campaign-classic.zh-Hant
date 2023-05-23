---
product: campaign
title: 配置URL權限
description: 瞭解如何配置URL權限
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 29%

---

# 配置URL權限（內部）{#url-permissions}



可由您的 Campaign Classic 執行個體的 JavaScript 程式碼 (工作流程等等) 呼叫之預設 URL 清單有限。這些是可讓您的執行個體正常運作的 URL。

依預設，執行個體不得連線到外部 URL。但是，可以將一些外部URL添加到授權URL清單中，以便實例可以連接到它們。 這可讓您將 Campaign 執行個體連結到外部系統，例如 SFTP 伺服器或網站，以啟用檔案和/或資料傳輸。

>[!NOTE]
>
>此過程僅限於 **現場** 部署。
>
>作為 **托管** 客戶，如果您 [市場活動控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)，可以使用URL權限自助服務介面。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=zh-Hant)
>
>其他 **混合/托管** 客戶需要聯繫Adobe支援團隊以將IP添加到允許清單中。

對於 **混合** 和 **內部部署** 部署，管理員需要引用新 **url權限** 的 **serverConf.xml** 的子菜單。


有三種連接保護模式：

* **阻塞**:所有不屬於允許清單的URL都被阻止，並顯示錯誤消息。 這是postupgrade後的預設模式。
* **許可**:允許所有不屬於允許清單的URL。
* **警告**:允許所有不屬於允許清單的URL，但JS解釋器會發出警告，以便管理員可以收集這些URL。 此模式添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>預設情況下，新實現使用 **阻塞** 的子菜單。
>
>作為遷移中的現有客戶，您可以臨時使用 **警告** 的子菜單。 在允許URL之前分析出站通信量。 定義了允許的URL清單後，可以將URL添加到允許清單並激活 **阻塞** 的子菜單。

有關詳細資訊，請參閱以下各節：

* [控制面板文件](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)
* [託管模型](hosting-models.md)
* [Campaign 伺服器設定](configuring-campaign-server.md)
* [市場活動伺服器配置檔案參數](the-server-configuration-file.md)
* [安全和隱私檢查表](get-started-security-privacy.md)
