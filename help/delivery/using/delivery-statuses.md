---
product: campaign
title: 傳遞狀態
description: 進一步了解傳遞控制面板上可用的狀態
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring, Deliverability
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: 4b13e310fcee9ba24e83b697fca57bc494505642
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 8%

---

# 傳遞狀態 {#delivery-statuses}



<!--ajouter intro 

ajouter screenshot -->

傳送後，傳送控制面板會顯示狀態，讓您監控傳送是否成功。 可能的狀態在下節中詳細說明。

![](assets/delivery-status.png)

如需您可能遇到的不同傳送失敗的詳細資訊，以及如何解決，請參閱 [本頁](understanding-delivery-failures.md).

**相關主題：**

* [傳遞儀表板](delivery-dashboard.md)
* [傳遞疑難排解](delivery-troubleshooting.md)
* [開始使用傳遞能力](about-deliverability.md)

## 傳遞狀態清單 {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> 狀態<br /> </th> 
   <th> 定義與解決方案<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已傳送<br /> </td> 
   <td> 已正確傳送至訊息提供者（但收件者不一定會收到）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已忽略<br /> </td> 
   <td> 由於收件者的地址有錯誤，傳送未傳送給收件者。 已封鎖清單、已隔離、未提供或重複。 <br /> </td> 
  </tr> 
  <tr> 
   <td> 失敗<br /> </td> 
   <td> 例如，由於地址無效或收件匣已滿，傳送無法送達收件者。 它也可連結至個人化區塊的問題，因為當結構不符合傳送對應時，這些區塊可能會產生錯誤。 請參閱 <a href="understanding-delivery-failures.md" target="_blank">了解傳送故障</a><br /> </td> 
  </tr>
  <tr> 
   <td> 待處理<br /> </td> 
   <td> 傳遞已準備好傳送，且將由傳遞伺服器(MTA)處理。 請參閱 <a href="#pending-status" target="_blank">待定狀態</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 不適用<br /> </td> 
   <td> 伺服器(MTA)已考慮傳送，但未處理。<br /> </td> 
  </tr>  
  <tr> 
   <td> 傳遞已取消<br /> </td> 
   <td> 操作員已取消傳送。<br /> </td> 
  </tr> 
  <tr> 
   <td> 服務提供者已將其列入考量<br /> </td> 
   <td> SMS服務提供者收到了傳送。<br /> 若為托管或混合安裝，若您已升級至 <a href="sending-with-enhanced-mta.md" target="_blank">增強的MTA</a>，訊息已成功從Campaign中繼至Enhanced MTA。</td> 
  </tr> 
  <tr> 
   <td> 已在行動裝置上收到<br /> </td> 
   <td> 收件者在行動裝置上收到簡訊。<br /> </td> 
  </tr>
  <tr> 
   <td> 已傳送給服務提供者<br /> </td> 
   <td> 傳送已傳送至簡訊服務提供者，但尚未收到。<br />
   </td> 
  </tr> 
  <tr> 
   <td> 已準備<br /> </td> 
   <td> 中間狀態僅用於外部連接器，例如行動通道。 它會依「擱置中」狀態，是將決定下列狀態的外部連接器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

若要了解如何最佳化Adobe Campaign電子郵件的傳遞能力，請參閱 [本節](about-deliverability.md). 如需有關傳遞能力的更深入探討，請參閱 [Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant).

## 待定狀態 {#pending-status}

確認傳送後，您會看到傳送的狀態為 **[!UICONTROL Pending]**. 此狀態表示執行程式正在等待某些資源的可用性。

此 **[!UICONTROL Pending]** 狀態可以先表示您的傳送已排程，且在指定日期前一直擱置。 有關詳細資訊，請參閱 [傳送排程](steps-sending-the-delivery.md#scheduling-the-delivery-sending) 區段。

如果您的傳送未傳送，其狀態仍會維持 **[!UICONTROL Pending]**，可能是下列結果：

* 在傳送伺服器上執行模組和程式並管理電子郵件傳送的MTA(Message Transfer Agent)可能尚未啟動，或者可能需要重新啟動。

   若要檢查此項並視需要啟動模組，請套用下列步驟：

   >[!NOTE]
   >
   >此操作可以使用 **內部部署** 或 **混合** 具有存取Campaign伺服器的托管模型(請參閱 [托管模型](../../installation/using/hosting-models.md))。

   1. 檢查 `mta@<instance>` 模組會在您的MTA伺服器上啟動。

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<instance-name> (9268) - 23.0 Mb
      [...]
      ```

   1. 如果未列出MTA，請使用下列命令啟動：

      ```
      nlserver start mta@<instance-name>
      ```

      >[!NOTE]
      >
      >取代 `<instance-name>` 以及執行個體的名稱（生產、開發等）。 執行個體名稱是透過設定檔案識別： `[path of application]nl6/conf/config-<instance-name>.xml`

* 傳送可能使用未在傳送伺服器上設定的相似性。

   在此情況下，請檢查流量管理（IP相關性）的設定，並使用 **[!UICONTROL Managing affinities with IP addresses]** 欄位，將傳遞連結至管理相關性的MTA。 如需相關性的詳細資訊，請參閱 [本節](../../installation/using/configure-delivery-settings.md).

* 當執行太多促銷活動時，傳送狀態仍為「擱置中」狀態。

   同時進行的促銷活動限制定義於 **[!UICONTROL NmsOperation_LimitConcurrency]** 選項。 預設值為 10。

   進一步了解 [本頁](../../installation/using/configuring-campaign-options.md).


**相關主題：**

* [傳送記錄檔和歷史記錄](#delivery-logs-and-history)
* [瞭解傳遞故障](understanding-delivery-failures.md)
* [傳送失敗類型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
