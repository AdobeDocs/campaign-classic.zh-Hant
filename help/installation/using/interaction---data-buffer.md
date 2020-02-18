---
title: 互動——資料緩衝
seo-title: 互動——資料緩衝
description: 互動——資料緩衝
seo-description: null
page-status-flag: never-activated
uuid: 4cb742b5-6bde-43e8-b26b-16f27dd65f72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: cbfdeb2f-4f20-45b8-8cc0-89362f9ea9c1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6b631f8456ad1f61cec1630334d76752f6af9866

---


# 互動——資料緩衝{#interaction-data-buffer}

>[!NOTE]
>
>有些組態只能由Adobe針對Adobe代管的部署執行。 例如，訪問伺服器和實例配置檔案。 若要進一步瞭解不同的部署，請參閱「代 [管模型](../../installation/using/hosting-models.md) 」一節或 [本文章](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)。

在Adobe Campaign中，「互 **動」模組中已引入資料緩衝區** 。 這可讓您取消 **同步庫存** 和選件計算，以提高傳入互動的效能。

它只涉及傳入的互動，不論是呼叫（有無呼叫資料）或狀態更新(updateStatus)。

為避免在寫入與接收方相關的提案時出現隊列，新進程生成允許 **以非同步方式寫入提案的** 資料緩 **衝區**。 此資料緩衝區會定期讀取和清空。 預設時段約為1秒。因此，建議書寫是分組的。

可在實 **例的配置檔案** (config-Instance.xml)中完成資料緩衝區配置。

>[!NOTE]
>
>對設定所做的任何變更都需要重新啟動Web伺服器(Apache:IIS)和Adobe Campaign程式。\
>在配置資料緩衝區後，請確保有適合的硬體配置可用。 （記憶體量）。

在配置資料緩衝區後，請確保有適合的硬體配置可用。 （記憶體量）。

寫入守護程式的定義(進程名為：)，如下所示：

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

如果您使用「傳入互動」,@autostart屬性必須為&quot;true&quot;，才能在Adobe Campaign伺服器啟動時自動啟動程式。

引數詳細資料：

```
 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 
```

