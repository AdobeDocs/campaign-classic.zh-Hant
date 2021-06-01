---
product: campaign
title: 互動 – 資料緩衝
description: 互動 – 資料緩衝
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---

# 互動 – 資料緩衝{#interaction-data-buffer}

您可以設定資料緩衝區，借由取消同步選件主張計算來提高入站互動效能。 此設定將在執行個體的設定檔案(config-Instance.xml)中執行。

在Adobe Campaign中，「互動」模組已引入&#x200B;**資料緩衝區**。 這可讓您透過取消同步庫存和優惠方案計算，提高傳入互動的&#x200B;**效能**。

它只與入站互動有關，無論是透過呼叫（包含或不含呼叫資料），還是透過狀態更新(updateStatus)。

為了在寫入與收件人相關的建議時避免隊列，新的進程生成一個&#x200B;**資料緩衝區**，該緩衝區允許非同步地&#x200B;**寫入建議**。 定期讀取並清空此資料緩衝區。 預設期間約為一秒。因此，建議書編寫被分組。

>[!NOTE]
>
>如果您使用與分佈式架構的交互，此參數是必不可少的。

資料緩衝區&#x200B;**configuration**&#x200B;可在實例的配置檔案(config-Instance.xml)中完成。

>[!CAUTION]
>
>某些設定只能由Adobe執行，以供Adobe托管的部署使用。 例如，要訪問伺服器和實例配置檔案。 若要進一步了解不同部署，請參閱[托管模型](../../installation/using/hosting-models.md)區段或[此頁面](../../installation/using/capability-matrix.md)。
>
>對配置所做的任何更改都需要重新啟動Web伺服器(Apache:IIS)和Adobe Campaign進程。\
>配置資料緩衝區後，請確保有適當的硬體配置可用。 （記憶體量）。


配置資料緩衝區後，請確保有適當的硬體配置可用。 （記憶體量）。

寫入守護程式(進程名為：)如下：

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

如果您使用入站互動，@autostart屬性必須為「true」，才能在Adobe Campaign伺服器啟動時自動啟動程式。

參數詳細資訊：

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
