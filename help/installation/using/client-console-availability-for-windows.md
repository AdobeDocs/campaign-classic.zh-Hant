---
product: campaign
title: Windows 用戶端控制台的可用性
description: Windows 用戶端控制台的可用性
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 4%

---

# Windows 用戶端控制台的可用性{#client-console-availability-for-windows}



為了讓Adobe Campaign使用者能夠登入您已建立和設定的執行個體，他們需要使用使用者端主控台。

## 讓使用者端主控台可供使用

用來啟動Adobe Campaign應用程式伺服器的電腦時(**nlserver web**)會從使用者端主控台接收使用者連線，您可以將其設定為可透過HTML介面使用Adobe Campaign rich client的設定程式。 每當有新版本的使用者端主控台可用時，使用者就會在啟動其使用者端主控台時下載該版本。

若要這麼做，您必須：

1. 選取包含主控台安裝程式的套件。

   此檔案名為 `setup-client-7.X.XXXX.exe`，其中 `X` 是Adobe Campaign的子版本，且 `XXXX` 是建置編號。

1. 將此套件複製並貼到Adobe Campaign安裝資料夾（針對混合安裝位在Marketing伺服器上）的下方 **/datakit/nl/eng/jsp**.
1. 啟動Adobe Campaign伺服器。

Campaign使用者可透過網頁瀏覽器下載主控台安裝程式，網址如下：

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此頁面需要應用程式中定義的登入名和密碼。

瞭解如何安裝主控台 [在本節中](../../installation/using/installing-the-client-console.md).

## 建議使用者升級其使用者端主控台

在Campaign伺服器資料夾中提供主控台後，系統會邀請使用者在專用的提示視窗中下載最新的使用者端主控台版本。 Adobe建議保留選項 **[!UICONTROL No longer ask this question]** 取消選取，以確保在可使用新版主控台時，所有使用者都會收到警報。

如果您選取此選項並選擇不下載最新版本，則不會通知其他使用者有新的可用版本。

如果選取了選項，您可以重設此提示。 只有熟悉編輯Windows登入的系統管理員才應該進行下列變更：

1. 使用開啟登入編輯器 **regedit** 命令來自 **[!UICONTROL Start > Run]** 功能表。
1. 搜尋節點並展開。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除 **confAdvisedUpgrade** 輸入並關閉登入編輯程式。
