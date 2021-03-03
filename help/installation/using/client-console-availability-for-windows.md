---
solution: Campaign Classic
product: campaign
title: 適用於 Windows 的用戶端主控台可用性
description: 適用於 Windows 的用戶端主控台可用性
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 1b02c3870ddc01705f01ea992e734cf0810e003a
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---


# 適用於 Windows 的用戶端主控台可用性{#client-console-availability-for-windows}

為了讓Adobe Campaign用戶能夠登錄您建立和配置的實例，他們需要使用客戶機控制台。

## 使客戶端控制台可用

當用於啟動Adobe Campaign應用程式伺服器(**nlserver web**)的電腦從客戶端控制台接收用戶連接時，可以配置該電腦，使Adobe Campaign富客戶端的安裝程式通過HTML介面可用。 每當有新版本的用戶端主控台可供使用時，啟動其用戶端主控台時，都會邀請使用者下載。

若要這麼做，您必須：

1. 選擇包含控制台安裝程式的軟體包。

   此檔案在v7中稱為`setup-client-7.X.XXXX.exe`，在v6.1中稱為`setup-client-6.X.XXXX.exe`，其中`X`是Adobe Campaign的子版本，而`XXXX`是組建編號。

1. 將此套件複製並貼至&#x200B;**/datakit/nl/eng/jsp**&#x200B;下的Adobe Campaign安裝資料夾（在混合安裝的行銷伺服器上）。
1. 啟動Adobe Campaign伺服器。

促銷活動使用者接著可透過網頁瀏覽器下載主控台安裝程式，這要歸功於下列URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

此頁面需要在應用程式中定義登入和密碼。

瞭解如何在本節](../../installation/using/installing-the-client-console.md)中安裝控制台。[

## 建議使用者升級其用戶端主控台

主控台在「促銷活動伺服器」檔案夾中可用後，會邀請使用者在專用的提示視窗中下載最新的用戶端主控台版本。 Adobe建議取消選擇&#x200B;**[!UICONTROL No longer ask this question]**&#x200B;選項，以確保在控制台有新版本時所有用戶都收到警報。

如果您選取此選項並選擇不下載最新版本，則不會通知其他使用者有新的可用版本。

如果選取了該選項，則可重設此提示。 只有熟悉編輯Windows註冊表的系統管理員才應進行以下更改：

1. 使用&#x200B;**[!UICONTROL Start > Run]**&#x200B;菜單中的&#x200B;**regedit**&#x200B;命令開啟註冊表編輯器。
1. 搜索節點並展開該節點。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 刪除&#x200B;**confCommendedUpgrade**&#x200B;條目並關閉註冊表編輯器。

