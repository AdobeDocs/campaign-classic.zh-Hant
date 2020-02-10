---
title: 在Adobe Campaign Classic中安裝中端來源補充伺服器
description: 本節詳細說明在Adobe Campaign Classic中安裝和設定中端來源伺服器。
page-status-flag: never-activated
uuid: 9b891a64-d75e-44d2-8de2-17334e1b8dca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 34ee3d99-4ffb-4279-b994-5ab7abc7cf06
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# 中端採購伺服器{#mid-sourcing-server}

本節詳細說明中間採購伺服器的安裝和配置，以及使第三方能夠在中間採購模式下發送消息的 **實例的部署** 。

「中間採購」架構是在中間採購部 [署中呈現的](../../installation/using/mid-sourcing-deployment.md)。

安裝中間採購伺服器的過程與以正常方式安裝伺服器的過程相同（請參閱標準配置）。 它是獨立實例，具有自己的資料庫，可用於運行傳送。 簡單來說，它包含額外的設定，可讓遠端執行個體在中端採購模式中透過它執行傳送。

## 安裝和配置實例的步驟 {#steps-for-installing-and-configuring-an-instance}

### 安裝和配置實例的先決條件 {#prerequisites-for-installing-and-configuring-an-instance}

* 應用程式伺服器上的JDK。
* 訪問應用程式伺服器上的資料庫伺服器。
* 防火牆配置為開啟HTTP(80)或HTTPS(443)埠至中端源伺服器。

以下過程詳細說明了使用單個中間採購伺服器的配置。 也可使用多部伺服器。 同樣地，您也可以從內部設定傳送特定訊息（例如工作流程通知）。

### 安裝和配置應用程式伺服器以進行中間採購部署 {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

安裝程式與獨立實例的安裝程式相同。 請參閱 [安裝和配置（單機）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-)。

但是，您必須套用下列項目：

* 在步 **驟5**，您必須停用 **mta** （傳送）和 **inMail** （彈回郵件）模組。 但 **wfserver** （工作流程）模組必須保持啟用狀態。

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

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

* 步 **驟6**、 **9****和** 10不需要。
* 在步驟 **12** 和 **13期間**，您需要在連接URL中指示8080埠（因為控制台直接與Tomcat通信，而不是通過Web伺服器）。 URL變為 [http://console.campaign.net:8080](http://console.campaign.net)。 在步驟 **13期間**，請選 **[!UICONTROL Issue towards Mid-sourcing]** 擇軟體包以及要安裝的軟體包。

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >技術傳送的預設傳送路由會自動取代為透過中部來源的電子郵件傳送。

### 安裝和配置中間採購伺服器 {#installing-and-configuring-the-mid-sourcing-server}

在客戶端控制台中，使用中 **間採購中** (在 **** /Administration/External accounts/資料夾中)找到電子郵件路由。 將伺服器 **、帳戶、密碼和** Mirror page URL **URL設定的URL********** ，填入托管mid-sourcing伺服器的伺服器提供商提供的資訊。 測試連接。

>[!NOTE]
>
>mid-sourcingEmitter **選項可建立兩** 個Mid-sourcing工作流程 **** 。 此程式預設每1小時20分鐘執行一次，並收集中端來源伺服器上的傳送資訊。

## 部署中端採購伺服器 {#deploying-a-mid-sourcing-server}

1. 安裝應用程式伺服器：

   >[!CAUTION]
   >
   >如果您安裝中間採購伺服器並想要安裝額外的Adobe Campaign模組，建議您使用「傳送」模組，而非「促銷活動」模組。

   請遵循與標準部署相同的步驟，僅選擇選 **[!UICONTROL Mid-sourcing platform]** 項。

   ![](assets/s_ncs_install_midsourcing01.png)

1. 用於在中間採購模式下接收的配置

   設定提交帳戶密碼：在 **/Mid-sourcing/Access Management/Operators/****** /資料夾中，遠端例項在中端採購模式中用於提交作業。 您必須為此運算子設定密碼，並將其提供給提交實例的管理員。

   Mid- **sourcing platform** （中部採購平台）選項建立用於儲存已提交交貨的預設資料夾以及執行提交的預設運算子。

## 多路傳輸中間採購伺服器 {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>僅內部部署環境支援多路復用。

多個提交例項可共用中間來源補充例項。 這些例項中的每個例項都必須與中間採購資料庫中的運算子相關聯。 要在中間採購伺服器上建立第二個帳戶，請執行以下操作：

1. 在節點中建立 **[!UICONTROL Mid-sourcing > Deliveries]** 與預設中間採購帳戶關聯的資料夾(例如：prod)。
1. 在與帳戶同名 **[!UICONTROL Mid-sourcing > Deliveries]** 的節點中建立資料夾(例如：acception_test)。

   ![](assets/mid_recette_account.png)

1. 在 **[!UICONTROL Mid-sourcing > Access Management > Operators]**&#x200B;中，建立新帳戶。

   ![](assets/mid_recette_user_create.png)

1. 在標籤 **[!UICONTROL Access rights]** 中，為此運算子提供「中部來源 **提交」群組的權利** 。 此訪問權限在中可用 **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**。

   ![](assets/mid_recette_user_rights.png)

1. 選擇選 **[!UICONTROL Restrict to data in the sub-folders of]** 項並選擇交貨資料夾，以將此運算子限制在中間來源補充交貨資料夾。

   ![](assets/mid_recette_user_restrictions.png)

1. 使用以下命令重新啟動Web模組：無 **伺服器重新啟動Web**。

必須更改serverConf.xml檔案中的mid-sourcing伺服器設定。 必須在現有行的「IP位址相關性管理」區段中新增下列行：

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

「@name」屬性必須遵守下列規則：

**&#39;marketing_account_operator_name&#39;。&#39;affinity_name&#39;。&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39;與在中間來源補充實例中聲明的中間來源補充帳戶的內部名稱相關。

&#39;affinity_name&#39;與指定給相似性的任意名稱相關。 此名稱必須是唯一的。 授權字元為 `[a-z]``[A-Z]``[0-9]`。 其目標是宣告一組公用IP位址。

&#39;affinity_group&#39;與每個傳送中使用之目標映射中宣告的子相似性相關。 包含&#39;.&#39;的最後一部分 如果沒有子相似性，則會忽略。 授權字元為 `[a-z]``[A-Z]``[0-9]`。

您必須停止並重新啟動伺服器，才能考慮修改。

## 在中端採購伺服器上設定追蹤 {#configuring-tracking-on-a-mid-sourcing-server}

**配置中間採購伺服器**

1. 前往&#39;operators&#39;並選取運算子 **[!UICONTROL mid]**。
1. 在標籤 **[!UICONTROL Frontal servers]** 中，輸入追蹤伺服器連線參數。

   若要建立追蹤例項，請輸入追蹤伺服器的URL、追蹤伺服器內部帳戶密碼及例項名稱、其密碼及與其關聯的DNS遮罩。

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. 輸入連接參數後，按一下 **[!UICONTROL Confirm the configuration]**。
1. 如有必要，請指定儲存傳送中影像的位置。 若要這麼做，請從下拉式清單中選取其中一種出版模式。

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   如果您選擇 **[!UICONTROL Tracking server(s)]** 此選項，影像將會複製到中間採購伺服器。

**設定客戶平台**

1. 轉至外部中間採購工藝路線帳戶。
1. 在頁籤 **[!UICONTROL Mid-Sourcing]** 中，指定中間採購伺服器連接參數。

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. 按一下以確認您的設定 **[!UICONTROL Test the connection]**。
1. 宣告中間採購伺服器上參考的追蹤例項：

   按一下連結 **[!UICONTROL Use this platform as a platform to access the tracking servers]**,

   指定追蹤例項的名稱，然後確認與追蹤伺服器的連線。

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

如果消息的傳送將由多個中部採購伺服器管理，請選擇該選項並指 **[!UICONTROL Routing with alternating mid-sourcing accounts]** 定不同的伺服器。

![](assets/s_ncs_install_midsourcing_tracking04.png)

