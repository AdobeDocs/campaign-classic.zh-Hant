---
product: campaign
title: 在Campaign中安裝中間來源伺服器
description: 本節詳細說明了Campaign中中間來源伺服器的安裝和設定
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 1%

---

# 中間來源伺服器{#mid-sourcing-server}



本節詳細說明中間來源伺服器的安裝和設定，以及讓第三方能夠傳送訊息的執行個體的部署 **中間來源** 模式。

「中間來源」架構在中介紹 [中間來源部署](../../installation/using/mid-sourcing-deployment.md).

安裝中間來源伺服器的程式與以正常方式安裝伺服器的程式相同（請參閱標準設定）。 它是一個獨立的執行個體，有自己的資料庫，可用於執行傳送。 簡言之，它包含額外的設定，可讓遠端執行個體在中間來源模式下透過它執行傳遞。

>[!CAUTION]
>
>設定中間來源伺服器後，以及 [同步工作流程](../../workflow/using/about-technical-workflows.md) 第一次執行時，請確定您沒有更新中間來源外部帳戶的內部名稱。

## 安裝和設定執行個體的步驟 {#steps-for-installing-and-configuring-an-instance}

### 安裝和設定執行個體的先決條件 {#prerequisites-for-installing-and-configuring-an-instance}

* 應用程式伺服器上的JDK。
* 存取應用程式伺服器上的資料庫伺服器。
* 防火牆已設定為開啟HTTP (80)或HTTPS (443)連線埠至中間來源伺服器。

以下程式詳細說明使用單一中間來源伺服器的設定。 也可以使用多個伺服器。 同樣地，您也可以從內部設定傳送特定訊息（例如工作流程通知）。

### 為中間來源部署安裝和設定應用程式伺服器 {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

安裝程式與獨立執行處理的安裝程式相同。 請參閱 [安裝和設定（單一電腦）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

不過，您必須套用下列內容：

* 在步驟 **5**，您必須停用 **mta** （傳遞）和 **inMail** （退回郵件）模組。 此 **wfserver** （工作流程）模組，但必須保持啟用狀態。

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="false"/>  
       <wfserver autoStart="true"/>  
       <inMail autoStart="false"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#enabling-processes)。

* 步驟 **6**， **9** 和 **10** 不需要。
* 步驟期間 **12** 和 **13**，您必須在連線URL中指定8080連線埠（因為主控台會直接與Tomcat通訊，而非透過網頁伺服器）。 URL會變成 `http://console.campaign.net:8080`. 步驟期間 **13**，選取 **[!UICONTROL Issue towards Mid-sourcing]** 封裝以及要安裝的封裝。

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >透過中間來源的電子郵件路由會自動取代技術傳遞的預設路由。

### 安裝和設定中間來源伺服器 {#installing-and-configuring-the-mid-sourcing-server}

從使用者端主控台，找到 **使用中間來源的電子郵件路由** 中間來源帳戶(在 **/管理/外部帳戶/** 資料夾)。 填入 **伺服器的URL**， **帳戶**， **密碼** 和 **映象頁面URL** 包含託管中間來源伺服器的伺服器提供者所提供資訊的設定。 測試連線。

>[!NOTE]
>
>此 **mid-sourcingEmitter** 選項會建立兩個 **中間來源** 工作流程。 此程式預設每1小時20分鐘執行一次，並收集中間來源伺服器上的傳遞資訊。

## 部署中間來源伺服器 {#deploying-a-mid-sourcing-server}

1. 安裝應用程式伺服器：

   >[!CAUTION]
   >
   >如果您安裝中間來源伺服器並想要安裝額外的Adobe Campaign模組，我們建議您使用傳送模組，而不要使用行銷活動模組。

   遵循與標準部署相同的程式，僅選取 **[!UICONTROL Mid-sourcing platform]** 選項。

   ![](assets/s_ncs_install_midsourcing01.png)

1. 用於中間來源模式接收的設定

   設定提交帳戶密碼：在 **/Mid-sourcing/Access Management/Operator/** 資料夾， **mid** 運運算元供遠端執行個體用於中間來源模式下的提交。 您必須為此運運算元設定密碼，並將其提供給提交執行個體的管理員。

   此 **中間來源平台** 選項會建立用來儲存已提交傳遞的預設資料夾，以及執行提交的預設運運算元。

## 多工處理中間來源伺服器 {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>僅內部部署環境支援多工處理。

多個提交執行個體可共用中間來源執行個體。 這些執行個體中的每一個都需要與中間來源資料庫中的運運算元相關聯。 若要在中間來源伺服器上建立第二個帳戶：

1. 在中建立資料夾 **[!UICONTROL Mid-sourcing > Deliveries]** 與預設中間來源帳戶相關聯的節點（例如：prod）。
1. 在中建立資料夾 **[!UICONTROL Mid-sourcing > Deliveries]** 與帳戶同名的節點（例如：acceptance_test）。

   ![](assets/mid_recette_account.png)

1. 在 **[!UICONTROL Mid-sourcing > Access Management > Operators]**，建立新帳戶。

   ![](assets/mid_recette_user_create.png)

1. 在 **[!UICONTROL Access rights]** 索引標籤中，賦予此運運算元以下專案的許可權： **中間來源提交** 群組。 此存取權適用於 **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. 選取 **[!UICONTROL Restrict to data in the sub-folders of]** 選項並選取傳遞資料夾，將此運運算元限制在中間來源傳遞資料夾。

   ![](assets/mid_recette_user_restrictions.png)

1. 使用下列命令重新啟動Web模組： **nlserver重新啟動web**.

您必須變更serverConf.xml檔案中的中間來源伺服器設定。 下列行必須新增至「與IP位址的相似性管理」現有行下方：

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

「@name」屬性必須符合下列規則：

**&#39;marketing_account_operator_name&#39;.&#39;affinity_name&#39;.&#39;affinity_group`**

「marketing_account_operator_name」與中間來源執行個體中宣告的中間來源帳戶的內部名稱相關。

&#39;affinity_name&#39;與指定給相似性的任意名稱相關。 此名稱必須是唯一的。 授權的字元包括 `[a-z]``[A-Z]``[0-9]`. 目標是宣告一組公用IP位址。

&#39;affinity_group&#39;會關聯每個傳遞中使用的目標對應中所宣告的子相似性。 最後一部分包含「。」 如果沒有Sub-affinity，則會忽略。 授權的字元包括 `[a-z]``[A-Z]``[0-9]`.

您必須停止然後重新啟動伺服器，才能將修改列入考量。

## 在中間來源伺服器上設定追蹤 {#configuring-tracking-on-a-mid-sourcing-server}

**設定中間來源伺服器**

1. 前往「運運算元」並選取運運算元 **[!UICONTROL mid]**.
1. 在 **[!UICONTROL Frontal servers]** 索引標籤中，輸入追蹤伺服器連線引數。

   若要建立追蹤執行個體，請輸入追蹤伺服器的URL、追蹤伺服器內部帳戶密碼、執行個體的名稱、密碼以及與之相關聯的DNS遮罩。

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. 輸入連線引數後，按一下 **[!UICONTROL Confirm the configuration]**.
1. 如有必要，請指定儲存傳遞中所含影像的位置。 若要這麼做，請從下拉式清單中選取其中一個發佈模式。

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   如果您選擇 **[!UICONTROL Tracking server(s)]** 選項，這些影像將會複製到中間來源伺服器上。

**設定客戶平台**

1. 前往外部中間來源路由帳戶。
1. 在 **[!UICONTROL Mid-Sourcing]** 索引標籤中，指定中間來源伺服器連線引數。

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. 按一下以確認您的設定 **[!UICONTROL Test the connection]**.
1. 宣告在中間來源伺服器上參考的追蹤執行個體：

   按一下連結 **[!UICONTROL Use this platform as a proxy to access the tracking servers]**，

   指定追蹤執行個體的名稱，然後確認與追蹤伺服器的連線。

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

如果訊息的傳遞將由多個中間來源伺服器管理，請選取「 」選項 **[!UICONTROL Routing with alternating mid-sourcing accounts]** 和指定不同的伺服器。

![](assets/s_ncs_install_midsourcing_tracking04.png)
