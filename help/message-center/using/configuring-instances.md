---
product: campaign
title: 設定執行個體
description: 了解如何在Adobe Campaign Classic中設定交易式訊息控制和執行例項。
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1222'
ht-degree: 1%

---


# 設定執行個體 {#creating-a-shared-connection}

![](../../assets/v7-only.svg)

若要使用交易式訊息功能，您需要設定控制和執行例項。 您可以使用下列任一項：
* [一個控制實例](#control-instance) 與一個或多個執行實例關聯
* [多個控制實例](#using-several-control-instances) 與多個執行實例關聯

>[!IMPORTANT]
>
>結構擴充功能影響 [訊息中心技術工作流程](../../message-center/using/additional-configurations.md#technical-workflows) 控制或執行例項必須複製到交易式訊息模組使用的其他例項上。

您還需要指定執行實例並將其連接到控制實例。

本節將說明設定及連接控制與執行例項所需的所有步驟。

>[!IMPORTANT]
>
>控制實例和執行實例必須安裝在不同的電腦上。 他們無法共用相同的Campaign執行個體。

## 配置控制實例 {#control-instance}

若要連接控制執行個體和執行執行個體，您必須先建立並設定 **[!UICONTROL Execution instance]** 類型外部帳戶 **在控制實例上**. 因此，一次 [已發佈](../../message-center/using/publishing-message-templates.md#template-publication)，交易式訊息範本可部署至執行例項。

如果您使用數個執行例項，您必須建立與執行例項數量一樣多的外部帳戶。

>[!NOTE]
>
>當多個控制實例使用執行實例時，資料可以按資料夾和運算子進行拆分。 有關詳細資訊，請參閱 [使用數個控制例項](#using-several-control-instances).

### 建立外部帳戶

>[!NOTE]
>
>必須執行下列步驟 **在控制實例上**.

若要建立 **[!UICONTROL Execution instance]** 輸入外部帳戶，套用下列項目：

1. 前往 **[!UICONTROL Administration > Platform > External accounts]** 檔案夾。
1. 選取其中一個執行執行個體類型隨Adobe Campaign提供且現成可用的外部帳戶，按一下滑鼠右鍵並選擇 **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. 根據您的需求變更標籤。

   ![](assets/messagecenter_create_extaccount_002.png)

1. 選取 **[!UICONTROL Enabled]** 讓外部帳戶可運作的選項。

   ![](assets/messagecenter_create_extaccount_003.png)

1. 指定安裝執行實例的伺服器的地址。

   ![](assets/messagecenter_create_extaccount_004.png)

1. 帳戶必須符合運算子資料夾中定義的訊息中心代理。 依預設，Adobe Campaign提供的現成可用帳戶為 **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. 輸入操作員資料夾中定義的帳戶密碼。

   >[!NOTE]
   >
   >為了避免在每次登錄到實例時輸入密碼，您可以指定執行實例中控制實例的IP地址。 有關詳細資訊，請參閱 [配置執行實例](#execution-instance).

1. 指定要由執行實例使用的恢複方法。 要恢復的資料由執行實例轉發到控制實例，以添加到交易式消息和事件存檔。

   ![](assets/messagecenter_create_extaccount_007.png)

   資料收集是透過使用HTTP/HTTPS存取的Web服務，或透過同盟資料存取(FDA)模組進行。

   >[!NOTE]
   >
   >請注意，使用FDA over HTTP時，僅支援使用PostgreSQL資料庫的執行例項。 不支援MSSQL或Oracle資料庫。

   如果控制例項可直接存取執行例項的資料庫，則建議使用第二種方法(FDA)。 否則，選擇Web服務訪問。 要指定的FDA帳戶與與控制執行個體上建立之各執行執行執行個體之資料庫的連線一致。

   ![](assets/messagecenter_create_extaccount_008.png)

   如需同盟資料存取(FDA)的詳細資訊，請參閱 [本節](../../installation/using/about-fda.md).

1. 按一下 **[!UICONTROL Test the connection]** 以確認控制執行個體和執行執行個體已連結。

   ![](assets/messagecenter_create_extaccount_006.png)

使用數個執行例項時，請重複這些步驟，建立與執行例項數一樣多的外部帳戶。

### 識別執行個體 {#identifying-execution-instances}

每個執行實例必須與唯一標識符相關聯，以便在控制實例上查看執行實例時區分它們的歷史記錄。

此識別碼可歸因於每個執行例項 **手動**. 在此情況下，必須執行此步驟 **每個執行實例**. 要執行此操作，請使用部署嚮導，如下所述：

1. 在執行實例上開啟部署嚮導。
1. 前往 **[!UICONTROL Message Center]** 窗口。
1. 將您選擇的識別碼指派給執行個體。

   ![](assets/messagecenter_id_execinstance_001.png)

1. 對每個執行例項重複上述步驟。

識別碼也可以是 **自動** 屬性。 若要這麼做，請前往 **控制實例**，然後按一下 **[!UICONTROL Initialize connection]** 按鈕。

![](assets/messagecenter_create_extaccount_006bis.png)

## 配置執行實例 {#execution-instance}

>[!NOTE]
>
>必須執行下列步驟 **執行實例上**.

要將執行實例連接到控制實例，請執行以下步驟。

為了使控制實例能夠連接到執行實例而不必提供密碼，只需在 **訊息中心** 存取權限區段。 但是，預設禁止空密碼。

要使用空口令，請轉至執行實例並定義一個安全區域，該安全區域僅限於傳送事件的資訊系統的IP地址。 此安全區域必須允許空密碼並接受 `<identifier> / <password>` 類型連接。 如需詳細資訊，請參閱[本章節](../../installation/using/security-zones.md)。

>[!NOTE]
>
>當多個控制實例使用執行實例時，資料可以按資料夾和運算子進行拆分。 有關詳細資訊，請參閱 [使用數個控制例項](#using-several-control-instances).

1. 在執行例項上，前往運算子資料夾( **[!UICONTROL Administration > Access management > Operators]** )。
1. 選取 **訊息中心** 代理。

   ![](assets/messagecenter_operator_001.png)

1. 選取 **[!UICONTROL Edit]** 按一下 **[!UICONTROL Access rights]** ，然後按一下 **[!UICONTROL Edit the access parameters...]** 連結。

   ![](assets/messagecenter_operator_002.png)

1. 在 **[!UICONTROL Access settings]** ，按一下 **[!UICONTROL Add a trusted IP mask]** 連結，並新增控制執行個體的IP位址。

   ![](assets/messagecenter_operator_003.png)

使用數個執行例項時，請對每個執行例項重複這些步驟。

## 使用數個控制例項 {#using-several-control-instances}

您可以與各種控制實例共用執行群集。 此類型的架構需要下列設定。

例如，假設您的公司管理兩個品牌，每個品牌都有其自己的控制例項： **控制1** 和 **控制2**. 也使用兩個執行例項。 您需要為每個控制實例輸入不同的消息中心運算子：an **mc1** 運算子 **控制1** 例項和 **mc2** 運算子 **控制2** 例項。

在所有執行實例的樹中，為每個運算子建立一個資料夾(**資料夾1** 和 **資料夾2**)，並限制每個運算子對其資料夾的資料存取權限。

### 配置控制實例 {#configuring-control-instances}

>[!NOTE]
>
>必須執行下列步驟 **在控制實例上**.

1. 在 **控制1** 控制實例，為每個執行實例建立一個外部帳戶，然後輸入 **mc1** 運算子。 此 **mc1** 運算子(請參閱 [配置執行實例](#configuring-execution-instances))。

   ![](assets/messagecenter_multi_control_1.png)

1. 在 **控制2** 控制實例，為每個執行實例建立一個外部帳戶，然後輸入 **mc2** 運算子。 此 **mc2** 運算子(請參閱 [配置執行實例](#configuring-execution-instances))。

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >如需設定控制執行個體的詳細資訊，請參閱 [本節](#control-instance).

### 配置執行實例 {#configuring-execution-instances}

>[!NOTE]
>
>必須執行下列步驟 **執行實例**.

若要使用數個控制執行個體，必須對ALL執行執行個體執行此設定。

1. 在 **[!UICONTROL Administration > Production > Message Center]** 節點： **資料夾1** 和 **資料夾2**. 有關建立資料夾和視圖的詳細資訊，請參閱 [本頁](../../platform/using/access-management-folders.md).

   ![](assets/messagecenter_multi_control_3.png)

1. 建立 **mc1** 和 **mc2** 運算子，複製預設提供的Message Center運算子(**mc**)。 有關建立運算子的詳細資訊，請參閱 [本節](../../platform/using/access-management-operators.md).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** 和 **mc2** 運算子必須 **[!UICONTROL Message Center execution]** 權限，且無法存取Adobe Campaign用戶端主控台。 運算子必須始終與安全區域連結。 如需詳細資訊，請參閱[本章節](../../installation/using/security-zones.md)。

1. 對於每個運算子，請檢查 **[!UICONTROL Restrict to information found in sub-folders of]** ，然後選取相關資料夾(**資料夾1** 針對 **mc1** 運算子和 **資料夾2** 針對 **mc2** 運算元)。

   ![](assets/messagecenter_multi_control_5.png)

1. 為每個運算子的資料夾授予讀取和寫入權限。 要執行此操作，請以滑鼠右鍵按一下資料夾並選取 **[!UICONTROL Properties]** . 然後選取 **[!UICONTROL Security]** 標籤，然後新增相關運算子(**mc1** for **資料夾1** 和 **mc2** for **資料夾2**)。 請確定 **[!UICONTROL Read/Write data]** 框。

   ![](assets/messagecenter_multi_control_6.png)
