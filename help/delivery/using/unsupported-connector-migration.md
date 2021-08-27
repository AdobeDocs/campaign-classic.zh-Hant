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

已棄用的功能仍可供使用且受支援，但將不會進一步增強。 建議使用&#x200B;**[!UICONTROL Extended generic SMPP]**&#x200B;連接器。

有關已棄用和已移除功能的詳細資訊，請參閱此[page](../../rn/using/deprecated-features.md)。

舊版SMS連接器使用會過載Web程式的Java SMS連接器。 移轉至新的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;連接器會將此負載移至可支援此負載的MTA。

## 正移轉至Extended Generic SMPP連接器 {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>即使您可以轉換參數，配置&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;連接器也需要與提供程式進行交談，該提供程式將為您提供填入其餘參數所需的資訊。 如需關於此項目的詳細資訊，請參閱此[頁面](sms-protocol.md)。

首先，您需要建立新的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;外部帳戶，然後您可能可以轉換一些參數。 您可以在此[page](sms-set-up.md#creating-an-smpp-external-account)中找到詳細步驟。

您現在需要根據先前的連接器，從新建立的&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;外部帳戶的&#x200B;**[!UICONTROL Mobile]**&#x200B;標籤填入參數。

### 從通用連接器 {#from-generic-connector}

選擇&#x200B;**[!UICONTROL Generic]**&#x200B;連接器時，您應該有可適應每種情況的自訂JavaScript連接器。

如果您知道此連接器已使用SMPP協定，則可遷移至&#x200B;**[!UICONTROL Extended Generic SMPP]**&#x200B;連接器。 如果不支援，請洽詢您的提供者（如果他們支援SMPP通訊協定），並在顧問的協助下設定新連接器。

從&#x200B;**[!UICONTROL Generic]**&#x200B;連接器，您可以轉換至新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_generic.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### 從通用SMPP連接器 {#from-generic-smpp-connector}

從&#x200B;**[!UICONTROL Generic SMPP]**&#x200B;連接器，您可以轉換至新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_generic_2.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;標籤中：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

在&#x200B;**[!UICONTROL Mapping of Encoding]**&#x200B;標籤中：

* **[!UICONTROL Outbound SMS coding]**

在&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;標籤中：

* **[!UICONTROL Coding when sending]** 對應至  **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 對應至  **[!UICONTROL ID Format in the SR]**

### 從Sybase365連接器 {#from-sybase}

從&#x200B;**[!UICONTROL Sybase365]**&#x200B;連接器，您可以轉換至新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_3.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### 從CLX連接器 {#from-clx}

從&#x200B;**[!UICONTROL CLX]**&#x200B;連接器，您可以轉換至新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_4.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;標籤中：

* **[!UICONTROL Source number]**

在&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;標籤中：

* **[!UICONTROL Coding when sending]** 對應至  **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 對應至  **[!UICONTROL ID Format in the SR]**

### 從Tele2連接器 {#from-tele2}

從&#x200B;**[!UICONTROL Tele2]**&#x200B;連接器，您可以轉換至新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_6.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;標籤中：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

在&#x200B;**[!UICONTROL Mapping of Encoding]**&#x200B;標籤中：

* **[!UICONTROL Outbound SMS coding]**

### 從O2連接器 {#from-O2}

從&#x200B;**[!UICONTROL O2]**&#x200B;連接器，您可以轉換至新建立的&#x200B;**[!UICONTROL Extended SMPP]**&#x200B;帳戶：

![](assets/smpp_5.png)

在&#x200B;**[!UICONTROL Connection Settings]**&#x200B;標籤中：

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

在&#x200B;**[!UICONTROL SMPP Channel Settings]**&#x200B;標籤中：

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**
