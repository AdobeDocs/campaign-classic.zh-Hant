---
solution: Campaign Classic
product: campaign
title: 傳遞狀態
description: 進一步瞭解傳送控制面板上的可用狀態。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 8bf1b5b1a6763cf933d86f2af61b2bb68e870222
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 3%

---


# 傳遞狀態 {#delivery-statuses}

<!--ajouter intro 

ajouter screenshot -->

傳送傳送後，傳送控制面板會顯示狀態，讓您監視傳送是否成功。 可能的狀態將在以下章節中詳細說明。

![](assets/delivery-status.png)

有關您可能遇到的不同傳送失敗以及如何解決這些失敗的詳細資訊，請參閱[本頁](../../delivery/using/understanding-delivery-failures.md)。

**相關主題：**

* [傳遞儀表板](../../delivery/using/delivery-dashboard.md)
* [傳遞疑難排解](../../delivery/using/delivery-troubleshooting.md)
* [關於傳遞能力](../../delivery/using/about-deliverability.md)

## 傳送狀態清單{#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> 狀態<br /> </th> 
   <th> 定義和解決方案<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已發送<br /> </td> 
   <td> 傳送內容已正確傳送給訊息提供者（但收件者未必收到）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已忽略<br /> </td> 
   <td> 由於收件者的地址發生錯誤，因此未將傳送內容傳送給收件者。 它位於拒絕清單、隔離、未提供或重複。<br /> </td> 
  </tr> 
  <tr> 
   <td> 失敗<br /> </td> 
   <td> 例如，由於地址無效或收件匣已滿，傳送無法送達收件者。 它也可以連結至個人化區塊的問題，因為當結構不符合傳送對應時，這些區塊會產生錯誤。 請參閱<a href="../../delivery/using/understanding-delivery-failures.md" target="_blank">瞭解傳送失敗</a><br /> </td> 
  </tr>
  <tr> 
   <td> 擱置中<br /> </td> 
   <td> 傳送已準備好可傳送，且將由傳送伺服器(MTA)處理。 請參閱<a href="#pending-status" target="_blank">待定狀態</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不適用<br /> </td> 
   <td> 伺服器(MTA)已考慮傳送，但未處理。<br /> </td> 
  </tr>  
  <tr> 
   <td> 傳送已取消<br /> </td> 
   <td> 已由運算子取消傳送。<br /> </td> 
  </tr> 
  <tr> 
   <td> 服務提供商考慮<br /> </td> 
   <td> SMS服務提供商收到了發送。<br /> 若是代管或混合安裝，如果您已升級至 <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">Enhanced MTA</a>，則訊息會從Campaign成功中繼至Enhanced MTA。</td> 
  </tr> 
  <tr> 
   <td> 在行動裝置上收到<br /> </td> 
   <td> 收件者在其行動裝置上收到簡訊。<br /> </td> 
  </tr>
  <tr> 
   <td> 發送給服務提供商<br /> </td> 
   <td> 傳送內容已傳送至SMS服務供應商，但尚未收到。<br />
   </td> 
  </tr> 
  <tr> 
   <td> 準備<br /> </td> 
   <td> 中介狀態僅用於外部連接器，例如行動頻道。 它遵循「待定」狀態，是將確定以下狀態的外部連接器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

如要瞭解如何最佳化您的Adobe Campaign電子郵件的傳遞能力，請參閱[本節](../../delivery/using/about-deliverability.md)。 有關交付能力的深入探討，請參閱[Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html)。

## 暫掛狀態{#pending-status}

確認交貨後，您會看到交貨的狀態為&#x200B;**[!UICONTROL Pending]**。 此狀態表示執行進程正在等待某些資源的可用性。

**[!UICONTROL Pending]**&#x200B;狀態首先表示您的傳送已排程且待定至指定日期。 有關詳細資訊，請參閱[Delivery scheduling](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending)部分。

如果您的傳送未傳送，且其狀態仍為&#x200B;**[!UICONTROL Pending]**，則可能是下列結果：

* 在傳送伺服器上執行模組和程式並管理電子郵件傳送的MTA（訊息傳送代理）可能尚未啟動，或需要重新啟動。

   要檢查此問題並在必要時啟動模組，請應用以下步驟：

   >[!NOTE]
   >
   >此操作可以使用&#x200B;**on-premise**&#x200B;或&#x200B;**hybrid**&#x200B;代管模型來執行，並可存取促銷活動伺服器（請參閱[代管模型](../../installation/using/hosting-models.md)）。

   1. 檢查您的`mta@<instance>`模組是否已在MTA伺服器上啟動。

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. 如果未列出MTA，請使用下列命令啟動它：

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >將`<INSTANCENAME>`取代為例項名稱（生產、開發等）。 實例名稱通過配置檔案標識：`[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* 傳送可能使用未在傳送伺服器上設定的相似性。

   在此例中，請檢查流量管理（IP相關性）的設定，並使用&#x200B;**[!UICONTROL Managing affinities with IP addresses]**&#x200B;欄位將傳送連結至管理相關性的MTA。 有關相關性的詳細資訊，請參閱[本節](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)。

* 當執行的促銷活動過多時，傳送狀態仍會維持在「擱置中」狀態。

   同時進行促銷活動的限制在&#x200B;**[!UICONTROL NmsOperation_LimitConcurrency]**&#x200B;選項中定義。 預設值為 10。

   進一步瞭解[本頁](../../installation/using/configuring-campaign-options.md)中的選項。


**相關主題：**

* [傳送記錄檔和記錄](#delivery-logs-and-history)
* [瞭解傳送故障](../../delivery/using/understanding-delivery-failures.md)
* [傳送失敗類型和原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)
