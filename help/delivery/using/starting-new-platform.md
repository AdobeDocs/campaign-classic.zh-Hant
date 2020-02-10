---
title: 使用Adobe Campaign Classic啟動新平台
description: 進一步瞭解使用Adobe Campaign Classic啟動新平台時如何管理傳遞能力。
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
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# 啟動新平台 {#starting-new-platform}

維護您的網域和IP位址信譽至關重要。 您會在以下找到有關設定新平台的建議。

開始在新平台上傳送電子郵件是一個敏感的步驟，因為該平台沒有任何使用記錄，也沒有信譽（當傳送的IP從未用於此目的時）。 ISP自然會懷疑從未用於傳送電子郵件的IP位址，而且會突然開始傳送大量電子郵件流量。 實際上，垃圾郵件發送者通常使用「未知」的IP位址（即從未列入黑名單的位址），在偵測前傳送最多的訊息。

在生產階段開始時，您無法期望在產出方面達到操作速度。 此外，您不應嘗試以此速率發送消息，因為這可能導致ISP阻塞發送地址，並嚴重危害啟動階段的其他階段。

首次使用地址清單且可能無法完全限定的平台時，通常會啟動平台。 如果您傳送至無效的位址或蜜罐位址，這將會降低平台的聲譽。 如果您有無效地址清單，在第一次發送前將其導入隔離表(**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**)符合您的最大利益。 但是，如果您希望重新命名無效地址，則最好在平台信譽建立後再逐個逐個地執行此操作，以便隨著時間的推移「稀釋」不良地址的使用。

總結啟動時應遵循的原則：

* 將無效地址導入隔離表中（如果您有此資訊）
* 限制吞吐量速率(技術設定：限制匹配項數)
* 逐漸增加發送的卷：從一開始就不要將整個資料庫作為目標，而是每次傳送時，在清單中增加一小部分；這應可讓您在每個步驟增加音量，同時降低無效地址的總體速率
* 定期傳送：在某種程度上，定期傳送小鏡頭比偶爾傳送大型宣傳更好
* 密切關注交付報表：高錯誤指示燈可能表示技術設定配置不當。