---
product: campaign
title: 遺失密碼
description: 遺失密碼
feature: Monitoring, Access Management
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 3%

---

# 遺失密碼{#lost-password}

>[!NOTE]
>
>此頁面僅適用於使用原生驗證連線至Campaign的運運算元。

您可以變更或復原遺失的密碼。
有兩種可能的情況：

* [Adobe Campaign運運算元遺失密碼](#password-lost-by-campaign-operator)
* [內部密碼遺失](#internal-password-lost) （僅限內部部署客戶）

## Campaign運運算元遺失密碼 {#password-lost-by-campaign-operator}

如果Adobe Campaign運運算元遺失密碼，您可以加以變更。

>[!NOTE]
>
>此程式僅適用於使用原生驗證連線至Campaign的運運算元。 若為Adobe IMS驗證，請參閱[此檔案](https://helpx.adobe.com/ie/manage-account/using/change-or-reset-password.html){target="_blank"}。

若要重設Campaign密碼，請遵循下列步驟：

1. 透過具有管理員許可權的操作者連線。
1. 以滑鼠右鍵按一下運運算元。
1. 選取&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Reset password]**。

   ![](assets/operator-passwd.png)

1. 設定運運算元的新密碼。 建議操作員在第一次重新連線時變更密碼。

## 內部密碼遺失 {#internal-password-lost}

>[!NOTE]
>
>本節內容僅適用於內部部署客戶。

如果內部密碼遺失，您必須重新初始化它。

要執行此操作，請套用下列程式：

1. 編輯&#x200B;**/usr/local/neolane/nl6/conf/serverConf.xml**&#x200B;檔案。

1. 移至&#x200B;**internalPassword**&#x200B;行。

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. 刪除引號中的字串，在此案例中為： `myPassword`。 您會看到下列文字行：

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/>
   ```

1. 儲存變更並關閉檔案。

1. 停止`nlserver`處理序。

1. 設定新密碼。 要執行此操作，請輸入下列命令：

   ```javascript
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. 啟動`nlserver`處理序。

1. 您現在可以使用新密碼以&#x200B;**內部**&#x200B;模式連線。
