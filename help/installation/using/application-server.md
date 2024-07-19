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
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 1%

---

# 應用程式伺服器{#application-server}

必要的資料庫存取層必須安裝在伺服器上，並可從Adobe Campaign帳戶存取。

## Java開發套件 — JDK {#jdk}

Java Development Kit （簡稱JDK）是軟體開發套件。 它是啟用Java應用程式和Java Applet開發的基本元件。

動態網頁產生器使用JSP技術。 為此，應用程式中包含Tomcat引擎（來自Apache）。 它需要一個Java開發套件(JDK)，安裝在安裝Adobe Campaign應用程式的所有伺服器上。

您必須先在要執行Adobe Campaign應用程式伺服器（**nlserver web**&#x200B;處理序）的電腦上安裝JDK，因為它整合了servlet容器Apache Tomcat，用於產生動態網頁（報表、網頁表單等）。

此應用程式已針對Oracle開發的Java開發套件(JDK)以及&#x200B;**OpenJDK**&#x200B;核准。

Campaign [相容性矩陣](../../rn/using/compatibility-matrix.md)中詳細說明支援的版本。


>[!AVAILABILITY]
>
>* 從7.4.1版開始，Campaign至少需要Java JDK 11。 如果您的Campaign伺服器安裝在Windows環境中，則必須產生JRE，因為預設不再提供JRE。
>
>* 從v7.4.1開始，Tomcat 10.1是預設版本。
>

### 建議

安裝和升級Java Development Kit時，請套用下列建議：

* Java Development Kit可使用電腦上其他應用程式已使用的適當JDK版本進行安裝。

* 安裝JDK時，不需要與網頁瀏覽器整合。

* 在只執行傳遞代理程式（**nlserver mta**&#x200B;處理序）或工作流程伺服器（**nlserver wfserver**&#x200B;處理序）的電腦上，不需要安裝JDK。

* 升級Java版本時，必須先解除安裝舊版。 安裝在同一台電腦上的兩個Java版本都可能會造成衝突。

  身為內部部署客戶，您可以檢查`LD_LIBRARY_PATH` [環境變數](installing-packages-with-linux.md#environment-variables)是否已設定為最新版本(例如： java11)。 如果設定為舊版(例如： Java8)，則需要更新。 若為JDK 11，尋找JDK資料庫的路徑為`/usr/lib/jvm/java-11-openjdk-amd64/lib`。


### 安裝步驟

Java Development Kit是平台專屬的：每個作業系統都需要個別的安裝程式。

若要下載JDK，請連線至[Oracle網站](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}。

>[!CAUTION]
>
> 請務必下載Java開發套件(JDK)，而不是Java執行階段環境(JRE)。


若要在Linux環境中安裝JDSL，Adobe建議使用封裝管理員。

對於Debian，請使用下列指令：

```sql
apt install openjdk-11-jdk-headless
```

對於RHEL，請使用下列指令：

```sql
dnf install java-11-openjdk-headless
```



## 匯出報告 {#exporting-reports}

您可以使用Adobe Campaign將報表匯出至Microsoft Excel和Adobe PDF。

* 若為Microsoft Excel格式，Adobe Campaign需仰賴&#x200B;**LibreOffice**。

* 對於Adobe PDF格式，Adobe Campaign使用&#x200B;**PhantomJS**&#x200B;轉換工具。 PhantomJs包含在工廠套件中，且LibreOffice必須安裝在（**nlserver web**&#x200B;處理序）上執行Adobe Campaign應用程式伺服器的電腦上。

>[!NOTE]
>
>針對Linux，您需要新增字型。 如需詳細資訊，請參閱[MTA統計資料的](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics)字型。

## SpamAssassin {#spamassassin}

SpamAssassin可讓您為電子郵件指派分數，以判斷接收時所使用的反垃圾郵件工具是否會將訊息風險視為不想要的。 安裝是選擇性的。

SpamAssassin會將電子郵件限定為不受歡迎，這完全是根據篩選和評分規則。 因此，這些規則必須每天至少更新一次，才能讓您的SpamAssassin安裝及其與Adobe Campaign的整合全面運作，並確保在傳送之前指派給您傳送的評分具有相關性。 此更新由裝載SpamAssassin的伺服器管理員負責。

支援的最低版本為： **3.4**

SpamAssassin需要HTTP網際網路存取(tcp/80)。

在[設定SpamAssassin](../../installation/using/configuring-spamassassin.md)中顯示SpamAssassin的安裝和設定階段。
