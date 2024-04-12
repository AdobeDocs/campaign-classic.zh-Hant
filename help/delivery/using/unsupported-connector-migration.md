---
product: campaign
title: 不支援的SMS聯結器移轉
description: 將不支援的SMS聯結器移轉至Extended Generic SMPP聯結器
feature: SMS, Upgrade
hidefromtoc: true
exl-id: 60acf80c-8506-410b-ab2c-4f67a5677b43
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 1%

---

# 將不支援的SMS聯結器移轉至Extended Generic SMPP聯結器{#unsupported-connector-migration}



自版本20.2起，已棄用舊聯結器。 本檔案可協助您將仍在舊系統上執行的聯結器遷移至建議的SMPP聯結器。

>[!CAUTION]
>
>此移轉並非強制性，但由Adobe建議，並將確保您是在最新支援的軟體版本上執行。

## 關於SMS聯結器 {#about-sms-connectors}

下列聯結器自版本20.2起已淘汰：

* **[!UICONTROL Generic SMPP]** （支援二進位模式的SMPP 3.4版）
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

已棄用的功能仍可使用並受支援，但將不會進一步增強。 我們建議使用 **[!UICONTROL Extended generic SMPP]** 聯結器。

有關已棄用和已移除功能的詳細資訊，請參閱此 [頁面](../../rn/using/deprecated-features.md).

舊的SMS聯結器使用Java SMS聯結器，該Java SMS聯結器會多載網頁程式。 移轉至新 **[!UICONTROL Extended Generic SMPP]** 聯結器會將此負載移至可支援它的MTA。

## 遷移到擴展的通用SMPP聯結器 {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>即使您可以調換引數，設定 **[!UICONTROL Extended Generic SMPP]** 聯結器會要求您與提供者溝通，提供您填寫其餘引數所需的資訊。 如需關於此項目的詳細資訊，請參閱此[頁面](sms-protocol.md)。

首先，您需要建立新的 **[!UICONTROL Extended Generic SMPP]** 外部帳戶，然後您或許能夠轉譯一些引數。 您可以在這裡找到詳細步驟 [頁面](sms-set-up.md#creating-an-smpp-external-account).

您現在需要填寫以下專案的引數： **[!UICONTROL Mobile]** 您新建立的標籤 **[!UICONTROL Extended Generic SMPP]** 外部帳戶，具體取決於您先前的聯結器。

### 從一般聯結器 {#from-generic-connector}

當選擇 **[!UICONTROL Generic]** 聯結器後，您應該會有一個自訂JavaScript聯結器來因應各種情況。

如果您知道此聯結器已在使用SMPP通訊協定，則可以移轉至 **[!UICONTROL Extended Generic SMPP]** 聯結器。 如果沒有，請洽詢您的提供者是否支援SMPP通訊協定，並在顧問的協助下設定新的聯結器。

從您的 **[!UICONTROL Generic]** 聯結器，您可以調換至您新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

![](assets/smpp_generic.png)

在 **[!UICONTROL Connection Settings]** 標籤：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### 來自通用SMPP聯結器 {#from-generic-smpp-connector}

從您的 **[!UICONTROL Generic SMPP]** 聯結器，您可以調換至您新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

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

### 從Sybase365聯結器 {#from-sybase}

從您的 **[!UICONTROL Sybase365]** 聯結器，您可以調換至您新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

![](assets/smpp_3.png)

在 **[!UICONTROL Connection Settings]** 標籤：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### 從CLX聯結器 {#from-clx}

從您的 **[!UICONTROL CLX]** 聯結器，您可以調換至您新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

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

### 從Tele2聯結器 {#from-tele2}

從您的 **[!UICONTROL Tele2]** 聯結器，您可以調換至您新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

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

### 從O2聯結器 {#from-O2}

從您的 **[!UICONTROL O2]** 聯結器，您可以調換至您新建立的 **[!UICONTROL Extended SMPP]** 帳戶：

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
