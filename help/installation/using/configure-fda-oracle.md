---
solution: Campaign Classic
product: campaign
title: 配置對Oracle的訪問
description: 瞭解如何在FDA中配置對Oracle的訪問
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# 配置對Oracle的訪問 {#configure-access-to-oracle}

使用Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA)選項來處理儲存在外部資料庫中的資訊。 按照以下步驟配置對Oracle的訪問。

1. 在 [Linux或](#oracle-linux)[Windows上配置Oracle](#azure-windows)
1. 在Campaign中配 [置Oracle外](#oracle-external) 部帳戶

## Linux上的Oracle {#oracle-linux}

在FDA中連線至Oracle外部資料庫需要Adobe Campaign伺服器下方的其他設定。

1. 安裝與Oracle版本對應的Oracle完整客戶端。
1. 將您的TNS定義新增至安裝。 要執行此操作，請在/etc/oracle儲存庫 **的tnsnames.ora** 檔案中指定它們。 如果此儲存庫不存在，請建立它。

   然後建立新的TNS_ADMIN環境變數：導出TNS_ADMIN=/etc/oracle並重新啟動電腦。

1. 將Oracle整合到您的Adobe Campaign伺服器(nlserver)。 若要這麼做，請檢查 **customer.sh** 檔案是否位於Adobe Campaign伺服器樹狀結構的「nl6」資料夾中，且其中包含Oracle程式庫的連結。

   例如，對於11.2版的客戶：

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >這些值（尤其是ORACLE_HOME）取決於您的安裝儲存庫。 請務必先檢查樹結構，然後再參照這些值。

1. 安裝Oracle所需的庫：

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Oracle] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參 [閱本節](#oracle-external)。

## Windows版Oracle {#oracle-windows}

在FDA中連線至Oracle外部資料庫需要Adobe Campaign伺服器下方的其他設定。

1. 安裝Oracle客戶端。

1. 在C:Oracle資料夾中，建立包含 **TNS定義的tnsnames.ora** 檔案。

1. 以C:Oracle為值添加TNS_ADMIN環境變數並重新啟動電腦。

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Oracle] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參 [閱本節](#oracle-external)。

## Oracle外部帳戶 {#oracle-external}

外部 [!DNL Oracle] 帳戶允許您將Campaign實例連接到Oracle外部資料庫。

1. 從促銷 **[!UICONTROL Explorer]**&#x200B;活動中， **[!UICONTROL Administration]** 選擇「>」 **[!UICONTROL Platform]** 「>」 **[!UICONTROL External accounts]**。

1. 選擇 **[!UICONTROL New]**。

1. 選 **[!UICONTROL External database]** 擇作為外部帳戶 **[!UICONTROL Type]**。

1. 設定外 **[!UICONTROL Oracle]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:Oracle

   * **[!UICONTROL Server]**:DNS的名稱

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Time zone]**:伺服器時區

   ![](assets/oracle_config.png)

