---
solution: Campaign Classic
product: campaign
title: 在Campaign中安裝中間採購伺服器
description: 本節詳細說明在Campaign中安裝和配置中間採購伺服器的情況
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 1%

---

# 中間來源伺服器{#mid-sourcing-server}

本節詳細說明中間採購伺服器的安裝和配置，以及使第三方能夠以&#x200B;**mid-sourcing**&#x200B;模式發送消息的實例的部署。

「中間採購」體系結構顯示在[中間採購部署](../../installation/using/mid-sourcing-deployment.md)中。

安裝中間採購伺服器的過程與以正常方式安裝伺服器的過程相同（請參閱標準配置）。 它是獨立實例，具有自己的資料庫，可用於運行傳送。 簡單來說，它包含額外的設定，可讓遠端執行個體在中端採購模式中透過它執行傳送。

>[!CAUTION]
>
>在設定中間採購伺服器並首次運行[sync工作流](../../workflow/using/about-technical-workflows.md)後，請確保不更新中間採購外部帳戶的內部名稱。

## 安裝和配置實例{#steps-for-installing-and-configuring-an-instance}的步驟

### 安裝和配置實例{#prerequisites-for-installing-and-configuring-an-instance}的先決條件

* 應用程式伺服器上的JDK。
* 訪問應用程式伺服器上的資料庫伺服器。
* 防火牆配置為開啟HTTP(80)或HTTPS(443)埠至中端源伺服器。

以下過程詳細說明了使用單個中間採購伺服器的配置。 也可使用多部伺服器。 同樣地，您也可以從內部設定傳送特定訊息（例如工作流程通知）。

### 安裝和配置用於中間採購部署的應用程式伺服器{#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

安裝程式與獨立實例的安裝程式相同。 請參閱[安裝和配置（單機）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-)。

但是，您必須套用下列項目：

* 在步驟&#x200B;**5**&#x200B;中，您必須停用&#x200B;**mta**（傳送）和&#x200B;**inMail**（彈回郵件）模組。 但是，**wfserver**（工作流）模組必須保持激活狀態。

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

* 不需要步驟&#x200B;**6**、**9**&#x200B;和&#x200B;**10**。
* 在步驟&#x200B;**12**&#x200B;和&#x200B;**13**&#x200B;期間，您需要在連接URL中指示8080埠（因為控制台直接與Tomcat通信，而不是通過Web伺服器）。 URL會變成[http://console.campaign.net:8080](http://console.campaign.net)。 在步驟&#x200B;**13**&#x200B;期間，選擇&#x200B;**[!UICONTROL Issue towards Mid-sourcing]**&#x200B;軟體包以及要安裝的軟體包。

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >技術傳送的預設傳送路由會自動取代為透過中部來源的電子郵件傳送。

### 安裝和配置中間採購伺服器{#installing-and-configuring-the-mid-sourcing-server}

在客戶端控制台中，找到使用mid-sourcing **mid-sourcing帳戶的**&#x200B;電子郵件路由（在&#x200B;**/Administration/External accounts/**&#x200B;資料夾中）。 將代管中間採購伺服器的伺服器提供商提供的資訊填充到伺服器&#x200B;**、**&#x200B;帳戶&#x200B;**、**&#x200B;密碼&#x200B;**和**&#x200B;鏡像頁URL **設定中。**&#x200B;測試連接。

>[!NOTE]
>
>**mid-sourcingEmitter**&#x200B;選項會建立兩個&#x200B;**Mid-sourcing**&#x200B;工作流程。 此程式預設每1小時20分鐘執行一次，並收集中端來源伺服器上的傳送資訊。

## 部署中間採購伺服器{#deploying-a-mid-sourcing-server}

1. 安裝應用程式伺服器：

   >[!CAUTION]
   >
   >如果您安裝中間採購伺服器並想要安裝額外的Adobe Campaign模組，我們建議使用傳送模組，而非促銷活動模組。

   按照與標準部署相同的步驟操作，僅選擇&#x200B;**[!UICONTROL Mid-sourcing platform]**&#x200B;選項。

   ![](assets/s_ncs_install_midsourcing01.png)

1. 用於在中間採購模式下接收的配置

   設定提交帳戶密碼：在&#x200B;**/Mid-sourcing/Access Management/Operators/**&#x200B;資料夾中，遠端例項在中端來源模式中用於提交。 ****&#x200B;您必須為此運算子設定密碼，並將其提供給提交實例的管理員。

   **中間採購平台**&#x200B;選項建立用於儲存已提交交貨的預設資料夾和執行提交的預設運算子。

## 多路復用中間採購伺服器{#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>僅內部部署環境支援多路復用。

多個提交例項可共用中間來源補充例項。 這些例項中的每個例項都必須與中間採購資料庫中的運算子相關聯。 要在中間採購伺服器上建立第二個帳戶，請執行以下操作：

1. 在&#x200B;**[!UICONTROL Mid-sourcing > Deliveries]**&#x200B;節點中建立一個與預設中間採購帳戶關聯的資料夾(例如：prod)。
1. 在&#x200B;**[!UICONTROL Mid-sourcing > Deliveries]**&#x200B;節點中建立與帳戶同名的資料夾(例如：acception_test)。

   ![](assets/mid_recette_account.png)

1. 在&#x200B;**[!UICONTROL Mid-sourcing > Access Management > Operators]**&#x200B;中，建立新帳戶。

   ![](assets/mid_recette_user_create.png)

1. 在&#x200B;**[!UICONTROL Access rights]**&#x200B;標籤中，為此運算子提供&#x200B;**中間採購提交**&#x200B;群組的權利。 **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**&#x200B;中提供此訪問權限。

   ![](assets/mid_recette_user_rights.png)

1. 選擇&#x200B;**[!UICONTROL Restrict to data in the sub-folders of]**&#x200B;選項，然後選擇交貨資料夾，以將此運算子限制在中間採購交貨資料夾。

   ![](assets/mid_recette_user_restrictions.png)

1. 使用以下命令重新啟動Web模組：**nlserver重新啟動web**。

必須更改serverConf.xml檔案中的mid-sourcing伺服器設定。 必須在現有行的「IP位址相關性管理」區段中新增下列行：

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

「@name」屬性必須遵守下列規則：

**&#39;marketing_account_operator_name&#39;。&#39;affinity_name&#39;。&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39;與在中間來源補充實例中聲明的中間來源補充帳戶的內部名稱相關。

&#39;affinity_name&#39;與指定給相似性的任意名稱相關。 此名稱必須是唯一的。 授權字元為`[a-z]``[A-Z]``[0-9]`。 其目標是宣告一組公用IP位址。

&#39;affinity_group&#39;與每個傳送中使用之目標映射中宣告的子相似性相關。 包含&#39;.&#39;的最後一部分 如果沒有子相似性，則會忽略。 授權字元為`[a-z]``[A-Z]``[0-9]`。

您必須停止並重新啟動伺服器，才能考慮修改。

## 在中間採購伺服器{#configuring-tracking-on-a-mid-sourcing-server}上配置跟蹤

**配置中間採購伺服器**

1. 前往&#39;operators&#39;並選取運算子&#x200B;**[!UICONTROL mid]**。
1. 在&#x200B;**[!UICONTROL Frontal servers]**&#x200B;標籤中，輸入追蹤伺服器連線參數。

   若要建立追蹤例項，請輸入追蹤伺服器的URL、追蹤伺服器內部帳戶密碼及例項名稱、其密碼及與其關聯的DNS遮罩。

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. 輸入連接參數後，按一下&#x200B;**[!UICONTROL Confirm the configuration]**。
1. 如有必要，請指定儲存傳送中影像的位置。 若要這麼做，請從下拉式清單中選取其中一種出版模式。

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   如果您選擇&#x200B;**[!UICONTROL Tracking server(s)]**&#x200B;選項，則影像會複製到中間採購伺服器。

**設定客戶平台**

1. 轉至外部中間採購工藝路線帳戶。
1. 在&#x200B;**[!UICONTROL Mid-Sourcing]**&#x200B;標籤中，指定中間採購伺服器連接參數。

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. 按一下&#x200B;**[!UICONTROL Test the connection]**&#x200B;確認您的設定。
1. 宣告中間採購伺服器上參考的追蹤例項：

   按一下連結&#x200B;**[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   指定追蹤例項的名稱，然後確認與追蹤伺服器的連線。

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

如果消息的傳送將由多個中部源伺服器管理，請選擇&#x200B;**[!UICONTROL Routing with alternating mid-sourcing accounts]**&#x200B;選項並指定不同的伺服器。

![](assets/s_ncs_install_midsourcing_tracking04.png)
