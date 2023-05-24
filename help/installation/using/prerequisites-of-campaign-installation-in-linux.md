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

# 在Linux上安裝Campaign的必要條件{#prerequisites-of-campaign-installation-in-linux}



## 軟體先決條件 {#software-prerequisites}

本節詳細說明安裝Adobe Campaign之前所需的初步設定步驟。

安裝Adobe Campaign所需的技術和軟體設定已詳載於 [相容性矩陣](../../rn/using/compatibility-matrix.md).

提醒您，需要安裝並正確設定下列元件：

* Apache，請參閱 [相容性矩陣](../../rn/using/compatibility-matrix.md)，
* Java JDK和OpenJDK，請參閱 [Java開發套件 — JDK](../../installation/using/application-server.md#java-development-kit---jdk)，
* 程式庫，請參閱 [資料庫](#libraries)，
* 資料庫存取層，請參閱 [資料庫存取層](#database-access-layers)，
* LibreOffice，請參閱 [安裝LibreOffice for Debian](#installing-libreoffice-for-debian) 和 [安裝LibreOffice for CentOS](#installing-libreoffice-for-centos)，
* 字型，請參閱 [MTA統計資料的字型](#fonts-for-mta-statistics) 和 [日文執行個體的字型](#fonts-for-japanese-instances).

>[!NOTE]
>
>若要在CentOS 7和Debian 8平台上安裝低於或等於8709的組建版本，必須啟用apache access_compat模組。

### 資料庫 {#libraries}

若要在Linux中安裝Adobe Campaign，請確定您有必要的程式庫。

* 程式庫C必須能夠支援TLS （執行緒本機儲存）模式。 除了某些已停用Xen支援的核心以外，此模式在大多數情況下是作用中的。

   若要檢查此專案，您可以使用 **uname -a |灰黃** 命令為例。

   如果命令未傳回任何內容（空白行），則表示設定正確。

* 您必須有OpenSSL版本 **1.0.2** 或更高。

   對於RHEL 7/8發行版本，需要1.0版本的OpenSSL。

* 若要使用Adobe Campaign，您必須具備 **利比庫** 程式庫已安裝。

   以下版本的 **利比庫** 支援（32位元或64位元）：

   * RHEL 7/8、CentOS 7：libicu50
   * Debian 8： libicu52
   * Debian 9： libicu57

   若要使用Adobe Campaign，您必須安裝libc-ares程式庫。 在RHEL/CentOS上，執行下列命令：

   ```
   yum install c-ares
   ```

   在Debian上：

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

使用時，必須正確設定SELinux模組。

要執行此操作，請以root身份登入並輸入以下命令：

```
echo 0 >/selinux/enforce
```

除此之外，在 **/etc/sysconfig/httpd** 檔案中，新增了以下行以參照Adobe Campaign環境設定指令碼：

```
. ~neolane/nl6/env.sh
```

在RHEL和CentOS中，啟用SELinux時會發現資料庫的使用者端層存在相容性問題。 為確保Adobe Campaign能夠正常運作，建議您停用SELinux。

**套用下列程式：**

* 編輯檔案 **/etc/selinux/config**

* 修改SELINUX行，如下所示：

```
SELINUX=disabled
```

### MTA統計資料的字型 {#fonts-for-mta-statistics}

若要正確顯示MTA統計資料(nms/fra/jsp/stat.jsp)的報告，請新增字型。

在Debian中，新增命令：

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

在Redhat中，使用以下命令：

* 若為CentOS/RHEL 7：

   ```
   yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
   ```

* 對於RHEL 8：

   ```
   dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
   ```

### 日文執行個體的字型 {#fonts-for-japanese-instances}

日文例項需要特定字元的字型，才能將報表匯出為PDF格式。

在Debian中，新增命令：

```
aptitude install fonts-ipafont
```

在Red Hat中，新增命令：

* 對於RHEL 7：

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

* 對於RHEL 8：

   ```
   dnf install vlgothic-fonts
   ```

### 安裝LibreOffice for Debian {#installing-libreoffice-for-debian}

對於Debian，需要下列設定：

1. 安裝下列標準套件：

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. 安裝下列字型（可選用，但強烈建議用於日文執行個體）：

   ```
   apt-get install fonts-ipafont
   ```

### 安裝LibreOffice for CentOS {#installing-libreoffice-for-centos}

CentOS需要下列設定：

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## 資料庫存取層 {#database-access-layers}

您使用的資料庫引擎存取層必須安裝在伺服器上，並可透過Adobe Campaign帳戶存取。 版本和安裝模式可能會因使用的資料庫引擎而異。

支援的試行方案版本詳見 [相容性矩陣](../../rn/using/compatibility-matrix.md).

同時檢查一般 [資料庫](../../installation/using/database.md) 區段。

### PostgreSQL {#postgresql}

Adobe Campaign支援7.2版的PostgreSQL使用者端程式庫所有版本： (**libpq.so.5**， **libpq.so.4**， **libpq.so.3.2** 和 **libpq.so.3.1**)。

搭配Adobe Campaign使用PostgreSQL也需要安裝對應的 **pgcrypto** 程式庫。

### Oracle {#oracle}

擷取64位元Debian的程式庫版本，即： **libclntsh.so**， **libclntsh.so.11.1** 和 **libclntsh.so.10.1**.

您可以從Oracle技術網路取得Linux RPM套件。

>[!NOTE]
>
>如果您已安裝Oracle使用者端，但全域環境（例如： /etc/profile）未正確設定，您可以將遺漏的資訊新增至 **nl6/customer.sh** 指令碼如需詳細資訊，請參閱 [環境變數](../../installation/using/installing-packages-with-linux.md#environment-variables).

**疑難排解和最佳作法**

在Oracle使用者端或伺服器更新、版本變更或第一次安裝執行個體時，可能會出現問題。

如果您在使用者端主控台上注意到記錄、工作流程上次處理、下次處理等作業有非預期的時間延遲（一小時以上），則Oracle使用者端的程式庫和Oracle伺服器之間可能會發生問題。 若要避免這類問題

1. 請務必使用 **完整使用者端**.

   在使用Oracle即時使用者端版本時，已識別出各種問題。 此外，即時使用者端也不可能變更時區檔案。

1. 請確定 **使用者端版本** 和 **資料庫伺服器版本** 是 **相同**.

   儘管有Oracle的相容性矩陣，以及調整使用者端和伺服器版本的建議，但混用版本已知會導致問題。

   同時請檢查ORACLE_HOME值，確定它指向預期的使用者端版本（如果電腦上安裝有多個版本）。

1. 請確定使用者端和伺服器使用相同的 **時區檔案**.

### DB2 {#db2}

支援的程式庫版本為 **libdb2.so**.

## 實施步驟 {#implementation-steps}

適用於Linux的Adobe Campaign安裝必須依下列順序執行：伺服器安裝，然後執行個體設定。

本章將說明安裝程式。 安裝步驟如下：

* 步驟1：安裝應用程式伺服器，請參閱 [使用Linux安裝套件](../../installation/using/installing-packages-with-linux.md).
* 步驟2：與Web伺服器整合（選擇性，視部署的元件而定）。

安裝步驟完成後，您需要設定執行個體、資料庫和伺服器。 有關詳細資訊，請參閱 [關於初始設定](../../installation/using/about-initial-configuration.md).
