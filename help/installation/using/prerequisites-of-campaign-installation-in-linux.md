---
product: campaign
title: 在 Linux 安裝 Campaign 的必要條件
description: 在 Linux 安裝 Campaign 的必要條件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 1%

---

# 在Linux上安裝市場活動的先決條件{#prerequisites-of-campaign-installation-in-linux}



## 軟體先決條件 {#software-prerequisites}

本節詳細介紹安裝Adobe Campaign之前所需的初步配置步驟。

安裝Adobe Campaign所需的技術和軟體配置詳見 [相容性矩陣](../../rn/using/compatibility-matrix.md)。

提醒您，需要安裝並正確配置以下元件：

* Apache，請參閱 [相容性矩陣](../../rn/using/compatibility-matrix.md)。
* Java JDK和OpenJDK，請參閱 [Java開發工具包 — JDK](../../installation/using/application-server.md#java-development-kit---jdk)。
* 庫，請參閱 [庫](#libraries)。
* 資料庫訪問層，請參閱 [資料庫訪問層](#database-access-layers)。
* LibreOffice，請參閱 [正在為Debian安裝LibreOffice](#installing-libreoffice-for-debian) 和 [正在為CentOS安裝LibreOffice](#installing-libreoffice-for-centos)。
* 字型，請參閱 [MTA統計資訊的字型](#fonts-for-mta-statistics) 和 [日文實例的字型](#fonts-for-japanese-instances)。

>[!NOTE]
>
>要在CentOS 7和Debian 8平台上安裝低於或等於8709的內部版本，必須啟用apache access_compat模組。

### 庫 {#libraries}

要在Linux中安裝Adobe Campaign，請確保您有所需的庫。

* 庫C必須能夠支援TLS（線程本地儲存）模式。 除某些內核已禁用Xen支援外，此模式在大多數情況下都處於活動狀態。

   要檢查此項，可使用 **未命名 — a |grep xen** 例如。

   如果命令未返回任何內容（空行），則表示配置正確。

* 必須有OpenSSL版本 **1.0.2** 或更高。

   對於RHEL 7/8發行版，需要OpenSSL 1.0版。

* 要使用Adobe Campaign，你需要 **利比庫** 已安裝庫。

   以下版本 **利比庫** 支援（32位或64位）:

   * RHEL 7/8、CentOS 7:LIBICU50
   * 德比8:LIBICU52
   * 德比9:LIBICU57

   要使用Adobe Campaign，您需要安裝libc-ares庫。 在RHEL/CentOS上，運行以下命令：

   ```
   yum install c-ares
   ```

   在德比：

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

使用時，必須正確配置SELinux模組。

要執行此操作，請以root用戶身份登錄並輸入以下命令：

```
echo 0 >/selinux/enforce
```

除此之外，在 **/etc/sysconfig/httpd** 檔案中，添加了以下行以引用Adobe Campaign環境配置指令碼：

```
. ~neolane/nl6/env.sh
```

在RHEL和CentOS中，當啟用SELinux時，會發現與資料庫客戶端層的相容性問題。 為確保Adobe Campaign能夠正確運行，我們建議禁用SELinux。

**應用以下流程：**

* 編輯檔案 **/etc/selinux/config**

* 按如下方式修改SELINUX行：

```
SELINUX=disabled
```

### MTA統計資訊的字型 {#fonts-for-mta-statistics}

為了正確顯示有關MTA統計資訊(nms/fra/jsp/stat.jsp)的報告，請添加字型。

在Debian中，添加命令：

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

在Redhat中，使用以下命令：

* 對於CentOS/RHEL 7:

   ```
   yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
   ```

* 對於RHEL 8:

   ```
   dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
   ```

### 日文實例的字型 {#fonts-for-japanese-instances}

要將報表導出為PDF格式，日文實例需要特定字元的字型。

在Debian中，添加命令：

```
aptitude install fonts-ipafont
```

在Red Hat中，添加命令：

* 對於RHEL 7:

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

* 對於RHEL 8:

   ```
   dnf install vlgothic-fonts
   ```

### 正在為Debian安裝LibreOffice {#installing-libreoffice-for-debian}

對於Debian，需要以下配置：

1. 安裝以下標準包：

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. 安裝以下字型（可選，但強烈建議使用日文實例）:

   ```
   apt-get install fonts-ipafont
   ```

### 正在為CentOS安裝LibreOffice {#installing-libreoffice-for-centos}

CentOS需要以下配置：

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## 資料庫訪問層 {#database-access-layers}

您所使用的資料庫引擎的訪問層必須安裝在伺服器上，並且可以通過Adobe Campaign帳戶訪問。 版本和安裝模式可能因所使用的資料庫引擎而異。

支援的試運行版本在 [相容性矩陣](../../rn/using/compatibility-matrix.md)。

還檢查常規 [資料庫](../../installation/using/database.md) 的子菜單。

### PostgreSQL {#postgresql}

Adobe Campaign支援版本7.2的所有PostgreSQL客戶端庫版本：(**libpq.so.5**。 **libpq.so.4**。 **libpq.so.3.2** 和 **libpq.so.3.1**)。

將PostgreSQL與Adobe Campaign配合使用還需要安裝相應的 **pgcrypto** 庫。

### Oracle {#oracle}

檢索64位Debian的庫版本，即： **libclntsh.so**。 **libclntsh.so.11.1** 和 **libclntsh.so.10.1**。

您可以從Oracle技術網路獲取Linux RPM軟體包。

>[!NOTE]
>
>如果已安裝Oracle客戶端但已安裝全局環境(例如：/etc/profile)未正確配置，您可以將丟失的資訊添加到 **nl6/customer.sh** 指令碼有關此的詳細資訊，請參閱 [環境變數](../../installation/using/installing-packages-with-linux.md#environment-variables)。

**故障排除和最佳做法**

在Oracle客戶端或伺服器更新、版本更改或實例首次安裝後，可能會出現問題。

如果您在客戶端控制台上注意到日誌、工作流上次處理、下一次處理等中存在意外的時間延遲（一個或多個小時），則Oracle客戶端的庫和Oracle伺服器之間可能會出現問題。 為了避免這些問題

1. 確保使用 **完整客戶端**。

   使用Oracle即時客戶端版本時發現了各種問題。 此外，無法更改即時客戶端上的時區檔案。

1. 確保 **客戶端版本** 和 **資料庫伺服器版本** 是 **相同**。

   儘管Oracle的相容性矩陣和調整客戶端和伺服器版本的建議，但混合使用版本是會導致問題的。

   另請檢查ORACLE_HOME值，確保它指向預期的客戶端版本（如果電腦上安裝了多個版本）。

1. 確保客戶端和伺服器使用相同 **時區檔案**。

### DB2 {#db2}

支援的庫版本為 **libdb2.so**。

## 實施步驟 {#implementation-steps}

Adobe CampaignLinux安裝必須按以下順序進行：伺服器安裝後是實例配置。

本章介紹了安裝過程。 安裝步驟如下：

* 步驟1:安裝應用程式伺服器，請參閱 [使用Linux安裝軟體包](../../installation/using/installing-packages-with-linux.md)。
* 步驟2:與Web伺服器整合（可選，具體取決於部署的元件）。

安裝步驟完成後，您需要配置實例、資料庫和伺服器。 有關此內容的詳細資訊，請參閱 [關於初始配置](../../installation/using/about-initial-configuration.md)。
