---
product: campaign
title: 在 Linux 安裝 Campaign 的必要條件
description: 在 Linux 安裝 Campaign 的必要條件
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 1%

---

# 在Linux上安裝Campaign的必要條件{#prerequisites-of-campaign-installation-in-linux}

![](../../assets/v7-only.svg)

## 軟體必備條件 {#software-prerequisites}

本節詳細說明安裝Adobe Campaign前所需的初步設定步驟。

安裝Adobe Campaign所需的技術和軟體配置在[相容性矩陣](../../rn/using/compatibility-matrix.md)中有詳細說明。

提醒您，必須安裝並正確設定下列元件：

* Apache，請參閱[相容性矩陣](../../rn/using/compatibility-matrix.md),
* Java JDK和OpenJDK，請參閱[Java開發套件 — JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* 庫，請參閱[庫](#libraries),
* 資料庫訪問層，請參閱[資料庫訪問層](#database-access-layers),
* LibreOffice，請參閱[為Debian安裝LibreOffice](#installing-libreoffice-for-debian)和[為CentOS安裝LibreOffice](#installing-libreoffice-for-centos),
* 字型，請參閱[Fonts for MTA statistics](#fonts-for-mta-statistics)和[Fonts for Japanese實例](#fonts-for-japanese-instances)。

>[!NOTE]
>
>若要在CentOS 7和Debian 8平台上安裝低於或等於8709的組建，必須啟用apache access_compat模組。

### 程式庫 {#libraries}

若要在Linux中安裝Adobe Campaign，請確定您有必要的程式庫。

* 程式庫C必須能支援TLS（執行緒本機儲存）模式。 在大多數情況下，此模式處於活動狀態，但某些內核已禁用Xen支援。

   若要檢查此項，您可以使用&#x200B;**uname -a 例如，| grep xen**&#x200B;命令。

   如果命令未傳回任何內容（空行），表示配置正確。

* 您必須有OpenSSL的&#x200B;**版本0.9.8**&#x200B;或&#x200B;**1.0**。

   對於RHEL 7分發，需要1.0版的OpenSSL。

* 若要使用Adobe Campaign，您必須安裝&#x200B;**libicu**&#x200B;程式庫。

   支援下列版本的&#x200B;**libicu**（32位或64位）:

   * RHEL 7、CentOS 7:libicu50
   * Debian 8:libicu52
   * Debian 9:libicu57

   若要使用Adobe Campaign，您必須安裝libc-ares程式庫。 在RHEL/CentOS上，運行以下命令：

   ```
   yum install c-ares
   ```

   在Debian上：

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

使用時，必須正確配置SELinux模組。

要執行此操作，請以root身份登錄並輸入以下命令：

```
echo 0 >/selinux/enforce
```

此外，在&#x200B;**/etc/sysconfig/httpd**&#x200B;檔案中，還新增了以下行以參考Adobe Campaign環境配置指令碼：

```
. ~neolane/nl6/env.sh
```

在RHEL和CentOS中，當啟用SELinux時，會發現與資料庫的客戶端層的相容性問題。 為確保Adobe Campaign能正確運作，建議停用SELinux。

**套用下列程式：**

* 編輯檔案&#x200B;**/etc/selinux/config**

* 按如下方式修改SELINUX行：

```
SELINUX=disabled
```

### MTA統計資訊字型 {#fonts-for-mta-statistics}

為了正確顯示MTA統計資料報表(nms/fra/jsp/stat.jsp)，請新增字型。

在Debian中，新增命令：

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

在Redhat中，使用以下命令：

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### 日文實例的字型 {#fonts-for-japanese-instances}

日文執行個體需要特定字元的字型，才能將報表匯出為PDF格式。

在Debian中，新增命令：

```
aptitude install fonts-ipafont
```

在Red Hat中，添加命令：

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### 為Debian安裝LibreOffice {#installing-libreoffice-for-debian}

若為Debian，則需要下列設定：

1. 安裝下列標準套件：

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. 安裝下列字型（選用，但強烈建議使用日文執行個體）:

   ```
   apt-get install fonts-ipafont
   ```

### 安裝CentOS專用的LibreOffice {#installing-libreoffice-for-centos}

CentOS需要下列配置：

1. 安裝下列標準套件：

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. 安裝下列字型（選用，但強烈建議使用日文執行個體）:

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## 資料庫訪問層 {#database-access-layers}

您使用的資料庫引擎的存取層必須安裝在伺服器上，並可透過Adobe Campaign帳戶存取。 版本和安裝模式可能會因所使用的資料庫引擎而異。

[相容性矩陣](../../rn/using/compatibility-matrix.md)中詳細說明了支援的導頻版本。

另請檢查一般[資料庫](../../installation/using/database.md)部分。

### PostgreSQL {#postgresql}

Adobe Campaign支援7.2版中的所有PostgreSQL客戶端庫版本：（**libpq.so.5**、**libpq.so.4**、**libpq.so.3.2**&#x200B;和&#x200B;**libpq.so.3.1**）。

搭配Adobe Campaign使用PostgreSQL也需要安裝對應的&#x200B;**pgcrypto**&#x200B;程式庫。

### Oracle {#oracle}

擷取64位元Debian的程式庫版本，即：**libclntsh.so**、**libclntsh.so.11.1**&#x200B;和&#x200B;**libclntsh.so.10.1**。

您可以從Oracle技術網路獲取Linux RPM包。

>[!NOTE]
>
>如果您已安裝Oracle客戶端，但已安裝全局環境(例如：/etc/profile)未正確設定，您可以將遺漏的資訊新增至&#x200B;**nl6/customer.sh**&#x200B;指令碼。如需詳細資訊，請參閱[環境變數](../../installation/using/installing-packages-with-linux.md#environment-variables)。

**疑難排解和最佳實務**

oracle客戶端或伺服器更新、版本更改或實例的首次安裝後可能會出現問題。

如果您在用戶端主控台上發現記錄、工作流程上次處理、下次處理等作業出現非預期的時間延遲（一或多小時），則Oracle用戶端的程式庫與Oracle伺服器之間可能會有問題。 為了避免這些問題

1. 請務必使用&#x200B;**full client**。

   使用Oracle即時客戶端版本時發現了各種問題。 此外，無法在即時客戶端上更改時區檔案。

1. 確保&#x200B;**客戶端版本**&#x200B;和&#x200B;**資料庫伺服器版本**&#x200B;為&#x200B;**相同**。

   儘管Oracle的相容性矩陣和建議使客戶端和伺服器版本一致，但混合使用版本是已知會導致問題的。

   另請檢查「ORACLE_首頁」值，以確保它指向預期的客戶端版本（如果電腦上安裝了多個版本）。

1. 確保客戶端和伺服器使用相同的&#x200B;**時區檔案**。

### DB2 {#db2}

支援的程式庫版本為&#x200B;**libdb2.so**。

## 實施步驟 {#implementation-steps}

Adobe Campaign的Linux安裝必須依下列順序執行：伺服器安裝，然後執行實例配置。

本章將介紹安裝過程。 安裝步驟如下：

* 步驟1:安裝應用程式伺服器，請參閱[使用Linux](../../installation/using/installing-packages-with-linux.md)安裝套件。
* 步驟2:與Web伺服器整合（可選，視部署的元件而定）。

安裝步驟完成後，您需要配置實例、資料庫和伺服器。 有關詳細資訊，請參閱[關於初始配置](../../installation/using/about-initial-configuration.md)。
