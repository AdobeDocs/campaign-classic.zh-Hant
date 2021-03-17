---
solution: Campaign Classic
product: campaign
title: 互動 – 資料緩衝
description: 互動 – 資料緩衝
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---


# 互動 – 資料緩衝{#interaction-data-buffer}

您可以設定資料緩衝區，以取消同步化選件提案計算，以提高傳入的互動效能。 此配置將在實例自己的配置檔案(config-Instance.xml)中執行。

在Adobe Campaign，在交互模組中引入了&#x200B;**資料緩衝區**。 這可讓您取消同步庫存和選件計算，以&#x200B;**提高傳入互動的效能**。

它只涉及傳入的互動，不論是呼叫（有無呼叫資料）或狀態更新(updateStatus)。

為避免在寫入與收件者相關的提案時出現隊列，新進程生成允許以非同步方式寫入提案的&#x200B;**資料緩衝區**。 ****&#x200B;此資料緩衝區會定期讀取和清空。 預設時段約為1秒。因此，建議書寫是分組的。

>[!NOTE]
>
>如果您使用與分佈式體系結構的交互，則此參數是必要的。

資料緩衝區&#x200B;**configuration**&#x200B;可在實例的配置檔案(config-Instance.xml)中完成。

>[!CAUTION]
>
>某些配置只能通過Adobe來執行由Adobe托管的部署。 例如，訪問伺服器和實例配置檔案。 若要進一步瞭解不同的部署，請參閱[代管模型](../../installation/using/hosting-models.md)一節或[本頁](../../installation/using/capability-matrix.md)。
>
>對配置所做的任何更改都需要重新啟動Web伺服器(Apache:IIS)和Adobe Campaign進程。\
>在配置資料緩衝區後，請確保有適合的硬體配置可用。 （記憶體量）。


在配置資料緩衝區後，請確保有適合的硬體配置可用。 （記憶體量）。

寫入守護程式的定義(進程名為：)，如下所示：

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

如果您使用「入站交互」，則@autostart屬性必須為&quot;true&quot;，以在Adobe Campaign伺服器啟動時自動啟動進程。

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

