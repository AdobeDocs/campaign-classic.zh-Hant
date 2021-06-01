---
product: campaign
title: 在Campaign中安裝中間來源伺服器
description: 本節詳細說明在Campaign中安裝和設定中間來源伺服器
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 1%

---

# 中間來源伺服器{#mid-sourcing-server}

本節詳細說明中間來源伺服器的安裝和配置，以及執行個體的部署，該執行個體可讓第三方在&#x200B;**中間來源**&#x200B;模式中傳送訊息。

「中間來源」架構顯示在[中間來源部署](../../installation/using/mid-sourcing-deployment.md)中。

安裝中間來源伺服器的程式與以正常方式安裝伺服器的程式相同（請參閱標準設定）。 它是獨立例項，其資料庫可用來執行傳送。 簡言之，它包含額外的設定，可讓遠端執行個體在中間來源模式中透過它執行傳送。

>[!CAUTION]
>
>設定中間來源伺服器且首次執行[同步工作流程](../../workflow/using/about-technical-workflows.md)後，請務必不要更新中間來源外部帳戶的內部名稱。

## 安裝和配置實例{#steps-for-installing-and-configuring-an-instance}的步驟

### 安裝和配置實例{#prerequisites-for-installing-and-configuring-an-instance}的先決條件

* 應用程式伺服器上的JDK。
* 訪問應用程式伺服器上的資料庫伺服器。
* 防火牆配置為向中間來源伺服器開啟HTTP(80)或HTTPS(443)埠。

下列程式詳細說明使用單一中間來源伺服器的設定。 也可以使用多台伺服器。 同樣，也可以從內部設定傳送特定訊息（例如工作流程通知）。

### 安裝和配置用於中間來源部署的應用程式伺服器{#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

安裝過程與獨立實例的安裝過程相同。 請參閱[安裝和配置（單台電腦）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-)。

但您必須套用下列項目：

* 在步驟&#x200B;**5**&#x200B;中，您必須停用&#x200B;**mta**（傳送）和&#x200B;**inMail**（退信郵件）模組。 但是，**wfserver**（工作流程）模組必須保持啟用狀態。

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

* 步驟&#x200B;**6**、**9**&#x200B;和&#x200B;**10**&#x200B;不是必需的。
* 在步驟&#x200B;**12**&#x200B;和&#x200B;**13**&#x200B;期間，您需要在連接URL中指示8080埠（因為控制台直接與Tomcat通信，而不是通過Web伺服器）。 URL會變成[http://console.campaign.net:8080](http://console.campaign.net)。 在步驟&#x200B;**13**&#x200B;期間，選擇&#x200B;**[!UICONTROL Issue towards Mid-sourcing]**&#x200B;包以及要安裝的包。

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >技術傳送的預設路由會自動取代為透過中間來源的電子郵件路由。

### 安裝和配置中間來源伺服器{#installing-and-configuring-the-mid-sourcing-server}

在用戶端主控台中，使用中間來源&#x200B;**中間來源帳戶找到**&#x200B;電子郵件路由（在&#x200B;**/管理/外部帳戶/**&#x200B;資料夾中）。 將伺服器&#x200B;**、**&#x200B;帳戶&#x200B;**、**&#x200B;密碼&#x200B;**和**&#x200B;鏡像頁面URL **的** URL填入為中間來源伺服器的伺服器供應商提供的資訊。 測試連線。

>[!NOTE]
>
>**mid-sourcingEmitter**&#x200B;選項會建立兩個&#x200B;**Mid-sourcing**&#x200B;工作流程。 此程式預設每1小時20分鐘執行一次，並在中間來源伺服器上收集傳送資訊。

## 部署中間來源伺服器{#deploying-a-mid-sourcing-server}

1. 安裝應用程式伺服器：

   >[!CAUTION]
   >
   >如果您安裝中間來源伺服器，且想要安裝額外的Adobe Campaign模組，建議您使用傳送模組，而非Campaign模組。

   請遵循與標準部署相同的步驟，僅選擇&#x200B;**[!UICONTROL Mid-sourcing platform]**&#x200B;選項。

   ![](assets/s_ncs_install_midsourcing01.png)

1. 在中間來源模式接收的配置

   設定提交帳戶密碼：在&#x200B;**/Mid-sourcing/Access Management/Operators/**&#x200B;資料夾中，遠端執行個體會在中間來源模式中用於提交作業。 ****&#x200B;您必須為此運算子設定密碼，並將其授予提交實例的管理員。

   **中間來源平台**&#x200B;選項建立用於儲存已提交傳送的預設資料夾，以及執行提交的預設運算子。

## 復用中間來源伺服器{#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>只有內部部署環境才支援多工處理。

中間來源例項可由多個提交例項共用。 每個執行個體都需與中間來源資料庫中的運算子相關聯。 要在中間來源伺服器上建立第二個帳戶：

1. 在&#x200B;**[!UICONTROL Mid-sourcing > Deliveries]**&#x200B;節點中建立與預設中間來源帳戶關聯的資料夾(例如：prod)。
1. 在&#x200B;**[!UICONTROL Mid-sourcing > Deliveries]**&#x200B;節點中建立與帳戶同名的資料夾(例如：acception_test)。

   ![](assets/mid_recette_account.png)

1. 在&#x200B;**[!UICONTROL Mid-sourcing > Access Management > Operators]**&#x200B;中，建立新帳戶。

   ![](assets/mid_recette_user_create.png)

1. 在&#x200B;**[!UICONTROL Access rights]**&#x200B;標籤中，為此運算子提供&#x200B;**中間來源提交**&#x200B;群組的權限。 此訪問權限在&#x200B;**[!UICONTROL Mid-sourcing > Access Management > Operator groups]**&#x200B;中可用。

   ![](assets/mid_recette_user_rights.png)

1. 選取&#x200B;**[!UICONTROL Restrict to data in the sub-folders of]**&#x200B;選項，然後選取傳送資料夾，以將此運算子限制在中間來源傳送資料夾。

   ![](assets/mid_recette_user_restrictions.png)

1. 使用以下命令重新啟動Web模組：**nlserver重新啟動web**。

您必須在serverConf.xml檔案中更改中間來源伺服器設定。 必須在現有行的「IP位址相關性管理」區段中新增下列行：

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

「@name」屬性必須符合下列規則：

**&#39;marketing_account_operator_name&#39;。&#39;affinity_name&#39;。&#39;affinity_group&#39;**

「marketing_account_operator_name」與在中間來源實例中聲明的中間來源帳戶的內部名稱相關。

「affinity_name」與為相關性指定的任意名稱相關。 此名稱必須是唯一的。 授權字元為`[a-z]``[A-Z]``[0-9]`。 其目的是要宣告一組公用IP位址。

「affinity_group」與每個傳送中使用的目標對應中宣告的子相關性相關。 最後一部分包括「。」 若沒有子相關性，則會忽略。 授權字元為`[a-z]``[A-Z]``[0-9]`。

您必須停止，然後重新啟動伺服器，才能考慮修改。

## 在中間來源伺服器{#configuring-tracking-on-a-mid-sourcing-server}上配置追蹤

**配置中間來源伺服器**

1. 轉到「operators」，然後選擇運算子&#x200B;**[!UICONTROL mid]**。
1. 在&#x200B;**[!UICONTROL Frontal servers]**&#x200B;標籤中，輸入追蹤伺服器連線參數。

   若要建立追蹤例項，請輸入追蹤伺服器的URL、追蹤伺服器內部帳戶密碼，以及該例項的名稱、其密碼以及與其相關聯的DNS遮罩。

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. 輸入連接參數後，按一下&#x200B;**[!UICONTROL Confirm the configuration]**。
1. 如有必要，請指定要儲存傳送中包含之影像的位置。 若要這麼做，請從下拉式清單中選取其中一個發佈模式。

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   如果選擇&#x200B;**[!UICONTROL Tracking server(s)]**&#x200B;選項，則影像將複製到中間來源伺服器。

**設定客戶平台**

1. 轉至外部中間來源傳送帳戶。
1. 在&#x200B;**[!UICONTROL Mid-Sourcing]**&#x200B;標籤中，指定中間來源伺服器連線參數。

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. 按一下&#x200B;**[!UICONTROL Test the connection]**&#x200B;確認配置。
1. 宣告中間來源伺服器上參考的追蹤例項：

   按一下連結&#x200B;**[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   指定追蹤例項的名稱，然後確認與追蹤伺服器的連線。

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

如果要由多個中間來源伺服器管理訊息傳送，請選取選項&#x200B;**[!UICONTROL Routing with alternating mid-sourcing accounts]**&#x200B;並指定不同的伺服器。

![](assets/s_ncs_install_midsourcing_tracking04.png)
