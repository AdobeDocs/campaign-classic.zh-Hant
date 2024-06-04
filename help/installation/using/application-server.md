---
product: campaign
title: 應用程式伺服器
description: 應用程式伺服器
feature: Installation
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 7e1c3b256cf43232e49d9daa0bf44d1e114b565b
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 1%

---

# 應用程式伺服器{#application-server}

必要的資料庫存取層必須安裝在伺服器上，並可從Adobe Campaign帳戶存取。

## Java開發套件 — JDK {#java-development-kit---jdk}

Java Development Kit （簡稱JDK）是軟體開發套件。 它是啟用Java應用程式和Java Applet開發的基本元件。

動態網頁產生器使用JSP 1.2技術。 為此，應用程式中包含Tomcat引擎（來自Apache）。 它需要一個Java開發套件(JDK)，安裝在安裝Adobe Campaign應用程式的所有伺服器上。

您必須先在要執行Adobe Campaign應用程式伺服器的電腦上安裝JDK (**nlserver web** 程式)，因為它合併了servlet容器Apache Tomcat，用於產生動態網頁（報表、網路表單等）。

此應用程式已獲核准用於Oracle開發的Java開發套件(JDK)以及用於 **OpenJDK**.

Campaign中會詳細說明支援的版本 [相容性矩陣](../../rn/using/compatibility-matrix.md).


### 建議

安裝和升級Java Development Kit時，請套用下列建議：

* Java Development Kit可使用電腦上其他應用程式已使用的適當JDK版本進行安裝。

* 安裝JDK時，不需要與網頁瀏覽器整合。

* 在只執行傳遞代理程式的機器上(**nlserver mta** process)或工作流程伺服器(**nlserver wfserver** 程式)，則不需要安裝JDK。

* 若要保留平台作業效能並確保與已安裝版本的相容性，您必須在Windows和Linux中停用自動JDK更新功能。

* 升級Java版本時，必須先解除安裝舊版。 安裝在同一台電腦上的兩個Java版本都可能會造成衝突。

  身為內部部署客戶，您可以檢查 `LD_LIBRARY_PATH` [環境變數](installing-packages-with-linux.md#environment-variables) 設為最新版本(例如： java11)。 如果設定為舊版(例如： Java8)，則需要更新。 若為JDK 11，尋找JDK程式庫的路徑為 `/usr/lib/jvm/java-11-openjdk-amd64/lib`.


### 安裝步驟

Java Development Kit是平台專屬的：每個作業系統都需要個別的安裝程式。

若要下載JDK，請連線至 [oracle網站](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}.

>[!CAUTION]
>
> 請務必下載Java開發套件(JDK)，而不是Java執行階段環境(JRE)。


若要在Linux環境中安裝JDSL，Adobe建議使用封裝管理員。

對於Debian，請使用下列指令：

```sql
aptitude install openjdk-8-jdk
```

對於RHEL，請使用下列指令：

```sql
yum install java-1.8.0-openjdk
```


## OpenSSL {#openssl}

在Linux中，必須安裝OpenSSL。 Adobe Campaign支援OpenSSL 1.0.2版或更新版本。

## 匯出報告 {#exporting-reports}

您可以使用Adobe Campaign將報表匯出至Microsoft Excel和Adobe PDF。

* 對於Microsoft Excel格式，Adobe Campaign依賴於 **LibreOffice**.

* 對於Adobe PDF格式，Adobe Campaign使用 **PhantomJS** 轉換工具。 PhantomJs包含在工廠套件中，且LibreOffice必須安裝在執行Adobe Campaign應用程式伺服器的電腦上(**nlserver web** 流&#39;b5&#39;7b)。

>[!NOTE]
>
>針對Linux，您需要新增字型。 有關詳細資訊，請參閱 [MTA統計資料的字型](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

SpamAssassin可讓您為電子郵件指派分數，以判斷接收時所使用的反垃圾郵件工具是否會將訊息風險視為不想要的。 安裝是選擇性的。

SpamAssassin會將電子郵件限定為不受歡迎，這完全是根據篩選和評分規則。 因此，這些規則必須每天至少更新一次，才能讓您的SpamAssassin安裝及其與Adobe Campaign的整合全面運作，並確保在傳送之前指派給您傳送的評分具有相關性。 此更新由裝載SpamAssassin的伺服器管理員負責。

支援的最低版本為： **3.4**

SpamAssassin需要HTTP網際網路存取(tcp/80)。

SpamAssassin的安裝和設定階段會顯示在 [設定SpamAssassin](../../installation/using/configuring-spamassassin.md).
