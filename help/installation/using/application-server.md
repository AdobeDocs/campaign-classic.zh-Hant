---
title: 應用程式伺服器
seo-title: 應用程式伺服器
description: 應用程式伺服器
seo-description: null
page-status-flag: never-activated
uuid: 837c6a5c-53a4-4d1b-a084-9cf77e7a0eee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 7a9e028c-255d-4aad-9827-d19f9a7897b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 應用程式伺服器{#application-server}

必要的資料庫存取層必須安裝在伺服器上，並可從Adobe Campaign帳戶存取。

## Java開發套件- JDK {#java-development-kit---jdk}

動態網頁產生器採用JSP 1.2技術。 為此，應用程式中會包含Tomcat引擎（來自Apache）。 它需要安裝Java開發套件(JDK)，此套件會安裝在Adobe Campaign應用程式所在的所有伺服器上。

您必須先在要執行Adobe Campaign應用程式伺服器(**nlserver web** process)的電腦上安裝JDK，因為它整合了Servlet容器Apache Tomcat，用來產生動態網頁（報表、Web表單等）。

此應用程式已獲得Oracle和 **OpenJDK開發的Java開發套件(JDK)的批准**。

支援的版本在「相容性」 [表中詳述](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

>[!NOTE]
>
>它可以使用電腦上其他應用程式已使用的相應JDK版本進行安裝。
>  
>安裝時，您不需要執行與網頁瀏覽器的整合。
>
>在僅執行傳送代理(**nlserver mta** process)或工作流伺服器(**nlserver wfserver process** )的機器上，不需要安裝JDK。

要下載Java JDK，請連接到： [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html)。

**警告：您必須下載JDK，而不是JRE。**

>[!CAUTION]
>
>為保留平台操作效能並確保與已安裝版本相容，您必須在Windows和Linux中禁用自動JDK更新功能。

要在Linux環境中安裝JDSL，最好使用軟體包管理器。

在Debian 7和8中，使用下列命令：

```
aptitude install openjdk-7-jdk
```

對於RHEL 6，請使用下列命令：

```
yum install java-1.8.0-openjdk
```

對於RHEL 7，請使用下列命令：

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

在Linux中，必須安裝OpenSSL。 Adobe Campaign支援的版本 **為OpenSSL 1.0.1****和OpenSSL 0.9.8**。 接受0.9.8g至0.9.8o的子版本。

>[!NOTE]
>
>對於RHEL 6和CentOS 6，需要openSSL 1.0。

## 匯出報表 {#exporting-reports}

Adobe Campaign可讓您以Microsoft excel和Adobe PDF格式匯出平台報表。 對於Microsoft excel格式，Adobe Campaign使用 **LibreOffice**。 對於Adobe PDF格式，Adobe Campaign會使用 **PhantomJS轉換程式** 。 PhantomJs包含在出廠包中，且LibreOffice必須安裝在Adobe Campaign應用程式伺服器在(**nlserver web** process)上執行的機器上。

>[!NOTE]
>
>對於Linux，您需要新增字型。 如需詳細資訊，請參閱「字型」 [以取得MTA統計資料](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)。

## SpamAssassin {#spamassassin}

SpamAssassin可讓您指派分數給電子郵件，以判斷接收時使用的反垃圾郵件工具是否會將郵件風險視為不需要。 安裝是可選的。

SpamAssassin將電子郵件視為不想要的，完全以篩選和計分規則為基礎。 因此，您必須每天至少更新這些規則一次，才能讓SpamAssassin安裝及其與Adobe Campaign的整合功能完整運作，並確保在傳送前指派給傳送的分數相關性。 此更新由代管SpamAssassin的伺服器管理員負責。

支援的最低版本為： **3.2.5** 和 **3.3.2**.

SpamAssassin需要HTTP網際網路存取(tcp/80)。

在配置SpamAssassin中將顯示SpamAssassin的安裝和 [配置階段](../../installation/using/configuring-spamassassin.md)。
