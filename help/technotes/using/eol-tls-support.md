---
product: campaign
title: 終止支援 TLS 1.0 和 1.1
description: 終止支援 TLS 1.0 和 1.1
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: e18d43b6-2a77-4881-85e7-ca36248d4634
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---

# 終止支援 TLS 1.0 和 1.1{#eol-tls-support}



Adobe不再支援不符合傳輸層安全性(TLS)1.2通訊協定的使用者系統和用戶端系統。 如果您繼續使用舊版TLS，則可能會失去所有Adobe產品和服務的存取權。

## 為何會看到此頁面？

如果您看到下列訊息： **無法顯示此頁**，這表示您嘗試存取的Adobe應用程式、網頁或服務，需要與網頁瀏覽器、作業系統或應用程式建立更安全的網路連線。 必須使用 **TLS 1.2** 用於用戶系統和Adobe應用和web服務之間的安全網路通信和資料交換。

Adobe已不再支援較低版本的TLS（包括TLS 1.0和1.1）。 如需TLS 1.2通訊協定的技術詳細資訊，請參閱 [常見問題](#faq).

## 我可以做什麼來恢復服務？

現代網頁瀏覽器支援TLS 1.2。升級您的瀏覽器可讓您存取這些應用程式和服務。

您可以下載並安裝下列其中一個常用瀏覽器：

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

如果您使用其他瀏覽器，請確定其支援TLS 1.2。

您的作業系統和應用程式架構也必須支援TLS 1.2。如果升級瀏覽器無法解決問題，請確定您的電腦符合 [Campaign相容性矩陣](../../rn/using/compatibility-matrix.md).

## 常見問題{#faq}

* **什麼是傳輸層安全性(TLS)?**

   [傳輸層安全性](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS)是一種安全通訊協定，可在兩個通訊應用程式之間提供隱私權和資料完整性。 它廣泛部署於需要透過網路安全交換資料的網頁瀏覽器和其他應用程式。

   根據協定規範，TLS包括TLS記錄協定和TLS握手協定兩層。 記錄協定提供連接安全性。 握手協定使伺服器和客戶端能夠相互驗證，並在資料交換之前協商加密算法和加密密鑰。

* **會有什麼影響？**

   Adobe的安全性法規遵循標準要求自2018年5月起淘汰舊版通訊協定，並規定使用TLS 1.2作為最新版本。 如果您的系統不符合TLS 1.2，則對某些Adobe應用程式和服務的存取權限會受限。

* **TLS對您有何影響？**

   您只能透過安全的網路連線與某些Adobe應用程式和服務互動。 TLS有助於確保您的瀏覽器與這些應用程式及網站服務之間的連線安全可靠。

   隨著新瀏覽器和作業系統的發佈，安全標準也隨之升級，以確保更高層級的隱私權和資料完整性。 不過，這些瀏覽器或作業系統的舊版本並未更新以納入最新標準。

   隨著可接受的安全級別的提高，這些較舊、較不安全的瀏覽器版本和應用程式將被拋在後面。

   若要與安全網站連線，請更新您的作業系統和瀏覽器版本。

* **TLS是否容易受到駭客攻擊？**

   已記錄使用舊版加密方法對TLS 1.0的攻擊，且較舊版本比TLS 1.2更容易受到攻擊。如需詳細資訊，請參閱對TLS/SSL的攻擊。

* **為什麼Adobe停用對TLS 1.0和1.1的支援？**

   Adobe有安全性法規遵循標準，需要禁用對舊協定的支援。 此類標準可確保符合支付卡行業(PCI)。 PCI適配伺服器是一組安全標準，要求接受、處理、儲存或傳輸信用卡資訊的組織維護一個安全的環境。

   自2018年5月起，PCI法規規定必須使用TLS 1.1或更新版本。

* **為何Adobe強制使用TLS 1.2而非允許TLS 1.1或TLS 1.0?**

   對Adobe應用程式和網站服務的大部分要求來自符合TLS 1.2的使用者系統，來自TLS 1.1系統的低流量。

   Adobe已移轉至TLS 1.2，因此其應用程式和網站服務的存取安全性更高。

* **我可以使用舊版TLS的最後日期是什麼？**

   Adobe可鼓勵使用者快速放棄舊版，以免暴露於安全性弱點。 如需詳細資訊，請聯絡Adobe客戶服務或您的客戶成功經理。

* **如果我使用的瀏覽器未針對TLS 1.2進行設定，會顯示什麼錯誤訊息？**

   這取決於您使用的瀏覽器。 中提及的所有瀏覽器 [Campaign相容性矩陣](../../rn/using/compatibility-matrix.md) 已設定為使用TLS 1.2。如果您使用的瀏覽器或版本未列在清單中，請更新您的瀏覽器。

   Adobe不控制SSL通信層生成的錯誤消息。 瀏覽器會在連線至Adobe應用程式和服務之前產生這些訊息。 以下是Windows 7上Internet Explorer 11可能發生的錯誤範例：

   ![](assets/do-not-translate/page-not-displayed.png)

   Internet Explorer 11預設會啟用TLS 1.2，但如果關閉，您可以將其開啟。 在此情況下，請從進階設定對話方塊開啟TLS 1.2，而不使用其他選項。 其他錯誤，例如，也可能發生：

   * 無法連接到服務
   * 服務無法提供
   * 連接中出錯
