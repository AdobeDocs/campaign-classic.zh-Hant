---
product: campaign
title: Chrome Firefox和Edge瀏覽器中的促銷活動Web元件和版本100
description: Chrome、Firefox和Edge瀏覽器中的市場活動Web元件和版本100
hide: true
hidefromtoc: true
source-git-commit: 48c9aab4f7e5f1f204a003a4d53f8d975247b867
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# 3位瀏覽器版本對市場活動Web元件的影響 {#version-100}

Google、Mozilla警告說，Chrome和Firefox可能會因即將推出的3位版本而破壞一些網站。

Chrome v100已設定為在 **2022年3月29日**、和Firefox v100開啟 **2022年5月3日**。

請注意，MicrosoftEdge於2022年3月較早時發佈了100版。

版本號從2到3位數的更改可能會在訪問未準備進行此更改的網站時導致一些問題。 某些網頁可能會在這些新瀏覽器版本中停止正確顯示。

主要網站的相容性提前測試。 如果在發佈這些版本之前無法修復的站點存在問題，則公司已準備好備份計畫以確保站點不受影響。

網站上的潛在問題或功能丟失源於瀏覽器發送到您訪問的網站的用戶代理字串：用戶代理是瀏覽器發送到網站的字串，用於讓網站知道您使用的瀏覽器和版本以及相關技術。 當您的瀏覽器向網站發送請求時，它會在檢索您請求的內容之前用用戶代理字串標識自己。 用戶代理字串中的資料有助於網站以適合瀏覽器的格式傳送內容。 用戶代理的版本將遞增，以與瀏覽器版本號匹配。 從2位移到3位可能會導致問題。

## 您有受到影響嗎？{#version-100-impact}

Adobe建議您test市場活動Web應用程式，包括Web表單和調查，以確保這些應用程式在這些新的瀏覽器版本中仍能正常工作。

此建議適用於所有Web應用程式，尤其是如果您已包含JavaScript代碼。

您必須使用所有瀏覽器、移動和案頭同時檢查兩者。

## 如何test?{#version-100-test}

您可以配置瀏覽器以立即將版本報告為100，然後報告並更正您遇到的任何問題。

使用這些設定，瀏覽器將新用戶代理字串發送到網站，指示瀏覽器為v100。 如果您的Web表單遇到任何問題，應為瀏覽器編輯器建立一個Bug。 請考慮在這些更新廣泛可用之前重建這些Web表單。

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

要將用戶代理更改回其預設值，只需返回 `about:config` 並搜索 `general.useragent.override` 的子菜單。  出現時，按一下垃圾表徵圖以刪除設定，然後重新啟動瀏覽器。

### 帶Chrome 100的test{#test-chrome-100}

要在您自己的Web應用上testGoogleChrome 100用戶代理，可以使用以下步驟啟用此test:

1. 開啟Chrome，輸入 `chrome://flags` 在地址欄中，然後按Enter鍵。
1. 搜索 `Force major version to 100 in User-Agent` ，並按如下所示啟用它。

   ![](assets/force-user-agent-chrome.png)

1. 重新啟動瀏覽器。
1. 關閉 `chrome://flags` 頁籤。

要將用戶代理更改回其預設值，只需按照此過程操作，並將標誌的設定更改為 `Default` 然後重新啟動瀏覽器。


### Test與MicrosoftEdge 100{#test-ms-edge-100}

從v97開始，站點所有者可以通過啟用實驗標誌來模擬此版本  `#force-major-version-to-100` 在 `edge://flags`。

1. 開啟Microsoft邊，輸入 `edge://flags` 在地址欄中，然後按Enter鍵。
1. 搜索 `force-major-version-to-100` ，並啟用它，如下所示。

   ![](assets/force-user-agent-edge.png)

1. 重新啟動瀏覽器。
1. 關閉 `edge://flags` 頁籤。

要將用戶代理更改回其預設值，只需按照此過程操作，並將標誌的設定更改為 `Default` 然後重新啟動瀏覽器。
