---
solution: Campaign Classic
product: campaign
title: 設定URL權限
description: 瞭解如何設定URL權限
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 27%

---


# 設定URL權限{#url-permissions}

可由您的 Campaign Classic 執行個體的 JavaScript 程式碼 (工作流程等等) 呼叫之預設 URL 清單有限。這些是可讓您的執行個體正常運作的 URL。

依預設，執行個體不得連線到外部 URL。不過，您可以將一些外部URL新增至授權URL的清單，讓您的例項可以連線至這些URL。 這可讓您將 Campaign 執行個體連結到外部系統，例如 SFTP 伺服器或網站，以啟用檔案和/或資料傳輸。

對於&#x200B;**Hybrid**&#x200B;和&#x200B;**內部部署**&#x200B;部署，管理員需要在&#x200B;**serverConf.xml**&#x200B;檔案中參考新的&#x200B;**urlPermission**。

提供三種連接保護模式：

* **阻止**:不屬於允許清單的所有URL都被阻止，並返回錯誤消息。這是postupgrade之後的預設模式。
* **權限**:允許所有不屬於允許清單的URL。
* **警告**:允許所有不屬於允許清單的URL，但JS解釋器會發出警告，以便管理員收集這些URL。此模式添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>預設情況下，新實現使用&#x200B;**Blocking**&#x200B;模式。
>
>作為遷移的現有客戶，您可以臨時使用&#x200B;**警告**&#x200B;模式。 在允許URL之前，先分析出站流量。 定義允許的URL清單後，可以將URL添加到allowlist並激活&#x200B;**Blocking**&#x200B;模式。

如需詳細資訊，請參閱下列章節：

* [控制面板文件](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [託管模式](hosting-models.md)
* [Campaign 伺服器設定](configuring-campaign-server.md)
* [促銷活動伺服器設定檔案參數](the-server-configuration-file.md)
* [安全性與隱私權檢查清單](get-started-security-privacy.md)