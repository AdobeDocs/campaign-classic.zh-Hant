---
product: campaign
title: 應用程式伺服器
description: 應用程式伺服器
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 1%

---

# 應用程式伺服器{#application-server}



必須在伺服器上安裝所需的資料庫訪問層，並可從Adobe Campaign帳戶訪問。

## Java開發工具包 — JDK {#java-development-kit---jdk}

動態網頁生成器採用JSP 1.2技術。 為此，應用程式中包括一個Tomcat引擎（來自Apache）。 它需要安裝在Adobe Campaign應用程式所在的所有伺服器上的Java開發工具包(JDK)。

必須先在要運行Adobe Campaign應用程式伺服器的電腦上安裝JDK(**nlserver web** 因為它包含一個Servlet容器Apache Tomcat，用於生成動態Web頁（報表、Web表單等）。

該應用程式已被批准用於由Oracle開發的Java開發工具包(JDK)以及 **OpenJDK**。

市場活動中詳細列出了支援的版本 [相容性矩陣](../../rn/using/compatibility-matrix.md)。

>[!NOTE]
>
>可以使用電腦上其他應用程式已使用的相應JDK版本安裝它。
>  
>安裝時，不需要您執行與Web瀏覽器的整合。
>
>在僅執行傳遞代理的電腦上(**nlserver mta** 進程)或工作流伺服器(**nlserver wfserver** 過程)，不需要安裝JDK。

要下載Java JDK，請連接到： [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html)。

**警告：必須下載JDK，而不是JRE。**

>[!CAUTION]
>
>要保留平台操作效能並確保與已安裝版本相容，必須在Windows和Linux中禁用自動JDK更新功能。

要在Linux環境中安裝JDSL，最好使用軟體包管理器。

在Debian 8和9中，使用以下命令：

```
aptitude install openjdk-8-jdk
```

對於RHEL 7，使用以下命令：

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

在Linux中，必須安裝OpenSSL。 Adobe Campaign支援OpenSSL 1.0.2版或更高版本。

## 導出報表 {#exporting-reports}

Adobe Campaign允許您以MicrosoftExcel和Adobe PDF格式導出平台報告。 對於MicrosoftExcel格式，Adobe Campaign使用 **自由辦公室**。 對於Adobe PDF格式，Adobe Campaign使用 **幻影JS** 轉換器。 PhantomJs包含在出廠包中，並且LibreOffice必須安裝在Adobe Campaign應用程式伺服器在(**nlserver web** 處理)。

>[!NOTE]
>
>對於Linux，您需要添加字型。 有關此內容的詳細資訊，請參閱 [MTA統計資訊的字型](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)。

## SpamAssassin {#spamassassin}

SpamAssassin允許您為電子郵件分配分數，以確定接收時使用的反垃圾郵件工具是否認為郵件具有不可取的風險。 安裝是可選的。

SpamAssassin對電子郵件的不受歡迎程度的認定完全基於過濾和評分規則。 因此，必須每天至少更新這些規則一次，以便SpamAssassin的安裝及其與Adobe Campaign的整合能夠充分發揮作用，並確保在發送前分配給您交貨的分數的相關性。 此更新由托管SpamAssassin的伺服器管理員負責。

支援的最低版本為： **3.4**

SpamAssassin需要HTTP Internet訪問(tcp/80)。

SpamAssasin的安裝和配置階段介紹於 [配置SpamAssassin](../../installation/using/configuring-spamassassin.md)。
