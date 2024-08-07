---
product: campaign
title: 設定Oracle的存取權
description: 瞭解如何在FDA中設定Oracle存取權
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 設定Oracle的存取權 {#configure-access-to-oracle}



使用Campaign [同盟資料存取](../../installation/using/about-fda.md) (FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟設定對Oracle的存取權。

1. 在[Linux](#oracle-linux)或[Windows](#azure-windows)上設定Oracle
1. 在Campaign中設定Oracle[外部帳戶](#oracle-external)

## 在Linux上的Oracle {#oracle-linux}

在FDA中連線至Oracle外部資料庫時，需要在Adobe Campaign伺服器上設定以下其他設定。

1. 安裝與您的Oracle版本相對應的Oracle完整使用者端。
1. 將TNS定義新增至安裝。 若要這麼做，請在/etc/oracle存放庫的&#x200B;**tnsnames.ora**&#x200B;檔案中指定。 如果此存放庫不存在，請建立它。

   然後建立新的TNS_ADMIN環境變數：匯出TNS_ADMIN=/etc/oracle並重新啟動電腦。

1. 將Oracle整合至您的Adobe Campaign伺服器(nlserver)。 若要這麼做，請檢查&#x200B;**customer.sh**&#x200B;檔案是否存在於Adobe Campaign伺服器樹狀結構的「nl6」資料夾中，而且其是否包含Oracle程式庫的連結。

   例如，對於11.2中的使用者端：

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >這些值(尤其是ORACLE_HOME)取決於您的安裝存放庫。 在參照這些值之前，請務必檢查您的樹狀結構。

1. 安裝Oracle所需的程式庫：

   * **libclntsh.so**

     ```
     cd /usr/lib/oracle/<version>/client<architecture>/lib
     ln -s libclntsh.so.<version> libclntsh.so
     ```

   * **libaio1**

     ```
     apt install libaio1
     or
     yum install libaio1
     ```

1. 然後，您可以在Campaign Classic中設定[!DNL Oracle]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#oracle-external)。

## 在Windows上Oracle {#oracle-windows}

在FDA中連線至Oracle外部資料庫時，需要在Adobe Campaign伺服器上設定以下其他設定。

1. 安裝Oracle使用者端。

1. 在C：Oracle資料夾中，建立包含您的TNS定義的&#x200B;**tnsnames.ora**&#x200B;檔案。

1. 新增具有C：Oracle作為值的TNS_ADMIN環境變數，並重新啟動電腦。

1. 然後，您可以在Campaign Classic中設定[!DNL Oracle]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#oracle-external)。

## oracle外部帳戶 {#oracle-external}

[!DNL Oracle]外部帳戶可讓您將Campaign執行個體連線至Oracle外部資料庫。

1. 從行銷活動&#x200B;**[!UICONTROL Explorer]**，選取&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 選擇&#x200B;**[!UICONTROL New]**。

1. 選取&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

1. 設定&#x200B;**[!UICONTROL Oracle]**&#x200B;外部帳戶，您必須指定：

   * **[!UICONTROL Type]**：Oracle

   * **[!UICONTROL Server]**： DNS的名稱

   * **[!UICONTROL Account]**：使用者名稱

   * **[!UICONTROL Password]**：使用者帳戶密碼

   * **[!UICONTROL Time zone]**：伺服器時區

   ![](assets/oracle_config.png)
