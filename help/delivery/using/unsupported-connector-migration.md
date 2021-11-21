---
product: campaign
title: 不支援的SMS連接器移轉
description: 將不支援的SMS連接器移轉至Extended Generic SMPP連接器
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
hidefromtoc: true
exl-id: 60acf80c-8506-410b-ab2c-4f67a5677b43
source-git-commit: 91dec9adb177aedc4a82879011371b54886166be
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---

# 將不支援的SMS連接器移轉至Extended Generic SMPP連接器{#unsupported-connector-migration}

![](../../assets/v7-only.svg)

舊版連接器自20.2版起將不再使用。 本文檔將幫助您將仍在舊系統上運行的連接器遷移到推薦的SMPP連接器。

>[!CAUTION]
>
>此移轉並非強制性，但Adobe建議您這麼做，這可確保您在最新支援的軟體版本上執行。

## 關於SMS連接器 {#about-sms-connectors}

下列連接器自20.2版起將不再使用：

* **[!UICONTROL Generic SMPP]** （支援二進位模式的SMPP 3.4版）
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

已棄用的功能仍可供使用且受支援，但將不會進一步增強。 建議您使用 **[!UICONTROL Extended generic SMPP]** 連接器。

如需已棄用和已移除功能的詳細資訊，請參閱 [頁面](../../rn/using/deprecated-features.md).

舊版SMS連接器使用會過載Web程式的Java SMS連接器。 移轉至新 **[!UICONTROL Extended Generic SMPP]** 連接器會將此負載移至可支援此負載的MTA。

## 正移轉至Extended Generic SMPP連接器 {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>即使您可以轉換參數，請設定 **[!UICONTROL Extended Generic SMPP]** 連接器需要您與提供者溝通，提供填入其餘參數所需的資訊。 如需關於此項目的詳細資訊，請參閱此[頁面](sms-protocol.md)。

首先，您需要建立新 **[!UICONTROL Extended Generic SMPP]** 外部帳戶，然後您可能可以轉換一些參數。 您可以在此找到詳細步驟 [頁面](sms-set-up.md#creating-an-smpp-external-account).

您現在需要從 **[!UICONTROL Mobile]** 標籤 **[!UICONTROL Extended Generic SMPP]** 外部帳戶（視您先前的連接器而定）。

### 從通用連接器 {#from-generic-connector}

選擇 **[!UICONTROL Generic]** 連接器中，您應有可因應各種情況的自訂JavaScript連接器。

如果您知道此連接器已使用SMPP通訊協定，則可移轉至 **[!UICONTROL Extended Generic SMPP]** 連接器。 如果不支援，請洽詢您的提供者（如果他們支援SMPP通訊協定），並在顧問的協助下設定新連接器。

從 **[!UICONTROL Generic]** 連接器，可以轉換至新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

![](assets/smpp_generic.png)

在 **[!UICONTROL Connection Settings]** 標籤：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### 從通用SMPP連接器 {#from-generic-smpp-connector}

從 **[!UICONTROL Generic SMPP]** 連接器，可以轉換至新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

![](assets/smpp_generic_2.png)

在 **[!UICONTROL Connection Settings]** 標籤：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在 **[!UICONTROL SMPP Channel Settings]** 標籤：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

在 **[!UICONTROL Mapping of Encoding]** 標籤：

* **[!UICONTROL Outbound SMS coding]**

在 **[!UICONTROL SMSC specificities]** 標籤：

* **[!UICONTROL Coding when sending]** 對應至 **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 對應至 **[!UICONTROL ID Format in the SR]**

### 從Sybase365連接器 {#from-sybase}

從 **[!UICONTROL Sybase365]** 連接器，可以轉換至新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

![](assets/smpp_3.png)

在 **[!UICONTROL Connection Settings]** 標籤：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### 從CLX連接器 {#from-clx}

從 **[!UICONTROL CLX]** 連接器，可以轉換至新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

![](assets/smpp_4.png)

在 **[!UICONTROL Connection Settings]** 標籤：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在 **[!UICONTROL SMPP Channel Settings]** 標籤：

* **[!UICONTROL Source number]**

在 **[!UICONTROL SMSC specificities]** 標籤：

* **[!UICONTROL Coding when sending]** 對應至 **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 對應至 **[!UICONTROL ID Format in the SR]**

### 從Tele2連接器 {#from-tele2}

從 **[!UICONTROL Tele2]** 連接器，可以轉換至新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

![](assets/smpp_6.png)

在 **[!UICONTROL Connection Settings]** 標籤：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在 **[!UICONTROL SMPP Channel Settings]** 標籤：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

在 **[!UICONTROL Mapping of Encoding]** 標籤：

* **[!UICONTROL Outbound SMS coding]**

### 從O2連接器 {#from-O2}

從 **[!UICONTROL O2]** 連接器，可以轉換至新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

![](assets/smpp_5.png)

在 **[!UICONTROL Connection Settings]** 標籤：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在 **[!UICONTROL SMPP Channel Settings]** 標籤：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**
