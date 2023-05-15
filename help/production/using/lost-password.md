---
product: campaign
title: 遺失密碼
description: 遺失密碼
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 8%

---

# 遺失密碼{#lost-password}



您可以更改或恢復丟失的密碼。
有兩種可能的情況：

* [Adobe Campaign運算子遺失密碼](#password-lost-by-campaign-operator)
* [內部密碼丟失](#internal-password-lost) （僅限內部部署客戶）

## Campaign運算子遺失密碼 {#password-lost-by-campaign-operator}

如果Adobe Campaign運算子遺失其密碼，您可以加以變更。
要執行此操作，請遵循下列步驟：

1. 通過具有管理員權限的運算子連接。
1. 以滑鼠右鍵按一下運算子。
1. 選取 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. 設定運算子的新密碼。 建議運算子在首次重新連線時變更其密碼。

## 內部密碼丟失 {#internal-password-lost}

>[!NOTE]
>
>本節內容僅適用於內部部署客戶。

如果內部密碼丟失，則必須重新初始化它。
要執行此操作，請應用以下過程：

1. 編輯 **/usr/local/neolane/nl6/conf/serverConf.xml** 檔案。

1. 前往 **internalPassword** 行。

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. 刪除以引號括住的字串，在此情況下： **myPassword**

   因此，您會取得下列行：

   ```
   !-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/
   ```

1. 儲存變更並關閉檔案。

1. 配置新密碼。 要執行此操作，請輸入以下命令：

   ```
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. 您現在可以使用新密碼來連線 **內部** 模式。
