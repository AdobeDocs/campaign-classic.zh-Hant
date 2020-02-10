---
title: 丟失密碼
seo-title: 丟失密碼
description: 丟失密碼
seo-description: null
page-status-flag: never-activated
uuid: caac68bf-abdc-45da-9697-b689ebd37002
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: d52eeadc-19c6-4d48-995a-1c1f2ca3b5ec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

---


# 丟失密碼{#lost-password}

您可以更改或恢復丟失的密碼。

有兩種可能的情況：

* Adobe Campaign運算子遺失密碼。

   在這種情況下，您可以更改有關操作員的密碼。 若要這麼做，請透過具有管理員權限的運算子連線，以滑鼠右鍵按一下運算子，選取 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 並設定運算子的新密碼。 我們建議營運商在第一次重新連線時變更其密碼。

   ![](assets/operator-passwd.png)

* **內部密碼** （僅限內部部署客戶）遺失。

   如果內 **部密碼** ，您必須重新初始化它。 若要這麼做，請套用下列程式：

   1. 編輯/usr/local/neolane/nl6/conf/serverConf.xml **檔案** 。
   1. 轉至internalPassword **行** 。

      ```
      <!-- XTK authentication mode internalPassword : Password of internal account -->
       <xtk internalPassword="myPassword"/>
      ```

   1. 刪除引號中的字串，在此例中：myPassword( **myPassword)**

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

   1. 您現在可以使用新密碼在「內部」模 **式下** 連接。

