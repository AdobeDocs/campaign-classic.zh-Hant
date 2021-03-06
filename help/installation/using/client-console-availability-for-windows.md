---
product: campaign
title: Windows 用戶端控制台的可用性
description: Windows 用戶端控制台的可用性
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---

# Windows 用戶端控制台的可用性{#client-console-availability-for-windows}

![](../../assets/v7-only.svg)

Adobe Campaign使用者若想登入您建立和設定的執行個體，必須使用用戶端主控台。

## 讓用戶端主控台可供使用

用來啟動Adobe Campaign應用程式伺服器的電腦(**nlserver web**)從用戶端主控台接收使用者連線，您可以加以設定，讓Adobe Campaign rich client的設定程式可透過HTML介面使用。 每當有新版本的用戶端主控台可用時，就會邀請使用者在啟動其用戶端主控台時下載。

要執行此操作，您必須：

1. 選擇包含控制台安裝程式的包。

   此檔案稱為 `setup-client-7.X.XXXX.exe` 適用於v7或 `setup-client-6.X.XXXX.exe` 針對v6.1，其中 `X` 是Adobe Campaign和 `XXXX` 是組建編號。

1. 將此套件複製並貼到Adobe Campaign安裝資料夾（位於混合式安裝的行銷伺服器上）下方的 **/datakit/nl/eng/jsp**.
1. 啟動Adobe Campaign伺服器。

然後，由於下列URL,Campaign使用者可透過網頁瀏覽器下載主控台安裝程式：

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此頁面需要應用程式中定義的登錄名和密碼。

了解如何安裝主控台 [在本節](../../installation/using/installing-the-client-console.md).

## 建議最終用戶升級其客戶端控制台

一旦主控台可在Campaign伺服器資料夾中使用，系統就會邀請使用者在專用的提示視窗中下載最新的用戶端主控台版本。 Adobe建議保留選項 **[!UICONTROL No longer ask this question]** 未選取，以確保當有新版本的控制台可用時，所有使用者都會收到警報。

如果您選取此選項並選擇不下載最新版本，系統就不會通知其他使用者有新的可用版本。

如果選取了選項，您可以重設此提示。 只有熟悉編輯Windows註冊表的系統管理員才應進行以下更改：

1. 使用開啟註冊表編輯器 **regedit** 命令 **[!UICONTROL Start > Run]** 功能表。
1. 搜尋節點並展開它。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除 **confDescuredUpgrade** 登入並關閉註冊表編輯器。
