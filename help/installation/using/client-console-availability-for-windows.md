---
product: campaign
title: Windows 用戶端控制台的可用性
description: Windows 用戶端控制台的可用性
feature: Installation, Upgrade
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 4%

---

# Windows 用戶端控制台的可用性{#client-console-availability-for-windows}



為了讓Adobe Campaign使用者能夠登入您已建立和設定的執行個體，他們需要使用使用者端主控台。

## 讓使用者端主控台可供使用

當用來啟動Adobe Campaign應用程式伺服器的電腦(**nlserver web**)收到來自使用者端主控台的使用者連線時，您可以將其設定為透過HTML介面提供Adobe Campaign Rich使用者端的安裝程式。 每當有新版本的使用者端主控台可供使用時，使用者就會在啟動其使用者端主控台時進行下載。

若要這麼做，您必須：

1. 選取包含主控台安裝程式的套件。

   此檔案名為`setup-client-7.X.XXXX.exe`，其中`X`是Adobe Campaign的子版本，`XXXX`是組建編號。

1. 將此套件複製並貼到&#x200B;**/datakit/nl/eng/jsp**&#x200B;底下的Adobe Campaign安裝資料夾（針對混合式安裝位於行銷伺服器上）。
1. 啟動Adobe Campaign伺服器。

Campaign使用者可透過網頁瀏覽器下載主控台安裝程式，網址如下：

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此頁面需要應用程式中定義的登入和密碼。

在本節[&#128279;](../../installation/using/installing-the-client-console.md)中瞭解如何安裝主控台。

## 建議使用者升級其使用者端主控台

在Campaign伺服器資料夾中可以使用主控台後，系統會邀請使用者在專用的提示視窗中下載最新的使用者端主控台版本。 Adobe建議取消選取選項&#x200B;**[!UICONTROL No longer ask this question]**，以確保當有新版本的主控台可用時，所有使用者都會收到警示。

如果您選取此選項並選擇不下載最新版本，則不會通知其他使用者有新的可用版本。

如果選取了選項，您可以重設此提示。 只有熟悉編輯Windows登入的系統管理員才應該進行下列變更：

1. 從&#x200B;**[!UICONTROL Start > Run]**&#x200B;功能表使用&#x200B;**regedit**&#x200B;命令開啟登入編輯程式。
1. 搜尋並展開節點。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除&#x200B;**confAdvisedUpgrade**&#x200B;專案並關閉登入編輯程式。
