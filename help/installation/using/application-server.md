---
product: campaign
title: 應用程式伺服器
description: 應用程式伺服器
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 1%

---

# 應用程式伺服器{#application-server}

![](../../assets/v7-only.svg)

必須在伺服器上安裝所需的資料庫存取層，並可從Adobe Campaign帳戶存取。

## Java開發套件 — JDK {#java-development-kit---jdk}

動態網頁生成器採用JSP 1.2技術。 為此，應用程式中包含Tomcat引擎（來自Apache）。 它需要安裝在Adobe Campaign應用程式所安裝的所有伺服器上的Java開發套件(JDK)。

首先，必須在要運行Adobe Campaign應用程式伺服器（**nlserver web**&#x200B;進程）的電腦上安裝JDK，因為它併入了Servlet容器Apache Tomcat，用於生成動態網頁（報告、Web表單等）。

此應用程式已獲得Oracle開發的Java開發套件(JDK)以及&#x200B;**OpenJDK**&#x200B;的批准。

Campaign [相容性矩陣](../../rn/using/compatibility-matrix.md)中會詳細說明支援的版本。

>[!NOTE]
>
>可以使用電腦上其他應用程式已使用的適當JDK版本來安裝它。
>  
>安裝時，您不需要執行與網頁瀏覽器的整合。
>
>在僅執行傳送代理（**nlserver mta**&#x200B;進程）或工作流伺服器（**nlserver wfserver**&#x200B;進程）的電腦上，不需要安裝JDK。

要下載Java JDK，請連接到：[https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html)。

**警告：必須下載JDK，而不是JRE。**

>[!CAUTION]
>
>要保留平台操作效能並確保與安裝的版本相容，必須禁用Windows和Linux中的自動JDK更新功能。

要在Linux環境中安裝JDSL，最好使用包管理器。

在Debian 8和9中，使用下列命令：

```
aptitude install openjdk-8-jdk
```

對於RHEL 7，使用以下命令：

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

在Linux中，必須安裝OpenSSL。 Adobe Campaign支援的版本為&#x200B;**OpenSSL 1.0.1**&#x200B;和&#x200B;**OpenSSL 0.9.8**。 接受子版本0.9.8g至0.9.8o。

## 匯出報表 {#exporting-reports}

Adobe Campaign可讓您匯出Microsoft Excel和Adobe PDF格式的平台報表。 對於Microsoft Excel格式，Adobe Campaign使用&#x200B;**LibreOffice**。 對於Adobe PDF格式，Adobe Campaign使用&#x200B;**PhantomJS**&#x200B;轉換器。 出廠包中包含PhantomJs，且必須將LibreOffice安裝在執行Adobe Campaign應用程式伺服器的電腦上（**nlserver web**&#x200B;進程）。

>[!NOTE]
>
>對於Linux，您需要添加字型。 有關詳細資訊，請參閱[MTA統計資訊字型](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)。

## SpamAssassin {#spamassassin}

SpamAssassin可讓您為電子郵件指派分數，以判斷接收時使用的反垃圾郵件工具是否會將郵件視為不可取。 安裝是可選的。

SpamAssassin將電子郵件認定為不受歡迎的郵件，完全基於篩選和計分規則。 因此，必須每天至少更新一次這些規則，才能讓您的SpamAssassin安裝及其與Adobe Campaign的整合完整運作，並保證在傳送前將分數指派給您的傳送的相關性。 此更新由托管SpamAssassin的伺服器管理員負責。

支援的最低版本為：**3.4**

SpamAssassin需要HTTP Internet訪問(tcp/80)。

[配置SpamAssassin](../../installation/using/configuring-spamassassin.md)中顯示SpamAssassin的安裝和配置階段。
