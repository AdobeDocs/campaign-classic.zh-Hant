---
product: campaign
title: 配置訪問Oracle
description: 了解如何在FDA中設定Oracle存取權
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 配置對Oracle{#configure-access-to-oracle}的訪問

使用Campaign [同盟資料存取](../../installation/using/about-fda.md)(FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟來設定存取Oracle。

1. 在[Linux](#oracle-linux)或[Windows](#azure-windows)上配置Oracle
1. 在Campaign中設定Oracle[外部帳戶](#oracle-external)

## OracleLinux {#oracle-linux}

在FDA中連線至Oracle外部資料庫需要Adobe Campaign伺服器下方的額外設定。

1. 安裝與Oracle版本對應的Oracle完整客戶端。
1. 將TNS定義新增至安裝。 要執行此操作，請在/etc/oracle儲存庫的&#x200B;**tnsnames.ora**&#x200B;檔案中指定它們。 如果此儲存庫不存在，請建立它。

   然後建立新的TNS_ADMIN環境變數：導出TNS_ADMIN=/etc/oracle，然後重新啟動電腦。

1. 將Oracle整合至您的Adobe Campaign伺服器(nlserver)。 要執行此操作，請檢查Adobe Campaign伺服器樹結構的「nl6」資料夾中是否存在&#x200B;**customer.sh**&#x200B;檔案，並檢查其中是否包含指向Oracle庫的連結。

   例如，對於11.2中的用戶端：

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >這些值(尤其是ORACLE_HOME)取決於您的安裝儲存庫。 參考這些值之前，請務必檢查樹結構。

1. 安裝Oracle所需的程式庫：

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

1. 在Campaign Classic中，您接著可以設定[!DNL Oracle]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[此部分](#oracle-external)。

## OracleWindows {#oracle-windows}

在FDA中連線至Oracle外部資料庫需要Adobe Campaign伺服器下方的額外設定。

1. 安裝Oracle客戶端。

1. 在C:Oracle資料夾中，建立包含TNS定義的&#x200B;**tnsnames.ora**&#x200B;檔案。

1. 新增TNS_ADMIN環境變數，並將C:Oracle設為值，然後重新啟動電腦。

1. 在Campaign Classic中，您接著可以設定[!DNL Oracle]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[此部分](#oracle-external)。

## Oracle外部帳戶{#oracle-external}

[!DNL Oracle]外部帳戶可讓您將Campaign執行個體連結至Oracle外部資料庫。

1. 從促銷活動&#x200B;**[!UICONTROL Explorer]**&#x200B;中，選取&#x200B;**[!UICONTROL Administration]**「>」 **[!UICONTROL Platform]**「>」 **[!UICONTROL External accounts]**。

1. 選擇&#x200B;**[!UICONTROL New]**。

1. 選擇&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

1. 配置&#x200B;**[!UICONTROL Oracle]**&#x200B;外部帳戶，必須指定：

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**:DNS的名稱

   * **[!UICONTROL Account]**:使用者名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Time zone]**:伺服器時區
   ![](assets/oracle_config.png)
