---
product: campaign
title: 設定Adobe Experience Manager整合
description: 了解如何設定Campaign-AEM整合
audience: integrations
content-type: reference
exl-id: 54ee88b2-e646-4fb9-abec-957f0096f15f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 4%

---

# 配置整合{#configuring-the-integration}

![](../../assets/common.svg)

## 在Adobe Campaign中設定 {#configuring-in-adobe-campaign}

若要同時使用這兩個解決方案，您必須將它們設定為彼此連線。

請依照下列步驟，開始在Adobe Campaign中進行設定：

1. [在Adobe Campaign中安裝AEM整合套件](#install-the-aem-integration-package-in-adobe-campaign)
1. [設定外部帳戶](#configure-the-external-account)
1. [設定AEM資源篩選](#configure-aem-resources-filtering)

用於進階設定，例如管理個人化欄位和區塊。 請參閱Adobe Experience Manager [檔案](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)。

### 在Adobe Campaign中安裝AEM整合套件 {#install-the-aem-integration-package-in-adobe-campaign}

首先需要安裝&#x200B;**[!UICONTROL AEM integration]**&#x200B;包。

1. 從Adobe Campaign例項，從上方工具列選取&#x200B;**[!UICONTROL Tools]**。
1. 選取 **[!UICONTROL Tools > Advanced > Import package...]**。

   ![](assets/aem_config_1.png)

1. 選取 **[!UICONTROL Install a standard package]**。
1. 檢查&#x200B;**[!UICONTROL AEM integration]** ，然後按一下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕。

   ![](assets/aem_config_2.png)

1. 在下一個窗口中，按一下&#x200B;**[!UICONTROL Start]**&#x200B;按鈕以開始安裝軟體包。 安裝完成後，關閉視窗。

### 為AEM運算子設定安全區域 {#configure-the-security-zone-for-aem-operator}

**[!UICONTROL AEM integration]**&#x200B;套件會在Campaign中設定&#x200B;**[!UICONTROL aemserver]**&#x200B;運算子。 此運算子將用來將Adobe Experience Manager伺服器連線至Adobe Campaign。

您需要為此運算子設定安全區域，以透過Adobe Experience Manager連線至Adobe Campaign。

>[!CAUTION]
>
>強烈建議建立專用於AEM的安全區域，以避免任何安全性問題。 有關詳細資訊，請參閱安裝[指南](../../installation/using/security-zones.md)。

如果您的Campaign執行個體是由Adobe托管，請聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)團隊。 如果您使用內部部署的Campaign，請遵循下列步驟：

1. 開啟&#x200B;**serverConf.xml**&#x200B;配置檔案。
1. 訪問所選安全區域的&#x200B;**allowUserPassword**&#x200B;屬性，並將其設定為&#x200B;**true**。

   這可讓Adobe Experience Manager透過登入/密碼連線Adobe Campaign。

### 設定外部帳戶 {#configure-the-external-account}

**[!UICONTROL AEM integration]**&#x200B;套件已建立Adobe Experience Cloud的外部帳戶。 您現在需要將其設定為與Adobe Experience Manager執行個體連線。

若要設定AEM外部帳戶，請遵循下列步驟：

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
   >請確定您的&#x200B;**[!UICONTROL Server]**&#x200B;位址不會以尾隨斜線結尾。

   ![](assets/aem_config_4.png)

1. 勾選&#x200B;**[!UICONTROL Enabled]**&#x200B;方塊。
1. 按一下 **[!UICONTROL Save]** 按鈕。

### 設定AEM資源篩選 {#configure-aem-resources-filtering}

**AEMResourceTypeFilter**&#x200B;選項用於篩選可在Adobe Campaign中使用的Experience Manager資源類型。 這可讓Adobe Campaign擷取專門設計為僅用於Adobe Campaign的Experience Manager內容。

檢查&#x200B;**[!UICONTROL AEMResourceTypeFilter]**&#x200B;選項是否已配置：

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

## 在Adobe Experience Manager中設定 {#configuring-in-adobe-experience-manager}

請依照下列步驟，開始在Adobe Experience Manager中進行設定：

1. 設定&#x200B;**replication**&#x200B;以從AEM製作例項複製到AEM發佈例項。

   若要了解如何設定復寫，請參閱Adobe Experience Manager [檔案](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)。

1. 在您的製作執行個體上安裝整合&#x200B;**FeaturePack**，然後在您的發佈執行個體上複製安裝。 (僅限AEM 5.6.1和6.0版)。

   若要了解如何安裝FeaturePack，請參閱Adobe Experience Manager [檔案](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)。

1. 設定專用的&#x200B;**Cloud Service**，將Adobe Experience Manager連線至Adobe Campaign。

   若要了解如何透過Cloud Services連線兩個解決方案，請參閱Adobe Experience Manager [檔案](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) 。

1. 配置&#x200B;**Externalizer服務**。

   若要了解如何設定，請參閱Adobe Experience Manager [檔案](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)。
