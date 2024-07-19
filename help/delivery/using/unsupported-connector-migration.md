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

已棄用的功能仍可使用並受支援，但將不會進一步增強。 我們建議使用&#x200B;**[!UICONTROL Extended generic SMPP]**&#x200B;聯結器。

如需已棄用和已移除功能的詳細資訊，請參閱此[頁面](../../rn/using/deprecated-features.md)。

舊的SMS聯結器使用Java SMS聯結器，該Java SMS聯結器會多載網頁程式。 移轉至新的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;聯結器會將此載入移至可支援的MTA。

## 遷移到擴展的通用SMPP聯結器 {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>即使您可以轉換引數，設定&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;聯結器需要您與提供者交談，提供者會提供您填寫其餘引數所需的資訊。 如需關於此項目的詳細資訊，請參閱此[頁面](sms-protocol.md)。

首先，您需要建立新的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;外部帳戶，然後您或許可以轉置某些引數。 您可以在此[頁面](sms-set-up.md#creating-an-smpp-external-account)中找到詳細步驟。

您現在需要根據先前的聯結器，從新建立的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;外部帳戶的&#x200B;**[!UICONTROL Mobile]**&#x200B;標籤中填入引數。

### 從一般聯結器 {#from-generic-connector}

選擇&#x200B;**[!UICONTROL Generic]**&#x200B;聯結器時，您應該要有可因應各種情況的自訂JavaScript聯結器。

如果您知道此聯結器已在使用SMPP通訊協定，則可以移轉至&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;聯結器。 如果沒有，請洽詢您的提供者是否支援SMPP通訊協定，並在顧問的協助下設定新的聯結器。

從您的&#x200B;**[!UICONTROL Generic]**&#x200B;聯結器，您可以轉置到您新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_generic.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;索引標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### 來自通用SMPP聯結器 {#from-generic-smpp-connector}

從您的&#x200B;**[!UICONTROL Generic SMPP]**&#x200B;聯結器，您可以轉置到您新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_generic_2.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;索引標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;索引標籤中：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

在&#x200B;**[!UICONTROL Mapping of Encoding]**&#x200B;索引標籤中：

* **[!UICONTROL Outbound SMS coding]**

在&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;索引標籤中：

* **[!UICONTROL Coding when sending]**&#x200B;對應至&#x200B;**[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]**&#x200B;對應至&#x200B;**[!UICONTROL ID Format in the SR]**

### 從Sybase365聯結器 {#from-sybase}

從您的&#x200B;**[!UICONTROL Sybase365]**&#x200B;聯結器，您可以轉置到您新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_3.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;索引標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### 從CLX聯結器 {#from-clx}

從您的&#x200B;**[!UICONTROL CLX]**&#x200B;聯結器，您可以轉置到您新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_4.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;索引標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;索引標籤中：

* **[!UICONTROL Source number]**

在&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;索引標籤中：

* **[!UICONTROL Coding when sending]**&#x200B;對應至&#x200B;**[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]**&#x200B;對應至&#x200B;**[!UICONTROL ID Format in the SR]**

### 從Tele2聯結器 {#from-tele2}

從您的&#x200B;**[!UICONTROL Tele2]**&#x200B;聯結器，您可以轉置到您新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_6.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;索引標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;索引標籤中：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

在&#x200B;**[!UICONTROL Mapping of Encoding]**&#x200B;索引標籤中：

* **[!UICONTROL Outbound SMS coding]**

### 從O2聯結器 {#from-O2}

從您的&#x200B;**[!UICONTROL O2]**&#x200B;聯結器，您可以轉置到您新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_5.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;索引標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;索引標籤中：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**
