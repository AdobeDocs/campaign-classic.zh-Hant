---
title: 適用於Windows的客戶端控制台可用性
seo-title: 適用於Windows的客戶端控制台可用性
description: 適用於Windows的客戶端控制台可用性
seo-description: null
page-status-flag: never-activated
uuid: d1cbb34e-87e0-481b-a78b-3616047eb5cb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: 4fa2e8c1-33d1-4d14-941b-ca528b8ceabb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 適用於Windows的客戶端控制台可用性{#client-console-availability-for-windows}

Adobe Campaign使用者若要能夠登入您所建立和設定的例項，就必須使用用戶端主控台。

當用來啟動Adobe Campaign應用程式伺服器(**nlserver web**)的電腦從用戶端主控台接收使用者連線時，您可以設定它，讓Adobe Campaignrich client的設定程式透過HTML介面提供。

若要這麼做，您必須：

1. 恢復包含控制台安裝程式的軟體包。

   此檔案是 `setup-client-7.X.XXXX.exe` v7或v6. `setup-client-6.X.XXXX.exe` 1的呼叫，其中 `X` 是Adobe Campaign的子版本， `XXXX` 是組建編號。

1. 將此套件複製並貼至Adobe Campaign安裝資料夾，位 **於/datakit/nl/eng/jsp下**。
1. 啟動Adobe Campaign伺服器。

最終用戶可通過Web瀏覽器下載控制台安裝程式，這要歸功於以下URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此頁面需要在應用程式中定義登入和密碼。

要下載並安裝控制台，請參 [閱安裝客戶端控制台](../../installation/using/installing-the-client-console.md)。

每當有新版本的用戶端主控台可供使用時，就會邀請您下載。

>[!NOTE]
>
>在顯示的提示中，Adobe建議不要選取此選 **[!UICONTROL No longer ask this question]** 項，以確保所有使用者在有新版本的主控台時收到警告。\
>如果您選取此選項並選擇不下載最新版本，則不會通知其他使用者有新的可用版本。

要重置此提示，請遵循以下步驟（只有熟悉編輯註冊表的系統管理員才應進行這些更改）:

1. 使用菜單中的 **regedit** 命令開啟註冊表 **[!UICONTROL Start > Run]** 編輯器。
1. 搜索節點並展開該節點。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除 **confDexculdedUpgrade條目** ，並關閉註冊表編輯器。

