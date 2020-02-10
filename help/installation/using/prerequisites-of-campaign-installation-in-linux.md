---
title: 在Linux中安裝促銷活動的先決條件
seo-title: 在Linux中安裝促銷活動的先決條件
description: 在Linux中安裝促銷活動的先決條件
seo-description: null
page-status-flag: never-activated
uuid: 65c7af3f-ca1d-4255-b54a-6a3c83af40ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 3e2ccb70-6c0c-435f-9c06-f3e5e40367bb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8ad1a83d40f5a841b01aaeb17fe271b44f2480dd

---


# 在Linux中安裝促銷活動的先決條件{#prerequisites-of-campaign-installation-in-linux}

## 軟體先決條件 {#software-prerequisites}

本節詳細說明安裝Adobe Campaign前所需的初步設定步驟。

安裝Adobe Campaign所需的技術和軟體組態詳見「相容性」 [表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

提醒您，必須安裝並正確設定下列元件：

* Apache，請參閱 [Compatibility matrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html),
* Java JDK和OpenJDK，請參閱 [Java開發套件- JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* 程式庫，請參閱 [程式庫](#libraries),
* 資料庫訪問層，請參閱數 [據庫訪問層](#database-access-layers),
* LibreOffice，請參閱「 [安裝LibreOffice for Debian](#installing-libreoffice-for-debian) 」和「 [安裝LibreOffice for CentOS](#installing-libreoffice-for-centos)」
* 字型，請參閱「字 [體」以取得MTA統計資料](#fonts-for-mta-statistics) , [以及「日文字型」](#fonts-for-japanese-instances)。

>[!NOTE]
>
>若要在CentOS 7和Debian 8平台上安裝低於或等於8709的組建版本，必須啟用apache access_compat模組。

### 資料庫 {#libraries}

若要在Linux中安裝Adobe Campaign，請確定您有必要的程式庫。

* 庫C必須能夠支援TLS（線程本地儲存）模式。 除了已禁用Xen支援的某些內核外，此模式在大多數情況下都處於活動狀態。

   若要檢查此項，您可以使 **用uname -a|例如grep xen** 命令。

   如果命令未傳回任何內容（空行），表示配置正確。

* 您必須 **有0.9.8** 或 **1.0** 版OpenSSL。

   對於RHEL 7和CentOS 6散發，需要1.0版的OpenSSL。

* 若要使用Adobe Campaign，您必須安裝 **libicu** library。

   支援下列 **版本** （32位元或64位元）:

   * RHEL 6、SLES、CentOS 6:libicu4.2
   * RHEL 7, CentOS 7:libicu50
   * 德比安七：libicu48
   * 德比安8:libicu52
   * 德比安九：libicu57
   若要使用Adobe Campaign，您必須安裝libc-ares程式庫。 在RHEL/CentOS上，運行以下命令：

   ```
   yum install c-ares
   ```

   德比安：

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

使用時，必須正確配置SELinux模組。

要執行此操作，請以root用戶身份登錄並輸入以下命令：

```
echo 0 >/selinux/enforce
```

除此之外，在 **** /etc/sysconfig/httpd檔案中，已新增下列行以參考Adobe Campaign環境設定指令碼：

```
. ~neolane/nl6/env.sh
```

在RHEL和CentOS中，當啟用SELinux時，會發現與資料庫客戶端層的相容性問題。 為確保Adobe Campaign能夠正確運作，我們建議停用SELinux。

**套用下列程式：**

* 編輯文 **件/etc/selinux/config**

* 按如下方式修改SELINUX行：

```
SELINUX=disabled
```

### MTA統計資料的字型 {#fonts-for-mta-statistics}

若要正確顯示MTA統計資料(nms/fra/jsp/stat.jsp)的報表，請新增字型。

在Debian中，添加命令：

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

在Redhat中，使用以下命令：

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### 日文例項的字型 {#fonts-for-japanese-instances}

日文例項需要特定字元的字型，才能將報表匯出為PDF格式。

在Debian中，添加命令：

```
aptitude install fonts-ipafont
```

在Red hat中，添加命令：

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### 安裝LibreOffice for Debian {#installing-libreoffice-for-debian}

對於Debian，需要以下配置：

1. 安裝下列標準套件：

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. 安裝下列字型（日文例項建議選用但強烈建議使用）:

   ```
   apt-get install fonts-ipafont
   ```

### 安裝CentOS專用的LibreOffice {#installing-libreoffice-for-centos}

CentOS需要下列組態：

1. 安裝下列標準套件：

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. 安裝下列字型（可選，但強烈建議使用日文例項）:

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## 資料庫訪問層 {#database-access-layers}

您所使用之資料庫引擎的存取層必須安裝在伺服器上，並可透過Adobe Campaign帳戶存取。 版本和安裝模式可能會因所使用的資料庫引擎而異。

支援的試用版在「相容性」表中 [有詳細說明](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

另請檢查常規 [資料庫](../../installation/using/database.md) 部分。

### PostgreSQL {#postgresql}

Adobe Campaign支援7.2版的所有PostgreSQL用戶端程式庫版本：(**libpq.so.5**、 **libpq.so.4**、 **libpq.3.2** 和 **** libpq.so.3.1)。

搭配使用PostgreSQL和Adobe Campaign也需要安裝對應的 **pgcrypto** libraries。

### Oracle {#oracle}

擷取64位元Debian的程式庫版本，例如： **libclntsh.so**、 **libclntsh.so.11.1****和** libclntsh.so.10.1。

您可以從Oracle技術網路獲取Linux RPM包。

>[!NOTE]
>
>如果您已經安裝了Oracle客戶端，但已安裝了全局環境(例如：/etc/profile)未正確設定，您可以將遺失的資訊新增至 **nl6/customer.sh** Script。如需詳細資訊，請參閱 [環境變數](../../installation/using/installing-packages-with-linux.md#environment-variables)。

**疑難排解與最佳實務**

在Oracle客戶端或伺服器更新、版本更改或實例的首次安裝後，可能會出現問題。

如果您在客戶端控制台上發現日誌、工作流上次處理、下次處理等中存在意外的時間延遲（一個或多個小時），則Oracle客戶端庫和Oracle server之間可能存在問題。 為避免此類問題

1. 請務必使用完整 **的用戶端**。

   在使用Oracle Instant Client版本時發現了各種問題。 此外，無法更改即時客戶端上的時區檔案。

1. 請確定客戶端 **版本** ，資料 **庫伺服器版本******&#x200B;相同。

   儘管Oracle的相容性清單和建議使客戶端和伺服器版本一致，但混合使用版本仍然會導致問題。

   另請檢查ORACLE_HOME值，以確保它指向預期的客戶機版本（在電腦上安裝多個版本時）。

1. 請確定客戶端和伺服器使用相同的 **時區檔案**。

### DB2 {#db2}

支援的程式庫版 **本為libdb2.so**。

## 實施步驟 {#implementation-steps}

Adobe Campaign的Linux安裝必須依下列順序進行：伺服器安裝後跟實例配置。

本章介紹了安裝過程。 安裝步驟如下：

* 步驟1:安裝應用程式伺服器，請參 [閱安裝Linux軟體包](../../installation/using/installing-packages-with-linux.md)。
* 步驟2:與Web伺服器整合（視部署的元件而定，為可選）。

安裝步驟完成後，您需要配置實例、資料庫和伺服器。 有關詳細資訊，請參閱關於 [初始配置](../../installation/using/about-initial-configuration.md)。
