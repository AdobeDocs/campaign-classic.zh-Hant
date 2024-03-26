---
product: campaign
title: 傳遞狀態
description: 進一步瞭解傳遞控制面板上可用的狀態
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 3%

---

# 傳遞狀態 {#delivery-statuses}



<!--ajouter intro 

ajouter screenshot -->

傳送傳送後，傳送控制面板會顯示狀態，讓您監視傳送是否成功。 可能的狀態會在下節中詳細說明。

![](assets/delivery-status.png)

有關您可以遇到的不同傳送失敗以及如何解決它們的詳細資訊，請參閱 [此頁面](understanding-delivery-failures.md).

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
   <td> 傳遞已正確傳送給訊息提供者（但收件者不一定會收到）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已忽略<br /> </td> 
   <td> 因為收件者的地址發生錯誤，所以未將傳遞傳送給收件者。 該檔案位於封鎖清單上、已隔離、未提供或重複。 <br /> </td> 
  </tr> 
  <tr> 
   <td> 已失敗<br /> </td> 
   <td> 例如，由於地址無效或收件匣已滿，傳遞無法連線至收件者。 它也可以連結到個人化區塊的問題，因為它們可能會在結構描述不符合傳遞對應時產生錯誤。 另請參閱 <a href="understanding-delivery-failures.md" target="_blank">瞭解傳送失敗</a><br /> </td> 
  </tr>
  <tr> 
   <td> 擱置中<br /> </td> 
   <td> 傳遞已準備就緒可供傳送，且將由傳遞伺服器(MTA)處理。 另請參閱 <a href="#pending-status" target="_blank">擱置狀態</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 不適用<br /> </td> 
   <td> 伺服器(MTA)已考慮傳遞，但未處理。<br /> </td> 
  </tr>  
  <tr> 
   <td> 傳遞已取消<br /> </td> 
   <td> 操作員已取消傳遞。<br /> </td> 
  </tr> 
  <tr> 
   <td> 服務提供者已將其列入考量<br /> </td> 
   <td> 簡訊服務提供者已收到傳遞。<br /> 對於託管或混合安裝，如果您已升級至 <a href="sending-with-enhanced-mta.md" target="_blank">增強的MTA</a>，則訊息已成功從Campaign轉送至Enhanced MTA。</td> 
  </tr> 
  <tr> 
   <td> 已在行動裝置上接收<br /> </td> 
   <td> 收件者在其行動裝置上收到簡訊。<br /> </td> 
  </tr>
  <tr> 
   <td> 已傳送給服務提供者<br /> </td> 
   <td> 傳遞內容已傳送給SMS服務提供者，但尚未收到。<br />
   </td> 
  </tr> 
  <tr> 
   <td> 已準備<br /> </td> 
   <td> 僅用於外部聯結器（例如行動裝置頻道）的中介狀態。 它會遵循「擱置中」狀態，且是會判斷下列狀態的外部聯結器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

若要瞭解如何最佳化Adobe Campaign電子郵件的傳遞能力，請參閱 [本節](about-deliverability.md). 如需傳送能力的更深入探討，請參閱 [Adobe傳遞性最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant).

## 擱置狀態 {#pending-status}

確認傳遞後，您會看到傳遞狀態為 **[!UICONTROL Pending]**. 此狀態表示執行程式正在等待某些資源的可用性。

此 **[!UICONTROL Pending]** 狀態可以首先表示您的傳送已排程且擱置中，直到指定日期。 有關詳細資訊，請參閱 [傳遞排程](steps-sending-the-delivery.md#scheduling-the-delivery-sending) 區段。

如果您的傳送未傳送，其狀態仍為 **[!UICONTROL Pending]**，原因可能是：

* MTA （郵件傳輸代理程式）會在傳遞伺服器上執行模組和程式，並管理電子郵件傳送，可能尚未啟動，或需要重新啟動。

  若要勾選此專案並在必要時啟動模組，請套用下列步驟：

  >[!NOTE]
  >
  >此作業可使用 **內部部署** 或 **混合式** 可存取Campaign伺服器的託管模型(請參閱 [託管模型](../../installation/using/hosting-models.md))。

   1. 檢查您的 `mta@<instance>` 模組會在MTA伺服器上啟動。

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<instance-name> (9268) - 23.0 Mb
      [...]
      ```

   1. 如果未列出MTA，請使用下列命令將其啟動：

      ```
      nlserver start mta@<instance-name>
      ```

      >[!NOTE]
      >
      >取代 `<instance-name>` 執行個體的名稱（生產、開發等）。 執行個體名稱會透過設定檔案識別： `[path of application]nl6/conf/config-<instance-name>.xml`

* 傳遞可能使用傳送伺服器上未設定的相似性。

  在此情況下，請檢查流量管理（IP相似性）的設定並使用 **[!UICONTROL Managing affinities with IP addresses]** 將傳遞連結至管理相似性之MTA的欄位。 如需相似性詳細資訊，請參閱 [本節](../../installation/using/configure-delivery-settings.md).

* 當有太多行銷活動執行時，傳送狀態仍會維持在「擱置中」狀態。

  同時行銷活動的限制定義於 **[!UICONTROL NmsOperation_LimitConcurrency]** 選項。 預設值為 10。

  進一步瞭解中的選項 [此頁面](../../installation/using/configuring-campaign-options.md).


**相關主題：**

* [傳遞記錄和歷史記錄](#delivery-logs-and-history)
* [瞭解傳遞故障](understanding-delivery-failures.md)
* [傳遞失敗型別和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
