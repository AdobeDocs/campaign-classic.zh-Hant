---
solution: Campaign Classic
product: campaign
title: 適用於 Windows 的用戶端主控台可用性
description: 適用於 Windows 的用戶端主控台可用性
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 5%

---


# 適用於 Windows 的用戶端主控台可用性{#client-console-availability-for-windows}

Adobe Campaign使用者若要能夠登入您所建立和設定的例項，就必須使用用戶端主控台。

當用來啟動Adobe Campaign應用程式伺服器(**nlserver web**)的電腦從用戶端主控台接收使用者連線時，您可以設定它，讓Adobe Campaignrich client的設定程式透過HTML介面提供。

若要這麼做，您必須：

1. 恢復包含控制台安裝程式的軟體包。

   此檔案在v7中稱為`setup-client-7.X.XXXX.exe`，在v6.1中稱為`setup-client-6.X.XXXX.exe`，其中`X`是Adobe Campaign的子版本，而`XXXX`是組建編號。

1. 將此套件複製並貼至&#x200B;**/datakit/nl/eng/jsp**&#x200B;下的Adobe Campaign安裝資料夾。
1. 啟動Adobe Campaign伺服器。

最終用戶隨後可通過Web瀏覽器下載控制台安裝程式，這要歸功於以下URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此頁面需要在應用程式中定義登入和密碼。

要下載並安裝控制台，請參閱[安裝客戶機控制台](../../installation/using/installing-the-client-console.md)。

每當有新版本的用戶端主控台可供使用時，就會邀請您下載。

>[!NOTE]
>
>在顯示的提示中，Adobe建議不要選取選項&#x200B;**[!UICONTROL No longer ask this question]**，以確保所有使用者在有新版本的主控台時收到警告。\
>如果您選取此選項並選擇不下載最新版本，則不會通知其他使用者有新的可用版本。

要重置此提示，請遵循以下步驟（只有熟悉編輯註冊表的系統管理員才應進行這些更改）:

1. 使用&#x200B;**[!UICONTROL Start > Run]**&#x200B;菜單中的&#x200B;**regedit**&#x200B;命令開啟註冊表編輯器。
1. 搜索節點並展開該節點。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除&#x200B;**confCommendedUpgrade**&#x200B;條目並關閉註冊表編輯器。

