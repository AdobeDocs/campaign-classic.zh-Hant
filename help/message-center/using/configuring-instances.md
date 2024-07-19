---
product: campaign
title: 設定執行個體
description: 瞭解如何在Adobe Campaign Classic中設定異動訊息控制和執行例項
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1236'
ht-degree: 1%

---


# 設定執行個體 {#creating-a-shared-connection}



若要使用異動訊息傳送功能，您必須設定控制和執行例項。 您可以使用下列其中一項：
* [一個控制項執行個體](#control-instance)與一或多個執行個體相關聯
* [數個控制執行個體](#using-several-control-instances)與數個執行個體相關聯

>[!IMPORTANT]
>
>結構描述擴充功能影響[訊息中心技術工作流程](../../message-center/using/additional-configurations.md#technical-workflows)在控制項或執行執行例項上使用的資源，這些執行個體需要在「異動訊息」模組使用的其他執行個體上重複。

您也需要指定執行例項並將其連線到控制例項。

本節將說明設定及連線控制項及執行例項所需的所有步驟。

>[!IMPORTANT]
>
>控制例項和執行例項必須安裝在不同的電腦上。 他們無法共用相同的Campaign執行個體。

## 設定控制例項 {#control-instance}

若要連線控制執行個體和執行執行個體，您必須先在控制執行個體&#x200B;**上建立並設定&#x200B;**[!UICONTROL Execution instance]**型別的外部帳戶**。 因此，一旦[發佈](../../message-center/using/publishing-message-templates.md#template-publication)，即可將異動訊息範本部署至執行個體。

如果您使用數個執行例項，則必須建立與執行例項相同數量的外部帳戶。

>[!NOTE]
>
>當多個控制例項使用執行例項時，資料可以依資料夾和運運算元劃分。 如需詳細資訊，請參閱[使用數個控制項執行個體](#using-several-control-instances)。

### 建立外部帳戶

>[!NOTE]
>
>下列步驟必須在控制項執行個體&#x200B;**上執行**。

若要建立&#x200B;**[!UICONTROL Execution instance]**&#x200B;型別外部帳戶，請套用下列專案：

1. 前往&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;資料夾。
1. 選取其中一個隨Adobe Campaign提供的現成執行個體型別外部帳戶，按一下滑鼠右鍵並選擇&#x200B;**[!UICONTROL Duplicate]** 。

   ![](assets/messagecenter_create_extaccount_001.png)

1. 根據您的需求變更標籤。

   ![](assets/messagecenter_create_extaccount_002.png)

1. 選取&#x200B;**[!UICONTROL Enabled]**&#x200B;選項，讓外部帳戶可運作。

   ![](assets/messagecenter_create_extaccount_003.png)

1. 指定安裝執行例項的伺服器位址。

   ![](assets/messagecenter_create_extaccount_004.png)

1. 帳戶必須符合操作員資料夾中定義的訊息中心代理程式。 依預設，Adobe Campaign提供的現成帳戶為&#x200B;**[!UICONTROL mc]** 。

   ![](assets/messagecenter_create_extaccount_005.png)

1. 輸入運運算元資料夾中定義的帳戶密碼。

   >[!NOTE]
   >
   >若要避免每次登入執行個體時都輸入密碼，您可以在執行個體中指定控制執行個體的IP位址。 如需詳細資訊，請參閱[設定執行個體](#execution-instance)。

1. 指定執行例項要使用的復原方法。 要復原的資料會由執行例項轉送至控制執行個體，以新增至異動訊息和事件封存檔。

   ![](assets/messagecenter_create_extaccount_007.png)

   資料收集會透過使用HTTP/HTTPS存取的網站服務或同盟資料存取(FDA)模組進行。

   >[!NOTE]
   >
   >請注意，使用FDA over HTTP時，僅支援使用PostgreSQL資料庫的執行例項。 不支援MSSQL或Oracle資料庫。

   如果控制執行個體可直接存取執行個體的資料庫，則建議使用第二個方法(FDA)。 如果沒有，請選擇Web服務存取。 要指定的FDA帳戶與連線到在控制執行個體上建立的各種執行個體資料庫的時間一致。

   ![](assets/messagecenter_create_extaccount_008.png)

   如需同盟資料存取(FDA)的詳細資訊，請參閱[本節](../../installation/using/about-fda.md)。

1. 按一下&#x200B;**[!UICONTROL Test the connection]**&#x200B;以確定控制項執行個體與執行個體已連結。

   ![](assets/messagecenter_create_extaccount_006.png)

使用多個執行例項時，重複這些步驟可建立與執行例項數量相同的外部帳戶。

### 識別執行個體 {#identifying-execution-instances}

每個執行例項都必須與唯一識別碼相關聯，以區分在控制例項上檢視每個執行例項時的歷史記錄。

此識別碼可手動歸因於每個執行執行個體&#x200B;****。 在此情況下，必須在每個執行執行例項&#x200B;**上執行此步驟**。 要執行此操作，請使用部署精靈，如下所述：

1. 在執行例項上開啟部署精靈。
1. 前往&#x200B;**[!UICONTROL Message Center]**&#x200B;視窗。
1. 將您選擇的識別碼指派給執行個體。

   ![](assets/messagecenter_id_execinstance_001.png)

1. 對每個執行例項重複上述步驟。

識別碼也可以是&#x200B;**自動**&#x200B;歸因。 若要這麼做，請移至&#x200B;**控制項執行個體**，然後按一下&#x200B;**[!UICONTROL Initialize connection]**&#x200B;按鈕。

![](assets/messagecenter_create_extaccount_006bis.png)

## 設定執行例項 {#execution-instance}

>[!NOTE]
>
>下列步驟必須在執行執行個體&#x200B;**上執行**。

若要將執行例項連線至控制例項，請遵循下列步驟。

若要讓控制項執行個體能夠連線到執行個體而不需要提供密碼，只要在&#x200B;**訊息中心**&#x200B;存取許可權區段中輸入控制項執行個體的IP位址即可。 不過，預設會禁止空白密碼。

若要使用空白密碼，請移至執行例項，並定義一個安全區域，其限製為傳送事件的資訊系統的IP位址。 此安全性區域必須允許空白密碼並接受`<identifier> / <password>`型別連線。 如需詳細資訊，請參閱[本章節](../../installation/using/security-zones.md)。

>[!NOTE]
>
>當多個控制例項使用執行例項時，資料可以依資料夾和運運算元劃分。 如需詳細資訊，請參閱[使用數個控制項執行個體](#using-several-control-instances)。

1. 在執行例項上，移至運運算元資料夾( **[!UICONTROL Administration > Access management > Operators]** )。
1. 選取&#x200B;**訊息中心**&#x200B;代理程式。

   ![](assets/messagecenter_operator_001.png)

1. 選取&#x200B;**[!UICONTROL Edit]**&#x200B;標籤，按一下&#x200B;**[!UICONTROL Access rights]**，然後按一下&#x200B;**[!UICONTROL Edit the access parameters...]**&#x200B;連結。

   ![](assets/messagecenter_operator_002.png)

1. 在&#x200B;**[!UICONTROL Access settings]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Add a trusted IP mask]**&#x200B;連結並新增控制執行個體的IP位址。

   ![](assets/messagecenter_operator_003.png)

使用數個執行例項時，請對每個執行例項重複這些步驟。

## 使用數個控制例項 {#using-several-control-instances}

您可以與各種控制執行處理共用執行叢集。 此型別的架構需要下列設定。

例如，假設您的公司管理兩個品牌，每個品牌都有自己的控制例項： **控制項1**&#x200B;和&#x200B;**控制項2**。 也會使用兩個執行例項。 您必須為每個控制項執行個體輸入不同的Message Center運運算元： **控制項1**&#x200B;執行個體的&#x200B;**mc1**&#x200B;運運算元，以及&#x200B;**控制項2**&#x200B;執行個體的&#x200B;**mc2**&#x200B;運運算元。

在所有執行例項的樹狀結構中，為每個運運算元建立一個資料夾（**資料夾1**&#x200B;和&#x200B;**資料夾2**），並限制每個運運算元的資料存取其資料夾。

### 設定控制例項 {#configuring-control-instances}

>[!NOTE]
>
>下列步驟必須在控制項執行個體&#x200B;**上執行**。

1. 在&#x200B;**Control 1**&#x200B;控制項執行個體上，為每個執行個體建立一個外部帳戶，並在每個外部帳戶中輸入&#x200B;**mc1**&#x200B;運運算元。 之後將在所有執行例項上建立&#x200B;**mc1**&#x200B;運運算元（請參閱[設定執行例項](#configuring-execution-instances)）。

   ![](assets/messagecenter_multi_control_1.png)

1. 在&#x200B;**Control 2**&#x200B;控制項執行個體上，為每個執行個體建立一個外部帳戶，並在每個外部帳戶中輸入&#x200B;**mc2**&#x200B;運運算元。 之後將在所有執行例項上建立&#x200B;**mc2**&#x200B;運運算元（請參閱[設定執行例項](#configuring-execution-instances)）。

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >如需設定控制項執行個體的詳細資訊，請參閱[本節](#control-instance)。

### 設定執行個體 {#configuring-execution-instances}

>[!NOTE]
>
>下列步驟必須在執行例項&#x200B;**上執行**。

若要使用數個控制例項，必須在所有執行例項上執行此設定。

1. 在&#x200B;**[!UICONTROL Administration > Production > Message Center]**&#x200B;節點中為每個運運算元建立一個資料夾： **資料夾1**&#x200B;和&#x200B;**資料夾2**。 有關建立資料夾和檢視的詳細資訊，請參閱[此頁面](../../platform/using/access-management-folders.md)。

   ![](assets/messagecenter_multi_control_3.png)

1. 複製預設提供的Message Center運運算元(**mc**)，以建立&#x200B;**mc1**&#x200B;和&#x200B;**mc2**&#x200B;運運算元。 如需建立運運算元的詳細資訊，請參閱[本節](../../platform/using/access-management-operators.md)。

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1**&#x200B;和&#x200B;**mc2**&#x200B;操作者必須擁有&#x200B;**[!UICONTROL Message Center execution]**&#x200B;許可權，而且他們無法存取Adobe Campaign使用者端主控台。 運運算元必須一律連結至安全區域。 如需詳細資訊，請參閱[本章節](../../installation/using/security-zones.md)。

1. 針對每個運運算元，核取「**[!UICONTROL Restrict to information found in sub-folders of]**」方塊，然後選取相關的資料夾（**mc1**&#x200B;運運算元為&#x200B;**資料夾1**，**mc2**&#x200B;運運算元為&#x200B;**資料夾2**）。

   ![](assets/messagecenter_multi_control_5.png)

1. 授予每個操作員其資料夾的讀寫許可權。 若要這麼做，請以滑鼠右鍵按一下資料夾，然後選取「**[!UICONTROL Properties]**」。 然後選取「**[!UICONTROL Security]**」索引標籤並新增相關運運算元（**資料夾1**&#x200B;為&#x200B;**mc1**，**資料夾2**&#x200B;為&#x200B;**mc2**）。 請確定已核取&#x200B;**[!UICONTROL Read/Write data]**&#x200B;方塊。

   ![](assets/messagecenter_multi_control_6.png)
