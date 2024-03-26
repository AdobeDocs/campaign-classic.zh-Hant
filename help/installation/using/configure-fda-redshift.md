---
product: campaign
title: 設定Amazon Redshift的存取權
description: 瞭解如何在FDA中設定Amazon Redshift的存取權
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ef2b98bd-441e-4e59-bb41-4e835e250663
source-git-commit: 2ba6066b2999973e64ed3b429af78696f093dd09
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 4%

---

# 設定Amazon Redshift的存取權 {#configure-access-to-redshift}

使用行銷活動 **同盟資料存取** (FDA)選項，用於處理儲存在外部資料庫中的資訊。 請依照下列步驟設定Amazon Redshift的存取權。

1. 設定 [Amazon Redshift資料庫](#configuring-redshift)
1. 設定Amazon Redshift [外部帳戶](#redshift-external) 在Campaign中

## Linux上的Amazon Redshift {#redshift-linux}

進行設定 [!DNL Amazon Redshift] 在Linux上，請遵循下列步驟：

1. 在ODBC安裝之前，請檢查您的Linux發行版本上是否已安裝下列套裝軟體：

   * 若為Red Hat/CentOS：

     ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
     ```

   * 對於Debian：

     ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
     ```

1. 在執行指令碼之前，您可以透過存取更多資訊 `--help` 選項：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./redshift_odbc-setup.sh --help
   ```

1. 存取指令碼所在的目錄，並以root使用者的身分執行以下指令碼：

   ```
     cd /usr/local/neolane/nl6/bin/fda-setup-scripts
     ./redshift_odbc-setup.sh
   ```

1. 安裝ODBC驅動程式之後，您需要重新啟動Campaign Classic。 要執行此操作，請執行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 接著，您可以在Campaign中設定 [!DNL Amazon Redshift] 外部帳戶。 有關如何設定外部帳戶的詳細資訊，請參閱 [本節](#redshift-external).

## Amazon Redshift外部帳戶 {#redshift-external}

此 [!DNL Amazon Redshift] 外部帳戶可讓您將您的Campaign執行個體連線至Amazon Redshift外部資料庫。

1. 在Campaign Classic中，設定您的 [!DNL Amazon Redshift] 外部帳戶。 從 **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選取 **[!UICONTROL External database]** 作為外部帳戶的 **[!UICONTROL Type]**.

1. 設定 **[!UICONTROL Amazon Redshift]** 外部帳戶，您必須指定：

   * **[!UICONTROL Type]**：Amazon Redshift

   * **[!UICONTROL Server]**：DNS的名稱

   * **[!UICONTROL Account]**：使用者名稱

   * **[!UICONTROL Password]**：使用者帳戶密碼

   * **[!UICONTROL Database]**：未在DSN中指定的資料庫名稱。 若在DSN中指定，可保留空白

   * **[!UICONTROL Working schema]**：工作結構描述的名稱。 [了解更多](https://docs.aws.amazon.com/redshift/latest/dg/r_Schemas_and_tables.html)

   * **[!UICONTROL Time zone]**：伺服器時區

   ![](assets/amazon_redshift.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。
