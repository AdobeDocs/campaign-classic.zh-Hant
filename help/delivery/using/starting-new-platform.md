---
solution: Campaign Classic
product: campaign
title: 使用Adobe Campaign Classic啟動新平台
description: 進一步瞭解如何使用Adobe Campaign Classic建立新平台時管理傳遞能力。
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 1%

---


# 啟動新平台 {#starting-new-platform}

在設定新平台時，維護網域和IP位址的信譽至關重要。

* 開始傳送電子郵件是一個敏感的步驟，因為平台沒有任何使用記錄，而且當傳送的IP從未用於此目的時，就沒有信譽。

* ISP自然會懷疑從未用於傳送電子郵件的IP位址，而且會突然開始傳送大量電子郵件流量。 事實上，垃圾郵件發送者通常使用「未知」的IP位址（從未列在密鑰清單上的位址），在偵測前傳送最多的訊息。

* 在生產階段開始時，您無法期望在產出方面達到操作速度。 此外，您不應嘗試以此速率發送消息，因為這可能導致ISP阻塞發送地址，並嚴重危害啟動階段的其他階段。

以下列出啟動新平台時應遵循的主要原則：

* 如果您有此資訊， **將無效地址導入隔離表**。
首次使用地址清單且可能無法完全限定的平台時，通常會啟動平台。 如果您傳送至無效的位址或蜜罐位址，這將會降低平台的聲譽。

   * 如果您有無效地址清單，在首次發送前將其導入隔離表（可通過&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;菜單獲得）符合您的最大利益。
   * 但是，如果您希望重新命名無效地址，則最好在平台信譽建立後再逐個逐個地執行此操作，以便隨著時間的推移「稀釋」不良地址的使用。

   如需詳細資訊，請參閱[透過隔離最佳化傳送](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines)。
* **通過限制匹** 配數來限制吞吐率。如需有關調整此類技術設定的詳細資訊，請連絡您的Adobe Campaign管理員。
* **逐步增加卷，以** 避免標籤為垃圾郵件。從頭開始不要將整個資料庫作為目標，而是每次傳送時新增清單的一部分。 這應可讓您在每個步驟增加音量，同時降低無效地址的總體速率。 為確保啟動階段的順利開發，您可使用波。 有關詳細資訊，請參閱[使用多個波發送](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。
* **定期傳送**。從某種程度上講，定期傳送小鏡頭比偶爾傳送大型宣傳更好。
* **密切關注傳送報表**。高錯誤指示燈可能表示技術設定配置不當。 有關詳細資訊，請參閱[監視傳送](../../delivery/using/about-delivery-monitoring.md)。

**相關主題**：
* [透過IP變暖提高您的電子郵件聲譽](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [全部關於垃圾郵件陷阱](https://helpx.adobe.com/campaign/kb/spam-traps.html)