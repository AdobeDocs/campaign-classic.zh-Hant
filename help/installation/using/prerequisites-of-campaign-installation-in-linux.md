---
product: campaign
title: 在Linux安裝Campaign的必要條件
description: 在 Linux 中安裝Campaign的先決條件
feature: Installation, Instance Settings
badge-v7-prem: label="僅限內部部署/混合部署" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# 在Linux上安裝Campaign的必要條件{#prerequisites-of-campaign-installation-in-linux}

## 軟體先決條件 {#software-prerequisites}

本節詳細說明安裝Adobe Campaign之前所需的初步設定步驟。

安裝Adobe Campaign所需的技術和軟體組態在[相容性矩陣](../../rn/using/compatibility-matrix.md)中有詳細說明。

提醒您，下列元件必須安裝並正確設定：

* Apache，請參閱[相容性矩陣](../../rn/using/compatibility-matrix.md)，
* Java JDK和OpenJDK，請參閱[Java Development Kit - JDK](../../installation/using/application-server.md#jdk)，
* 資料庫，請參閱[資料庫](#libraries)，
* 資料庫存取層，請參閱[資料庫存取層](#database-access-layers)，
* LibreOffice，請參閱[安裝適用於Debian的LibreOffice](#installing-libreoffice-for-debian)和[安裝適用於CentOS的LibreOffice](#installing-libreoffice-for-centos)，
* 字型，請參考[MTA統計資料的字型](#fonts-for-mta-statistics)以及日文執行個體的[字型](#fonts-for-japanese-instances)。


### 圖書館 {#libraries}

要在 Linux 中安裝 Adobe Campaign，請確保您具有所需的資料庫。

* 庫 C 必須能夠支援 TLS（線程本地存儲）模式。 此模式在大多數情況下處於活動狀態，但某些內核已禁用 Xen 支援。

  例如，要檢查這一點，您可以使用 **uname -a | grep xen** 命令。

  如果命令未傳回空白行，則表示設定正確。

* 您必須有OpenSSL版本&#x200B;**1.0.2**&#x200B;或更新版本。

  對於RHEL發行版本，需要OpenSSL 1.0版。

* 若要使用Adobe Campaign，您必須安裝&#x200B;**libicu**&#x200B;資料庫。

### SELinux {#selinux}

使用時，必須正確配置 SELinux 模組。

要執行此操作，請以root身份登入並輸入以下命令：

```
echo 0 >/selinux/enforce
```

除此之外，還在&#x200B;**/etc/sysconfig/httpd**&#x200B;檔案中新增了下列行，以參照Adobe Campaign環境設定指令碼：

```
. ~neolane/nl6/env.sh
```

在RHEL和CentOS中，啟用SELinux時會發現資料庫使用者端層的相容性問題。 為確保Adobe Campaign可正常運作，建議您停用SELinux。

**套用下列處理序：**

* 編輯檔案&#x200B;**/etc/selinux/config**

* 修改SELINUX行，如下所示：

```
SELINUX=disabled
```

### MTA統計資料的字型 {#fonts-for-mta-statistics}

為了正確顯示MTA統計資料(nms/fra/jsp/stat.jsp)的報表，請新增字型。

在Debian中新增命令：

```
apt install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

對RHEL使用下列命令：

```
dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
```

### 日文執行個體的字型 {#fonts-for-japanese-instances}

日文實例必須字型特定字元才能將報表匯出為 PDF 格式。

在 Debian 中，添加命令：

```
apt install fonts-ipafont
```

對於 RHEL，請添加以下命令：

```
dnf install epel-release # if required
dnf install vlgothic-fonts
```

### 安裝LibreOffice for Debian {#installing-libreoffice-for-debian}

對於Debian，需要以下設定：

1. 安裝下列標準套件：

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. 安裝以下字體（可選字體，但強烈建議用於日文實例）：

   ```
   apt-get install fonts-ipafont
   ```

### 安裝 LibreOffice for CentOS {#installing-libreoffice-for-centos}

CentOS 需要以下設定：

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## 資料庫訪問層 {#database-access-layers}

您正在使用的資料庫引擎的訪問層必須安裝在您的伺服器上，並且可以通過Adobe Campaign 帳戶進行訪問。 版本和安裝模式可能會因使用的資料庫引擎而有所不同。

支援的試驗版本在[相容性矩陣](../../rn/using/compatibility-matrix.md)中詳細說明。

同時檢查一般[資料庫](../../installation/using/database.md)區段。

### PostgreSQL {#postgresql}

Adobe Campaign支援9.6版之PostgreSQL使用者端程式庫的所有版本： **libpq.so.5**。

搭配Adobe Campaign使用PostgreSQL也需要安裝對應的&#x200B;**pgcrypto**&#x200B;資料庫。

### Oracle {#oracle}

檢索 64 位 Debian 的 資料庫 版本，即：libclntsh.so、libclntsh.so.19.1 **、libclntsh.so.18.1**、**libclntsh.so.12.1**、**libclntsh.so.11.1** 或 **libclntsh.so.10.1。**&#x200B;**&#x200B;**&#x200B;**&#x200B;**

您可以從 Oracle 技術網路獲取 Linux RPM 軟體包。

>[!NOTE]
>
>如果已安裝 Oracle 用戶端，但全域環境（對於執行個體：/etc/設定檔）未正確配置，則可以將缺少的信息添加到 nl6/客戶.sh 腳本中 **有關詳細信息，請參閱[環境變數](../../installation/using/installing-packages-with-linux.md#environment-variables)。**

**疑難解答和最佳做法**

在Oracle使用者端或伺服器更新、版本變更或首次安裝執行個體時，可能會出現問題。

如果您在使用者端主控台注意到記錄、工作流程上次處理、下次處理等作業中有非預期的時間延遲（一小時以上），則Oracle使用者端的程式庫和Oracle伺服器之間可能會發生問題。 若要避免這類問題

1. 請確定使用&#x200B;**完整使用者端**。

   在使用 Oracle Instant Client 版本時發現了各種問題。 此外，無法在即時用戶端上更改時區檔。

1. 確保&#x200B;**用戶端版本**&#x200B;和&#x200B;**資料庫伺服器版本**&#x200B;**相同**。

   儘管Oracle有相容性矩陣，並且建議調整使用者端和伺服器版本，但混合使用版本已知會導致問題。

   同時請檢查ORACLE_HOME值，確定它指向預期的使用者端版本（如果電腦上安裝了多個版本）。

1. 請確定使用者端和伺服器使用相同的&#x200B;**時區檔案**。

## 實施步驟 {#implementation-steps}

適用於Linux的Adobe Campaign安裝必須依下列順序進行：伺服器安裝，接著執行個體設定。

本章將說明安裝程式。 安裝步驟如下：

* 步驟1：安裝應用程式伺服器，請參閱[使用Linux安裝套件](../../installation/using/installing-packages-with-linux.md)。
* 步驟2：與Web伺服器整合（選擇性，視部署的元件而定）。

安裝步驟完成後，您需要設定執行個體、資料庫和伺服器。 有關詳細資訊，請參閱[關於初始設定](../../installation/using/about-initial-configuration.md)。
