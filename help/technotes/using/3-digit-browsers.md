---
product: campaign
title: Chrome和Firefox瀏覽器中的促銷活動Web元件和版本100
description: Chrome和Firefox瀏覽器中的促銷活動Web元件和版本100
hide: true
hidefromtoc: true
source-git-commit: 88148b70de408de7571166e1869c088e10e87bae
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Chrome和Firefox v100對Campaing Web元件的影響 {#version-100}

Google和Mozilla警告說，Chrome和Firefox可能會因即將推出的3位版本而破壞一些網站。

版本號從2到3位數的更改可能會在訪問未準備進行此更改的網站時導致一些問題。 某些網頁可能會在這些新瀏覽器版本中停止正確顯示。

Chrome v100已設定為在 **2022年3月29日**、和Firefox v100開啟 **2022年5月3日**。

Mozilla和Google正在提前測試主要網站的相容性。 如果在發佈這些版本之前無法修復的站點存在問題，則兩個站點都準備好備份計畫以確保站點不受影響。

網站上的潛在問題或功能丟失源於瀏覽器發送到您訪問的網站的用戶代理字串：用戶代理是瀏覽器發送到網站的字串，用於讓網站知道您使用的瀏覽器和版本以及相關技術。 當您的瀏覽器向網站發送請求時，它會在檢索您請求的內容之前用用戶代理字串標識自己。 用戶代理字串中的資料有助於網站以適合瀏覽器的格式傳送內容。 用戶代理的版本將遞增，以與瀏覽器版本號匹配。 從2位移到3位可能會導致問題。

## 您有受到影響嗎？{#version-100-impact}

Adobe建議您test市場活動Web應用程式，包括Web表單和調查以及電子郵件鏡像頁，以確保這些應用程式在這些新瀏覽器版本中仍能正常工作。

此建議適用於所有Web應用程式，尤其是如果您已包含JavaScript代碼。

您必須同時使用Firefox和Chrome、移動和案頭進行檢查。

## 如何test?{#version-100-test}

在Chrome和Firefox中，您可以配置瀏覽器以立即將版本報告為100，然後報告並更正您遇到的任何問題。

### TestFirefox 100{#test-firefox-100}

要使用Mozilla Firefox 100test網頁，可以通過手動更改用戶代理字串來模擬即將在Web應用上進行的用戶代理更改。

1. 開啟Firefox，輸入 `about:config` 在地址欄中，然後按Enter鍵。
1. 搜索 `general.useragent.override`。
1. 選擇「字串」，然後按一下加號(+)。

   ![](assets/force-user-agent-firefox.png)

1. 在欄位中輸入以下文本：

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. 按一下藍色複選標籤按鈕以保存設定。
1. 關閉並重新啟動瀏覽器。

在這些設定下，瀏覽器將新用戶代理字串發送到網站，指示瀏覽器是Firefox 100。 如果您的Web表單遇到任何問題，則應為Mozilla建立新的Bug報告。 請考慮在此更改廣泛可用之前重建這些Web表單。

要將用戶代理更改回其預設值，只需返回 `about:config` 並搜索 `general.useragent.override` 的子菜單。  出現時，按一下垃圾表徵圖以刪除設定，然後重新啟動瀏覽器。

### 帶Chrome 100的test{#test-chrome-100}

要在您自己的Web應用上testGoogleChrome 100用戶代理，可以使用以下步驟啟用此test:

1. 開啟Chrome，輸入 `chrome://flags` 在地址欄中，然後按Enter鍵。
1. 搜索 `Force major version to 100 in User-Agent` ，並按如下所示啟用它。

   ![](assets/force-user-agent-chrome.png)

1. 關閉並重新啟動瀏覽器。
1. 關閉 `chrome://flags` 的上界。

使用這些設定，瀏覽器將新用戶代理字串發送到網站，指示瀏覽器是Chrome 100。 如果您訪問的網站遇到任何問題，應為Google建立新的Bug報告。 請考慮在此更改廣泛可用之前重建這些Web表單。

要將用戶代理更改回其預設值，只需按照此過程操作，並將標誌的設定更改為 `Default` 重新啟動瀏覽器。
