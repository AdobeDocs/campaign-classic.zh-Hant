---
solution: Campaign Classic
product: campaign
title: 應用程式伺服器
description: 應用程式伺服器
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---


# 應用程式伺服器{#application-server}

必要的資料庫存取層必須安裝在伺服器上，並可從Adobe Campaign帳戶存取。

## Java開發套件- JDK {#java-development-kit---jdk}

動態網頁產生器採用JSP 1.2技術。 為此，應用程式中會包含Tomcat引擎（來自Apache）。 它需要安裝Java開發套件(JDK)，此套件會安裝在Adobe Campaign應用程式所在的所有伺服器上。

您必須先在要執行Adobe Campaign應用程式伺服器（**nlserver web**&#x200B;程式）的電腦上安裝JDK，因為它整合了用於產生動態網頁（報表、Web表單等）的servlet容器Apache Tomcat。

此應用程式已經獲得Oracle開發的Java開發套件(JDK)以及&#x200B;**OpenJDK**&#x200B;的批准。

支援的版本詳見Campaign [相容性矩陣](../../rn/using/compatibility-matrix.md)。

>[!NOTE]
>
>它可以使用電腦上其他應用程式已使用的相應JDK版本進行安裝。
>  
>安裝時，您不需要執行與網頁瀏覽器的整合。
>
>在僅執行傳送代理（**nlserver mta**&#x200B;進程）或工作流伺服器（**nlserver wfserver**&#x200B;進程）的機器上，不需要安裝JDK。

要下載Java JDK，請連接到：[https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html)。

**警告：您必須下載JDK，而不是JRE。**

>[!CAUTION]
>
>為保留平台操作效能並確保與已安裝版本相容，您必須在Windows和Linux中禁用自動JDK更新功能。

要在Linux環境中安裝JDSL，最好使用軟體包管理器。

在Debian 8和9中，使用下列命令：

```
aptitude install openjdk-8-jdk
```

對於RHEL 7，請使用下列命令：

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

在Linux中，必須安裝OpenSSL。 Adobe Campaign支援的版本為&#x200B;**OpenSSL 1.0.1**&#x200B;和&#x200B;**OpenSSL 0.9.8**。 接受0.9.8g至0.9.8o的子版本。

## 導出報告{#exporting-reports}

Adobe Campaign可讓您以Microsoft Excel和Adobe PDF格式匯出平台報表。 對於Microsoft Excel格式，Adobe Campaign使用&#x200B;**LibreOffice**。 對於Adobe PDF格式，Adobe Campaign會使用&#x200B;**PhantomJS**&#x200B;轉換程式。 PhantomJs包含在出廠包中，且LibreOffice必須安裝在Adobe Campaign應用程式伺服器在（**nlserver web**&#x200B;程式）上執行的機器上。

>[!NOTE]
>
>對於Linux，您需要新增字型。 如需詳細資訊，請參閱[MTA統計資料的字型](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)。

## SpamAssassin {#spamassassin}

SpamAssassin可讓您指派分數給電子郵件，以判斷接收時使用的反垃圾郵件工具是否會將郵件風險視為不需要。 安裝是可選的。

SpamAssassin將電子郵件視為不想要的，完全以篩選和計分規則為基礎。 因此，您必須每天至少更新這些規則一次，才能讓SpamAssassin安裝及其與Adobe Campaign的整合功能完整運作，並確保在傳送前指派給傳送的分數相關性。 此更新由代管SpamAssassin的伺服器管理員負責。

最低支援版本為：**3.4**

SpamAssassin需要HTTP網際網路存取(tcp/80)。

[配置SpamAssassin](../../installation/using/configuring-spamassassin.md)中顯示了SpamAssassin的安裝和配置階段。
