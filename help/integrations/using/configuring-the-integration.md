---
solution: Campaign Classic
product: campaign
title: 設定Adobe Experience Manager整合
description: 瞭解如何設定Campaign-AEM整合
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: a157082070b22e3621cb81411a5ddde387fd5fcf
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 2%

---


# 配置整合{#configuring-the-integration}

## 在Adobe Campaign中設定{#configuring-in-adobe-campaign}

若要搭配使用這兩個解決方案，您必須將它們設定為彼此連線。

請依照下列步驟，在Adobe Campaign中啟動設定：

1. [在Adobe Campaign中安裝AEM整合套件](#install-the-aem-integration-package-in-adobe-campaign)
1. [設定外部帳戶](#configure-the-external-account)
1. [設定AEM資源篩選](#configure-aem-resources-filtering)

適用於進階配置，例如管理個人化欄位和區塊。 請參閱Adobe Experience Manager [檔案](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)。

### 在Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}中安裝AEM整合套件

首先需要安裝&#x200B;**[!UICONTROL AEM integration]**&#x200B;軟體包。

1. 從您的Adobe Campaign例項中，從上方工具列選取&#x200B;**[!UICONTROL Tools]**。
1. 選取 **[!UICONTROL Tools > Advanced > Import package...]**。

   ![](assets/aem_config_1.png)

1. 選取 **[!UICONTROL Install a standard package]**。
1. 選中&#x200B;**[!UICONTROL AEM integration]** ，然後按一下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕。

   ![](assets/aem_config_2.png)

1. 在下一個窗口中，按一下&#x200B;**[!UICONTROL Start]**&#x200B;按鈕以開始安裝軟體包。 安裝完成後，關閉窗口。

### 設定AEM運算子的安全區{#configure-the-security-zone-for-aem-operator}

**[!UICONTROL AEM integration]**&#x200B;套件會在Campaign中設定&#x200B;**[!UICONTROL aemserver]**&#x200B;運算子。 此運算子將用來將Adobe Experience Manager伺服器連線至Adobe Campaign。

您需要為此營運商設定安全區，以便透過Adobe Experience Manager連線至Adobe Campaign。

>[!CAUTION]
>
>我們強烈建議建立專用於AEM的安全區，以避免任何安全性問題。 有關詳細資訊，請參閱[安裝指南](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

如果您的促銷活動實例是由Adobe代管，請聯絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)團隊。 如果您使用內部部署Campaign，請遵循下列步驟：

1. 開啟&#x200B;**serverConf.xml**&#x200B;配置檔案。
1. 訪問選定安全區的&#x200B;**allowUserPassword**&#x200B;屬性，並將其設定為&#x200B;**true**。

   這可讓Adobe Experience Manager透過登入／密碼連線Adobe Campaign。

### 配置外部帳戶{#configure-the-external-account}

**[!UICONTROL AEM integration]**&#x200B;套件已建立Adobe Experience Cloud的外部帳戶。 您現在需要設定它，以連線您的Adobe Experience Manager實例。

若要混淆AEM外部帳戶，請遵循下列步驟：

1. 按一下 **[!UICONTROL Explorer]** 按鈕。

   ![](assets/aem_config_3.png)

1. 選取 **[!UICONTROL Administration > Platform > External accounts]**。
1. 從&#x200B;**[!UICONTROL External account]**&#x200B;清單中，選擇&#x200B;**[!UICONTROL AEM instance]**。
1. 輸入AEM製作例項的參數：

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >請確定您的&#x200B;**[!UICONTROL Server]**&#x200B;位址未以尾隨斜線結尾。

   ![](assets/aem_config_4.png)

1. 選中&#x200B;**[!UICONTROL Enabled]**&#x200B;框。
1. 按一下 **[!UICONTROL Save]** 按鈕。

### 設定AEM資源篩選{#configure-aem-resources-filtering}

**AEMResourceTypeFilter**&#x200B;選項用於篩選可用於Adobe Campaign的Experience Manager資源類型。 這可讓Adobe Campaign擷取專門設計為僅用於Adobe Campaign的Experience Manager內容。

要檢查&#x200B;**[!UICONTROL AEMResourceTypeFilter]**&#x200B;選項是否已配置：

1. 按一下 **[!UICONTROL Explorer]** 按鈕。
1. 選取 **[!UICONTROL Administration > Platform > Options]**。
1. 從&#x200B;**[!UICONTROL Options]**&#x200B;清單中，選擇&#x200B;**[!UICONTROL AEMResourceTypeFilter]**。
1. 在&#x200B;**[!UICONTROL Value (text)]**&#x200B;欄位中，路徑應如下：

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   或者在某些情況下：

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## 在Adobe Experience Manager中設定{#configuring-in-adobe-experience-manager}

請依照下列步驟，在Adobe Experience Manager中啟動設定：

1. 設定&#x200B;**replication**，將AEM編寫例項複製至AEM發佈例項。

   要瞭解如何配置複製，請參閱Adobe Experience Manager [文檔](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)。

1. 在您的編寫執行個體上安裝整合&#x200B;**FeaturePack**，然後複製發佈執行個體上的安裝。 （僅適用於AEM 5.6.1和6.0版）。

   如要瞭解如何安裝FeaturePack，請參閱Adobe Experience Manager [說明檔案](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)。

1. 透過設定專屬的&#x200B;**雲端服務**，將Adobe Experience Manager連接至Adobe Campaign。

   如要瞭解如何透過雲端服務連接這兩個解決方案，請參閱Adobe Experience Manager [檔案](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager)。

1. 配置&#x200B;**Externalizer服務**。

   如要瞭解如何設定，請參閱Adobe Experience Manager [檔案](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)。

