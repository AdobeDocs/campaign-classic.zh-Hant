---
product: campaign
title: 傳遞狀態
description: 瞭解有關交貨控制面板上可用狀態的詳細資訊
feature: Monitoring, Deliverability
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 5%

---

# 傳遞狀態 {#delivery-statuses}

![](../../assets/common.svg)

<!--ajouter intro 

ajouter screenshot -->

發送交貨後，交貨控制面板將顯示一個狀態，允許您監視發送是否成功。 可能的狀態在下面一節中詳細說明。

![](assets/delivery-status.png)

有關您可能遇到的不同交貨失敗以及如何解決它們的詳細資訊，請參閱 [此頁](understanding-delivery-failures.md)。

**相關主題：**

* [傳遞儀表板](delivery-dashboard.md)
* [傳遞疑難排解](delivery-troubleshooting.md)
* [開始使用可交付性](about-deliverability.md)

## 交貨狀態清單 {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> 狀態<br /> </th> 
   <th> 定義和解決方案<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已傳送<br /> </td> 
   <td> 已將傳遞正確發送到消息提供程式（但收件人未必收到）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已忽略<br /> </td> 
   <td> 由於收件人的地址出錯，未將傳遞發送給收件人。 它位於denylist上、已隔離、未提供或重複。 <br /> </td> 
  </tr> 
  <tr> 
   <td> 失敗<br /> </td> 
   <td> 例如，由於地址無效或收件箱已滿，無法到達收件人。 它還可以連結到具有個性化塊的問題，因為當架構與傳遞映射不匹配時，這些塊可以生成錯誤。 請參閱 <a href="understanding-delivery-failures.md" target="_blank">瞭解交付失敗</a><br /> </td> 
  </tr>
  <tr> 
   <td> 待定<br /> </td> 
   <td> 遞送已準備好被發送，並且將由遞送伺服器(MTA)處理。 請參閱 <a href="#pending-status" target="_blank">掛起狀態</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不適用<br /> </td> 
   <td> 伺服器(MTA)已考慮傳遞，但未處理。<br /> </td> 
  </tr>  
  <tr> 
   <td> 已取消交貨<br /> </td> 
   <td> 操作員已取消交貨。<br /> </td> 
  </tr> 
  <tr> 
   <td> 服務提供商考慮的因素<br /> </td> 
   <td> SMS服務提供商收到了傳遞。<br /> 對於托管或混合安裝，如果已升級到 <a href="sending-with-enhanced-mta.md" target="_blank">增強的MTA</a>，該消息已成功從「市場活動」轉發到增強的MTA。</td> 
  </tr> 
  <tr> 
   <td> 在移動端接收<br /> </td> 
   <td> 接收方在其移動設備上收到SMS。<br /> </td> 
  </tr>
  <tr> 
   <td> 已發送到服務提供商<br /> </td> 
   <td> 該傳遞已發送到SMS服務提供商，但尚未收到。<br />
   </td> 
  </tr> 
  <tr> 
   <td> 已準備<br /> </td> 
   <td> 中間狀態僅用於外部連接器，如移動通道。 它遵循「掛起」狀態，是確定以下狀態的外部連接器。<br /> </td> 
  </tr> 
 </tbody> 
</table>

要瞭解如何優化Adobe Campaign電子郵件的傳送能力，請參閱 [此部分](about-deliverability.md)。 有關交付能力的更深入瞭解，請參閱 [Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant)。

## 掛起狀態 {#pending-status}

確認交貨後，您可以看到交貨的狀態為 **[!UICONTROL Pending]**。 此狀態表示執行進程正在等待某些資源的可用性。

的 **[!UICONTROL Pending]** 狀態首先表示您的交貨已計畫並且一直等待到給定日期。 有關詳細資訊，請參閱 [交貨計畫](steps-sending-the-delivery.md#scheduling-the-delivery-sending) 的子菜單。

如果未發送您的交貨，且其狀態仍為 **[!UICONTROL Pending]**，它可能是：

* MTA（郵件傳輸代理）在傳遞伺服器上運行模組和進程，並管理電子郵件發送，它可能尚未啟動，或可能需要重新啟動。

   要檢查此項並在必要時啟動模組，請應用以下步驟：

   >[!NOTE]
   >
   >此操作可通過 **現場** 或 **混合** 具有「市場活動」伺服器訪問權限的托管模型(請參閱 [托管模型](../../installation/using/hosting-models.md))。

   1. 檢查 `mta@<instance>` 模組將在MTA伺服器上啟動。

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. 如果未列出MTA，請使用以下命令啟動它：

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >替換 `<INSTANCENAME>` 實例名稱（生產、開發等）。 實例名稱通過配置檔案標識： `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* 傳遞可能使用發送伺服器上未配置的關聯。

   在這種情況下，檢查流量管理（IP關聯）的配置，然後使用 **[!UICONTROL Managing affinities with IP addresses]** 欄位，將交貨連結到管理關聯的MTA。 有關關聯的詳細資訊，請參閱 [此部分](../../installation/using/configure-delivery-settings.md)。

* 當運行過多市場活動時，交貨狀態仍為「待定」狀態。

   同時市場活動的限制在 **[!UICONTROL NmsOperation_LimitConcurrency]** 的雙曲餘切值。 預設值為 10。

   瞭解有關中選項的詳細資訊 [此頁](../../installation/using/configuring-campaign-options.md)。


**相關主題：**

* [交付日誌和歷史記錄](#delivery-logs-and-history)
* [瞭解傳遞故障](understanding-delivery-failures.md)
* [傳送失敗類型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
