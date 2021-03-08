---
solution: Campaign Classic
product: campaign
title: 建立共用連線
description: 建立共用連線
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 2%

---


# 建立共用連線{#creating-a-shared-connection}

>[!IMPORTANT]
>
>* [消息中心技術工作流](../../message-center/using/technical-workflows.md)在控制或執行實例上對方案進行的方案擴展需要在Adobe Campaign事務消息模組使用的其他實例上重複。
>* 控制實例和執行實例必須安裝在不同的電腦上。 他們無法共用相同的促銷活動例項。

>



## 控制實例{#control-instance}

如果您有劃分的架構，則需要指定連結至控制例項的執行例項，並加以連接。 事務性消息模板被部署到執行實例。 通過配置&#x200B;**[!UICONTROL Execution instance]**&#x200B;類型外部帳戶，可建立控制實例與執行實例之間的連接。 您需要建立與執行例項數量相同的外部帳戶。

>[!NOTE]
>
>當多個控制例項使用執行例項時，資料可依資料夾和運算子來劃分。 有關詳細資訊，請參閱[使用多個控制實例](#using-several-control-instances)。

要建立執行實例類型外部帳戶，請應用以下步驟：

1. 前往&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;資料夾。
1. 選擇一個執行實例類型，其中一個是帶有Adobe Campaign的現成可用外部帳戶，按一下右鍵並選擇&#x200B;**[!UICONTROL Duplicate]**。

   ![](assets/messagecenter_create_extaccount_001.png)

1. 根據您的需求變更標籤。

   ![](assets/messagecenter_create_extaccount_002.png)

1. 選擇&#x200B;**[!UICONTROL Enabled]**&#x200B;選項，使外部帳戶可以運行。

   ![](assets/messagecenter_create_extaccount_003.png)

1. 指定安裝執行實例的伺服器的地址。

   ![](assets/messagecenter_create_extaccount_004.png)

1. 帳戶必須與「消息中心代理」匹配，如操作員資料夾中所定義。 依預設，Adobe Campaign提供的現成可用帳戶為&#x200B;**[!UICONTROL mc]**。

   ![](assets/messagecenter_create_extaccount_005.png)

1. 輸入在操作員資料夾中定義的帳戶密碼。

   >[!NOTE]
   >
   >為避免在每次登錄實例時輸入口令，您可以指定執行實例中控制實例的IP地址。 有關詳細資訊，請參閱[執行實例](#execution-instance)。

1. 指定執行實例要使用的恢複方法。

   要恢復的資料由執行實例轉發到控制實例，以添加到事務消息和事件存檔。

   ![](assets/messagecenter_create_extaccount_007.png)

   資料收集是透過使用HTTP/HTTPS存取的Web服務，或透過Federated Data Access(FDA)模組進行。

   >[!NOTE]
   >
   >請注意，在使用FDA over HTTP時，僅支援使用PostgreSQL資料庫的執行實例。 不支援MSSQL或Oracle資料庫。

   如果控制實例可以直接訪問執行實例的資料庫，則建議使用第二種方法。 否則，請選擇Web服務訪問。 要指定的FDA帳戶與與在控制實例上建立的各種執行實例的資料庫的連接一致。

   ![](assets/messagecenter_create_extaccount_008.png)

   有關聯合資料存取(FDA)的詳細資訊，請參閱[訪問外部資料庫](../../installation/using/about-fda.md)。

1. 按一下&#x200B;**[!UICONTROL Test the connection]**&#x200B;確保控制實例和執行實例已連結。

   ![](assets/messagecenter_create_extaccount_006.png)

1. 每個執行例項都必須與識別碼相關聯。 此標識符可以通過使用部署嚮導（請參閱[標識執行實例](../../message-center/using/identifying-execution-instances.md)）手動分配給每個執行實例，也可以通過按一下控制實例的&#x200B;**初始化連接**&#x200B;按鈕自動分配給每個執行實例。

   ![](assets/messagecenter_create_extaccount_006bis.png)

## 執行實例{#execution-instance}

為了使控制實例能夠連接到執行實例而不需要提供口令，只需在&#x200B;**消息中心**&#x200B;訪問權限部分中輸入控制實例的IP地址。 但是，空密碼預設為禁止。

要使用空口令，請轉至執行實例並定義一個安全區，該安全區限制為發送事件的資訊系統的IP地址。 此安全區必須允許空密碼並接受`<identifier> / <password>`類型連接。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

>[!NOTE]
>
>當多個控制例項使用執行例項時，資料可依資料夾和運算子來劃分。 有關詳細資訊，請參閱[使用多個控制實例](#using-several-control-instances)。

1. 轉至執行實例(**[!UICONTROL Administration > Access management > Operators]**)中的operator資料夾。
1. 選擇&#x200B;**消息中心**&#x200B;代理。

   ![](assets/messagecenter_operator_001.png)

1. 選擇&#x200B;**[!UICONTROL Edit]**&#x200B;標籤，按一下&#x200B;**[!UICONTROL Access rights]** ，然後按一下&#x200B;**[!UICONTROL Edit the access parameters...]**&#x200B;連結。

   ![](assets/messagecenter_operator_002.png)

1. 在&#x200B;**[!UICONTROL Access settings]**&#x200B;窗口中，按一下&#x200B;**[!UICONTROL Add a trusted IP mask]**&#x200B;連結並添加控制實例的IP地址。

   ![](assets/messagecenter_operator_003.png)

## 使用多個控制實例{#using-several-control-instances}

您可以與各種控制實例共用執行群集。 此類型的體系結構需要以下配置。

例如，如果您的公司管理兩個品牌，每個品牌都有其自己的控制例項：**控制1**&#x200B;和&#x200B;**控制2**。 還使用兩個執行例項。 您需要為每個控制實例輸入不同的消息中心運算子：用於&#x200B;**Control 1**&#x200B;實例的&#x200B;**mc1**&#x200B;運算子和用於&#x200B;**Control 2**&#x200B;實例的&#x200B;**mc2**&#x200B;運算子。

在所有執行實例的樹中，為每個運算子建立一個資料夾（**資料夾1**&#x200B;和&#x200B;**資料夾2**），並限制每個運算子對其資料夾的資料存取。

### 配置控制實例{#configuring-control-instances}

1. 在&#x200B;**Control 1**&#x200B;控制實例中，為每個執行實例建立一個外部帳戶，並在每個外部帳戶中輸入&#x200B;**mc1**&#x200B;運算子。 此後將在所有執行實例上建立&#x200B;**mc1**&#x200B;運算子（請參閱[配置執行實例](#configuring-execution-instances)）。

   ![](assets/messagecenter_multi_control_1.png)

1. 在&#x200B;**Control 2**&#x200B;控制實例中，為每個執行實例建立一個外部帳戶，並在每個外部帳戶中輸入&#x200B;**mc2**&#x200B;運算子。 此後將在所有執行實例上建立&#x200B;**mc2**&#x200B;運算子（請參閱[配置執行實例](#configuring-execution-instances)）。

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >有關配置控制實例的詳細資訊，請參閱[Control instance](#control-instance)。

### 配置執行實例{#configuring-execution-instances}

要使用多個控制實例，必須對ALL執行實例執行此配置。

1. 在&#x200B;**[!UICONTROL Administration > Production > Message Center]**&#x200B;節點中，為每個運算子建立一個資料夾：**資料夾1**&#x200B;和&#x200B;**資料夾2**。 有關建立資料夾和視圖的詳細資訊，請參閱[此頁](../../platform/using/access-management-folders.md)。

   ![](assets/messagecenter_multi_control_3.png)

1. 通過複製預設提供的消息中心運算子(**mc5/>)，建立** mc1 **和** mc2 **運算子。**&#x200B;有關建立運算子的詳細資訊，請參閱[本節](../../platform/using/access-management-operators.md)。

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** 和 **mc2** 運營商必 **[!UICONTROL Message Center execution]** 須擁有權限，而且無法訪問Adobe Campaign客戶機控制台。操作員必須始終與安全區域連結。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

1. 對於每個運算子，選中&#x200B;**[!UICONTROL Restrict to information found in sub-folders of]**&#x200B;框，並為&#x200B;**mc1**&#x200B;運算子選擇相關資料夾（****&#x200B;資料夾1和&#x200B;**mc2**&#x200B;運算子的&#x200B;**資料夾2**）。

   ![](assets/messagecenter_multi_control_5.png)

1. 為每個操作員授予其資料夾的讀寫權限。 要執行此操作，請按一下右鍵資料夾並選擇&#x200B;**[!UICONTROL Properties]**。 然後，選擇&#x200B;**[!UICONTROL Security]**&#x200B;頁籤並添加相關運算子(**mc1**（**資料夾1**）和&#x200B;**mc2**（**資料夾2**）。 請確定&#x200B;**[!UICONTROL Read/Write data]**&#x200B;方塊已勾選。

   ![](assets/messagecenter_multi_control_6.png)

