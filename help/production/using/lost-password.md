---
solution: Campaign Classic
product: campaign
title: 遺失密碼
description: 遺失密碼
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 7%

---


# 遺失密碼{#lost-password}

您可以更改或恢復丟失的密碼。
有兩種可能的情況：

* [Adobe Campaign營運商遺失密碼](#password-lost-by-campaign-operator)
* [內部密碼遺失](#internal-password-lost) （僅限內部部署客戶）

## 促銷活動運算子{#password-lost-by-campaign-operator}遺失密碼

如果Adobe Campaign運算子遺失其密碼，您可以加以變更。
要執行此操作，請遵循下列步驟：

1. 透過擁有管理員權限的營運商連線。
1. 以滑鼠右鍵按一下運算子。
1. 選擇&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Reset password]**。

   ![](assets/operator-passwd.png)

1. 設定運算子的新密碼。 我們建議操作員在首次重新連接時更改其密碼。

## 內部密碼丟失{#internal-password-lost}

>[!NOTE]
>
>本節僅適用於內部部署客戶。

如果內部密碼丟失，您必須重新初始化它。
若要這麼做，請套用下列程式：

1. 編輯&#x200B;**/usr/local/neolane/nl6/conf/serverConf.xml**&#x200B;檔案。

1. 轉至&#x200B;**internalPassword**&#x200B;行。

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. 刪除引號中的字串，在此例中：**myPassword**

   因此，您可以獲得以下行：

   ```
   !-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/
   ```

1. 儲存變更並關閉檔案。

1. 設定新密碼。 要執行此操作，請輸入以下命令：

   ```
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. 您現在可以使用新密碼在&#x200B;**Internal**&#x200B;模式下連接。
