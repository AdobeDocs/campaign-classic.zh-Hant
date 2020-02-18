---
title: 設定整合
seo-title: 設定整合
description: 設定整合
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 31f30db6eaf1fee43f9f757124e3fa8ed1d0075f

---


# Configuring the integration{#configuring-the-integration}

## 在Adobe Campaign中設定 {#configuring-in-adobe-campaign}

若要搭配使用這兩個解決方案，您必須將它們設定為彼此連線。

請依照下列步驟，在Adobe Campaign中啟動設定：

1. [在Adobe Campaign中安裝AEM整合套件](#install-the-aem-integration-package-in-adobe-campaign)
1. [設定外部帳戶](#configure-the-external-account)
1. [設定AEM資源篩選](#configure-aem-resources-filtering)

適用於進階配置，例如管理個人化欄位和區塊。 請參閱Adobe Experience Manager文 [件](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)。

### 在Adobe Campaign中安裝AEM整合套件 {#install-the-aem-integration-package-in-adobe-campaign}

您首先需要安裝此套 **[!UICONTROL AEM integration]** 件。

1. 從您的Adobe Campaign例項中，從上方 **[!UICONTROL Tools]** 工具列中選取。
1. Select **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Select **[!UICONTROL Install a standard package]**.
1. 勾選 **[!UICONTROL AEM integration]** 然後按一下 **[!UICONTROL Next]** 按鈕。

   ![](assets/aem_config_2.png)

1. 在下一個窗口中，單 **[!UICONTROL Start]** 擊按鈕開始安裝軟體包。 安裝完成後，關閉窗口。

### 設定AEM營運商的安全區 {#configure-the-security-zone-for-aem-operator}

套件 **[!UICONTROL AEM integration]** 會在促銷活動 **[!UICONTROL aemserver]** 中設定運算元。 此運算子將用來將Adobe Experience Manager伺服器連接至Adobe Campaign。

您需要為此營運商設定安全區，以便透過Adobe Experience Manager連線至Adobe Campaign。

>[!CAUTION]
>
>我們強烈建議建立專用於AEM的安全區，以避免任何安全性問題。 有關詳細資訊，請參閱《安裝指 [南》](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

如果您的Campaign實例是由Adobe代管，請聯絡Adobe支援團隊。 如果您使用內部部署Campaign，請遵循下列步驟：

1. 開啟 **serverConf.xml配置檔案** 。
1. 訪問選 **定安全區的allowUserPassword** 屬性，並將其設定為 **true**。

   這可讓Adobe Experience manager透過登入／密碼連線Adobe Campaign。

### 設定外部帳戶 {#configure-the-external-account}

此套 **[!UICONTROL AEM integration]** 件已建立Adobe Experience cloud的外部帳戶。 您現在需要設定它，以連線您的Adobe Experience Manager實例。

若要混淆AEM外部帳戶，請遵循下列步驟：

1. Click the **[!UICONTROL Explorer]** button.

   ![](assets/aem_config_3.png)

1. Select **[!UICONTROL Administration > Platform > External accounts]**.
1. 從清單 **[!UICONTROL External account]** 中，選擇 **[!UICONTROL AEM instance]**。
1. 輸入AEM製作例項的參數：

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**
   >[!NOTE]
   >
   >請確定您的 **[!UICONTROL Server]** 位址未以尾隨斜線結尾。

   ![](assets/aem_config_4.png)

1. 選中該 **[!UICONTROL Enabled]** 框。
1. Click the **[!UICONTROL Save]** button.

### 設定AEM資源篩選 {#configure-aem-resources-filtering}

AEMResourceTypeFilter **** 選項可用來篩選Adobe Campaign中可用的Experience manager資源類型。 這可讓Adobe Campaign擷取專門設計為僅用於Adobe Campaign的Experience Manager內容。

要檢查選項是 **[!UICONTROL AEMResourceTypeFilter]** 否已配置：

1. Click the **[!UICONTROL Explorer]** button.
1. Select **[!UICONTROL Administration > Platform > Options]**.
1. 從清單 **[!UICONTROL Options]** 中，選擇 **[!UICONTROL AEMResourceTypeFilter]**。
1. 在字 **[!UICONTROL Value (text)]** 段中，路徑應如下：

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   或者在某些情況下：

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## 在Adobe Experience manager中設定 {#configuring-in-adobe-experience-manager}

請依照下列步驟，在Adobe Experience Manager中啟動設定：

1. 設定 **複製** ，以從AEM製作例項複製至AEM發佈例項。

   要瞭解如何配置複製，請參閱Adobe Experience manager文 [檔](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)。

1. 在您的製作例 **項上安裝整合FeaturePack** ，然後複製您發佈例項上的安裝。 （僅適用於AEM 5.6.1和6.0版）。

   如要瞭解如何安裝FeaturePack，請參閱Adobe Experience Manager文 [件](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)。

1. 透過設定專屬的雲端服務，將Adobe Experience manager與Adobe Campaign **連接**。

   如要瞭解如何透過雲端服務連接這兩個解決方案，請參閱Adobe Experience Manager文 [件](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) 。

1. 配置 **Externalizer服務**。

   如要瞭解如何設定，請參閱Adobe Experience Manager文 [件](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)。

