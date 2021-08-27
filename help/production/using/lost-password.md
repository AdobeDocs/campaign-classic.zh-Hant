---
product: campaign
title: 遺失密碼
description: 遺失密碼
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 7%

---

# 遺失密碼{#lost-password}

![](../../assets/v7-only.svg)

您可以更改或恢復丟失的密碼。
有兩種可能的情況：

* [Adobe Campaign運算子遺失密碼](#password-lost-by-campaign-operator)
* [內部密碼遺失](#internal-password-lost) （僅限內部部署客戶）

## Campaign運算子遺失密碼 {#password-lost-by-campaign-operator}

如果Adobe Campaign運算子遺失其密碼，您可以加以變更。
要執行此操作，請遵循下列步驟：

1. 通過具有管理員權限的運算子連接。
1. 以滑鼠右鍵按一下運算子。
1. 選擇&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Reset password]**。

   ![](assets/operator-passwd.png)

1. 設定運算子的新密碼。 建議運算子在首次重新連線時變更其密碼。

## 內部密碼丟失 {#internal-password-lost}

>[!NOTE]
>
>本節內容僅適用於內部部署客戶。

如果內部密碼丟失，則必須重新初始化它。
要執行此操作，請應用以下過程：

1. 編輯&#x200B;**/usr/local/neolane/nl6/conf/serverConf.xml**&#x200B;檔案。

1. 轉至&#x200B;**internalPassword**&#x200B;行。

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. 刪除以引號括住的字串，在此情況下：**myPassword**

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

1. 您現在可以使用新密碼在&#x200B;**內部**&#x200B;模式中連接。
