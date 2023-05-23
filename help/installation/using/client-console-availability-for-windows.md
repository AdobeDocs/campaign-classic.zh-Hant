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
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---

# Windows 用戶端控制台的可用性{#client-console-availability-for-windows}



要使Adobe Campaign用戶能夠登錄到您建立和配置的實例，他們需要使用客戶端控制台。

## 使客戶端控制台可用

當電腦用於啟動Adobe Campaign應用程式伺服器(**nlserver web**)從客戶端控制台接收用戶連接，您可以將其配置為通過HTML介面使Adobe Campaign富客戶端的安裝程式可用。 只要有新版本的客戶端控制台可用，用戶在啟動其客戶端控制台時將被邀請下載。

為此，您必須：

1. 選擇包含控制台安裝程式的包。

   此檔案稱為 `setup-client-7.X.XXXX.exe` 對於v7或 `setup-client-6.X.XXXX.exe` 對於v6.1，其中 `X` 是Adobe Campaign和 `XXXX` 是內部版本號。

1. 將此包複製並貼上到Adobe Campaign安裝資料夾（在混合安裝的營銷伺服器上）中， **/datakit/nl/eng/jsp**。
1. 啟動Adobe Campaign伺服器。

市場活動用戶可以通過Web瀏覽器下載控制台安裝程式，這要歸功於以下URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此頁要求在應用程式中定義登錄名和密碼。

瞭解如何安裝控制台 [此部分](../../installation/using/installing-the-client-console.md)。

## 建議最終用戶升級其客戶端控制台

控制台在市場活動伺服器資料夾中可用後，將邀請用戶在專用的提示窗口中下載最新的客戶端控制台版本。 Adobe建議保留 **[!UICONTROL No longer ask this question]** 未選定，以確保在新版本的控制台可用時向所有用戶發出警報。

如果選擇此選項並選擇不下載最新版本，則不會向其他用戶通知新的可用版本。

如果選中了該選項，則可以重置此提示。 只有能夠編輯Windows註冊表的系統管理員才應進行以下更改：

1. 使用 **雷吉** 命令 **[!UICONTROL Start > Run]** 的子菜單。
1. 搜索節點並展開它。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除 **confAdvisedUpgrade** 並關閉註冊表編輯器。
