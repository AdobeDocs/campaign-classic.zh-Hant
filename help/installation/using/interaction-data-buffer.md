---
product: campaign
title: 互動 — 資料緩衝
description: 互動 — 資料緩衝
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 互動 — 資料緩衝{#interaction-data-buffer}



您可以設定資料緩衝區，將優惠方案主張計算取消同步，以提高傳入互動效能。 此設定將在執行個體自己的設定檔案(config-Instance.xml)中執行。

在Adobe Campaign中，**資料緩衝區**&#x200B;已引入互動模組。 這可讓您&#x200B;**藉由取消同步化股票和優惠方案計算，提高傳入互動的效能**。

它只與傳入互動有關，無論是否透過呼叫（包含或不包含呼叫資料）或狀態更新(updateStatus)。

為了避免在寫入與收件者相關的提案時產生佇列，新處理序會產生&#x200B;**資料緩衝區**，允許非同步寫入&#x200B;**提案**。 系統會定期讀取及清空此資料緩衝區。 預設期間大約在一秒的空間內。因此，建議撰寫會歸入群組。

>[!NOTE]
>
>如果您使用與分散式架構的互動，此引數是必要的。

資料緩衝區&#x200B;**組態**&#x200B;可在執行個體的組態檔(config-Instance.xml)中完成。

>[!CAUTION]
>
>部分設定只能由Adobe代管的部署Adobe執行。 例如，存取伺服器和執行個體組態檔。 若要瞭解不同部署的詳細資訊，請參閱[託管模型](../../installation/using/hosting-models.md)區段或[此頁面](../../installation/using/capability-matrix.md)。
>
>對設定所做的任何變更都需要重新啟動網頁伺服器(Apache：IIS)和Adobe Campaign程式。\
>設定資料緩衝區之後，請確定有適合的硬體設定可用。 （存在的記憶體數量）。


設定資料緩衝區之後，請確定有適合的硬體設定可用。 （存在的記憶體數量）。

寫入精靈（名為：interaction）的定義如下：

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

如果您使用Inbound Interaction，@autostart屬性必須是「true」，Adobe Campaign伺服器啟動時才會自動啟動程式。

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
