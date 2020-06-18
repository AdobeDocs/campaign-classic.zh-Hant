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
source-git-commit: 56fed9fff445892366d3e0f1367029882077ae20
workflow-type: tm+mt
source-wordcount: '1355'
ht-degree: 0%

---


# 可傳遞性疑難排解{#deliverability-faq}

您是否遇到交付能力問題？ 您可以在這裡找到解決方案。

## MX規則錯誤 {#mx-rule-error}

**錯誤訊息「配額符合」代表什麼意思？**

此訊息指出您已達到特定MX的配額限制，您必須等候才能傳送其他電子郵件給此供應商。

在Adobe Campaign中，會針對每小時可傳送的電子郵件數設定。 此配置必須引起警惕，因為實例中定義的數字與與與ISP進行的連接數有關，而與實際發送的電子郵件數無關。

這表示連線可使用MX規則，但無法成功傳送電子郵件。 在這種情況下，使用IP或信譽不佳的網域的組態必須先嘗試數個連線，才能傳送電子郵件。 每次嘗試都會使用每小時評分的訊息。 因此，行銷促銷活動的績效將會受到重大影響。

因此，&quot;配額滿足&quot;不僅是配置問題，還與信譽掛鈎。 分析 [SMTP日誌中的錯誤消息非常重要](../../production/using/monitoring-processes.md#smtp-errors-per-domain)。

如需MX設定的詳細資訊，請參 [閱本節](../../installation/using/email-deliverability.md#mx-configuration)。

## ISP的相同錯誤資訊 {#same-error-for-an-isp}

**為什麼對於特定ISP，我總是收到相同的錯誤訊息？**

如果您總是收到相同的ISP錯誤訊息，則ISP可能會偵測到您的電子郵件或IP有故障。 執行下列建議：
* 檢查您是否收到連結至不存在之電子郵件地址的大部分失敗(使&#x200B;**用者未知** 失敗)。
* 更新訂閱表單以偵測輸入的網域名稱中的任何錯誤(例如： gmaul.com或yaho.com)。
* 如果您發現錯誤，指出您的訊息已宣告為垃圾訊息，或您的訊息經常遭到封鎖，請嘗試將過去12個月中未開啟或點按其中一則訊息的收件者排除在目標位置。

如果問題持續存在，請聯絡商業或傳遞性服務、Adobe Campaign Client Care或Adobe Campaign支援。

## 塊清單與隔離 {#block-list-versus-quarantine}

* **阻止清單上的電子郵件地址與隔離的電子郵件地址之間有何區別？**

   * 狀態是 **[!UICONTROL On block list]** 回饋迴路的結果（當某人將訊息報告為垃圾訊息時）。

   * 狀態 **[!UICONTROL Quarantined]** 是軟反彈或硬反彈的結果。
   For more on this, see [this section](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-block-list).

* **不同的隔離錯誤原因意味著什麼？**

   以下是10個可能的原因： 未定義、用戶未知、無效域、塊清單上的地址、拒絕、錯誤忽略、無法訪問、帳戶禁用、郵箱已滿、未連接。

   有關詳細資訊，請參閱了 [解隔離管理](../../delivery/using/understanding-quarantine-management.md)。

## 從塊清單中刪除 {#remove-from-block-list}

* **我的其中一個收件者被錯誤地加入區塊清單。 如何從塊清單中刪除它們，以便我可以再次開始發送郵件？**

   * 前往 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**。
   * 在對應記錄的詳細資訊中，將欄位的值 **[!UICONTROL Status]** 設定為 **[!UICONTROL Valid]**。
   * 保存記錄。

* **我要如何得知我的其中一個IP是否在區塊清單中？ 如何從塊清單中刪除IP?**

   若要檢查您的IP位址是否在區塊清單中，您可以使用各種網站來驗證它，例如：
   * [MX工具箱](https://mxtoolbox.com/)
   * [我的IP地址是什麼](https://whatismyipaddress.com)
   通常，IP地址檢查的結果將返回一個清單，其中包含塊清單的詳細資訊以及阻止IP地址的網站的名稱。

   按一下對應的連結，即可存取網站詳細資訊。 然後，您可以要求將您的網站從將IP位址新增至其區塊清單的網站中除名。

   >[!NOTE]
   >
   >除名程式可能因網站而異。 有些網站會要求您建立帳戶，而有些網站則只需您提供IP位址。

## 最佳實務{#best-practices}

以下是一些最佳實務，可協助您找出並解決傳遞性問題。

### 識別傳遞能力問題 {#identify-deliverability-issue}

以下元素可能會引起您的注意：

* 郵寄或促銷活動量度： 取消訂閱、濫用投訴及／或反彈率高於往常。
* 訂閱者活動： 開啟、點按和／或交易都低於一般。
* 種子帳戶會顯示已篩選或未傳送的郵件。

### 假設電位的原因 {#potential-causes}

請自問下列問題，以找出您的傳遞能力問題的可能原因：

* 清單區隔最近有變更嗎？
* 我是否已取得任何新的資料來源？
* 我是不是不小心寄了隔離檔案？
* 問題是否可能是因為我的訊息內容？
* 我發送的郵件是否足夠頻繁，以維持溫暖的IP?
* 我是否會依活動／參與來劃分郵件，或傳送完整檔案？
* 我檔案的「安全」區段在最近一次使用時是什麼？
* 對於未定義為安全的區段，我是否有重新啟動和重新確認策略？

### 解決問題 {#address-issue}

**投訴**

投訴由訂閱者定義，他們 **會從收件匣中按一下對應的按鈕** ，將電子郵件報告為垃圾訊息。

如果您的送貨問題是由於投訴造成的：
* 您需要嘗試判斷收件者抱怨的原因。
* 您也可以考慮將取消訂閱連結移至電子郵件的頂端。 這將鼓勵訂閱者取消訂閱，而不是抱怨垃圾訊息按鈕。

寄件者可以從反饋回來的投訴中獲 [得大量信](../../delivery/using/technical-recommendations.md#feedback-loop) 息：
* 必須將資料分類，並在選擇加入來源、地址已訂閱多久，甚至某些行為人口統計資料中尋找模式。
* 投訴通常可識別檔案中有風險的資料來源或區段。 「風險」是指最有可能抱怨的，這會損害聲譽，進而損害收件匣費率。

抱怨也來自那些不想再收到電子郵件的訂閱者：
* 這通常是因為訂閱者的訊息傳遞過度、對訊息的認知、他們不期待訊息，或不記得選擇加入。
* 此外，執行稽核也很重要，以確保所有收集點都清楚，而且您的收集點中沒有預先勾選的方塊。
* 當訂閱者選擇加入以設定音調，並說明他們預期收到您電子郵件的頻率時，您也應寄送歡迎電子郵件。

**資料有效性**

**當您傳送** 至ISP的無法傳送的位 **址時** ，會出現硬彈回。 由於以下許多原因，地址無法交付：
* 地址拼錯了。 這可透過即時資料驗證服務來解決，或在傳送行銷電子郵件至該位址之前，要求確認選擇加入。
* 錯誤清單或資料源。 如果是來自新來源，請檢閱地址的收集方式，並確保有權限。
* 郵寄至一次處於活動狀態，但閒置一段時間後已關閉或終止的位址。

**參與**

除了抱怨和資料有效性外，ISP也比以往更加專注於積 **極的參與** ，以做交付決策。 他們希望瞭解您的訂閱者是要開啟您的電子郵件，還是不閱讀而刪除電子郵件。 由於他們不會與寄件者分享此資料，因此我們必須運用現有的資訊，並將開啟／點按／交易轉譯為參與。

在持續維護聲譽的過程中，請務必瞭解訂閱者在您的名單中的參與程度，並為每個檔案的訂閱者 **建立時近風險等級** 。 最近一次開啟／點按／處理或註冊日期。 此時間範圍可能因垂直而不同。 操作步驟：

1. 確定每個垂直區段的作用中（「安全」）區段。 這通常是過去3-6個月內活動的訂閱者。
1. 降低發生頻率。
1. 建立重 [新參與系列](../../delivery/using/re-engagement-best-practices.md) ，以適度降低風險。 這通常是6-9個月，不需參與。
1. 針對高風險行為，制定重新確認促銷活動。 這通常是9-12個月內未收到電子郵件的訂閱者。
1. 最後，設定退出規則，並移除在「x」個月內未開啟您電子郵件的訂閱者。 我們通常建議使用12個月以上，但這可能因銷售和購買週期而有所不同。
