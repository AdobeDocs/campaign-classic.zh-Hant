---
product: campaign
title: 設定URL權限
description: 了解如何設定URL權限
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 4fd69aa28c2e9325f4738ec571a6632c42ec26b8
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 29%

---

# 設定URL權限（內部部署）{#url-permissions}

![](../../assets/v7-only.svg)

可由您的 Campaign Classic 執行個體的 JavaScript 程式碼 (工作流程等等) 呼叫之預設 URL 清單有限。這些是可讓您的執行個體正常運作的 URL。

依預設，執行個體不得連線到外部 URL。不過，您可以將一些外部URL新增至授權URL清單，這樣您的執行個體就能連線到這些URL。 這可讓您將 Campaign 執行個體連結到外部系統，例如 SFTP 伺服器或網站，以啟用檔案和/或資料傳輸。

>[!NOTE]
>
>此程式僅限於 **內部部署** 部署。
>
>As a **托管** 客戶，如果您可以 [Campaign控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)，您可以使用URL權限自助服務介面。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=zh-Hant)
>
>其他 **混合/托管** 客戶需要聯絡Adobe支援團隊，將IP新增至允許清單。

針對 **混合** 和 **內部部署** 部署時，管理員需要參考 **urlPermission** 在 **serverConf.xml** 檔案。


提供三種連接保護模式：

* **封鎖**:所有不屬於允許清單的URL都會遭到封鎖，並顯示錯誤訊息。 這是升級後的預設模式。
* **許可**:允許屬於允許清單的所有URL。
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
>依預設，新實施會使用 **封鎖** 模式。
>
>身為來自移轉的現有客戶，您可以暫時使用 **警告** 模式。 先分析傳出流量再允許URL。 定義允許的URL清單後，您可以將URL新增至允許清單並啟用 **封鎖** 模式。

如需詳細資訊，請參閱下列章節：

* [控制面板文件](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [託管模型](hosting-models.md)
* [Campaign 伺服器設定](configuring-campaign-server.md)
* [Campaign伺服器設定檔案參數](the-server-configuration-file.md)
* [安全性與隱私權檢查清單](get-started-security-privacy.md)
