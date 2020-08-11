---
title: 在Adobe Campaign Classic中管理傳遞性時的要點
description: 在Adobe Campaign Classic中管理傳遞性時，需要檢查哪些要點？
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b14f5ecd2b06ed9f4cb49d8779b9f94ea4bcdddc
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---


# 可傳遞性關鍵點{#deliverability-key-points}

若要最佳化Adobe Campaign電子郵件的傳遞能力，我們建議使用下列最佳實務。 傳遞能力問題通常與網際網路服務提供商和郵件伺服器管理員實施的針對垃圾郵件的保護措施有關。

**電子郵件傳送能力** ，是指一組特性，這些特性決定了郵件在短時間內，通過個人電子郵件地址到達其目的地的能力，並且在內容和格式方面具有預期的質量。

這些特徵可分為四大類：
* 資料品質
* 訊息與內容
* 發送基礎架構
* 聲譽

它們共同構成了成功的電子郵件傳遞能力計畫的基礎。

傳遞 **能力比率** ，是已傳送成功傳送給收件者的電子郵件數。

可交付率取決於眾多因素，特別是：
* 正確配置實例
* 您的IP位址信譽
* 目標地址的質量
* 低投訴與高反彈率
* 您的訊息內容
* 消息驗證(SPF、DKIM、DMARC)
* 發件人信譽

以下列出要檢查的要點，以確保良好的交付能力。

## 檢查網路配置 {#network-configuration}

垃圾郵件發送者試圖隱藏其真實身份，結果導致其伺服器難以識別。 不嘗試隱藏伺服器身份的合法網路配置對於大量發送電子郵件至關重要。

## 傳送至有效位址 {#valid-addresses}

垃圾郵件發送者通常使用基於頻繁名稱和名字清單的地址生成器；此外，他們很少處理郵件伺服器傳回的技術通知。 無效地址的高率通常被解釋為垃圾郵件的標誌。 雙重加入機制和有效處理技術反彈訊息，可避免此情況。

## 減少投訴和反彈率 {#reduce-complaint-rates}

ISP通常會以明顯的方式將收到的訊息報告為垃圾訊息。 這使得識別不可靠源成為可能。 透過快速執行退出要求、定期使用特定清單、透過雙重加入系統驗證同意，並實作回饋回覆，您可以降低投訴率。

## 傳送至蜜罐地址 {#honeypot-addresses}

ISP和其他組織(請參閱 [Project Honey Pot網站](https://www.projecthoneypot.org/) )會利用不對應於實際人員、但僅是為了欺騙垃圾郵件發送者而建立的郵箱。 這些所謂的「蜜罐」地址會發佈在網路上，以便由垃圾郵件機器人收集，從而捕獲非法發送者。 使用雙重選擇加入機制，將此類地址排除在清單中。 使用協力廠商清單時，您必須確定其維護人員採用的方法。

## 調整訊息內容 {#message-content}

在較小程度上，某些郵件的內容會導致某些篩選器將其檢測為垃圾郵件。 使用某些單字、在主旨行和訊息內使用驚嘆號，會視為垃圾郵件的告示符號。 此外，垃圾郵件發送者已知會用影像取代文字，以防止反垃圾郵件過濾器自動分析違規文字。 因此，含有高比例影像或影像作為附件的訊息（HTML格式）最終可能會遭到封鎖。

## 以您的聲譽為榮 {#reputation}

寄送垃圾郵件的人會進行程式化傳送，以維持其久遠的聲譽。 他們有時需要調整行銷計畫，以符合ISP強加的最佳實務，因此，在聲譽達到高峰（上升）後，他們會設定定期的遞送。

## 最佳實務{#best-practices}

瞭解與Adobe Campaign的傳遞能力相關的最佳實務。 使用下列連結來導覽主題並尋找指引。

<table>
<tr>
  <td>
    <a href="starting-new-platform.md">
      <img alt="開始" src="assets/do-not-localize/start.svg"/>
    </a>
    <div>
      <a href="starting-new-platform.md">
    <strong>開始</strong>
    </a>
    </div>
    <p>
    <em>啟動新平台</em>
    <p>
  </td>
   <td>
    <a href="control-message-content.md">
      <img alt="設計" src="assets/do-not-localize/design.svg"/>
    </a>
    <div>
      <a href="control-message-content.md">
    <strong>設計</strong>
    </a>
    </div>
    <p>
    <em>控制訊息內容</em>
    <p>
  </td>
  <td>
    <a href="improve-reputation.md">
      <img alt="設計" src="assets/do-not-localize/check.svg"/>
    </a>
    <div>
      <a href="improve-reputation.md">
    <strong>傳送</strong>
    </a>
    </div>
    <p>
    <em>提升您的聲譽</em>
    <p>
  </td>
</tr>
<tr>
  <td>
    <a href="technical-recommendations.md">
      <img alt="最佳化" src="assets/do-not-localize/optimize.svg"/>
    </a>
    <div>
      <a href="technical-recommendations.md">
    <strong>最佳化</strong>
    </a>
    </div>
    <p>
    <em>技術建議</em>
    <p>
  </td>
   <td>
    <a href="monitoring-deliverability.md">
      <img alt="檢查" src="assets/do-not-localize/monitor.svg"/>
    </a>
    <div>
      <a href="monitoring-deliverability.md">
    <strong>顯示器</strong>
    </a>
    </div>
    <p>
    <em>監控工具</em>
    <p>
  </td>
  <td>
    <a href="deliverability-faq.md">
      <img alt="最佳化" src="assets/do-not-localize/troubleshoot.svg"/>
    </a>
    <div>
      <a href="deliverability-faq.md">
    <strong>疑難排解</strong>
    </a>
    </div>
    <p>
    <em>解決問題</em>
    <p>
  </td>
</tr>
</table>
