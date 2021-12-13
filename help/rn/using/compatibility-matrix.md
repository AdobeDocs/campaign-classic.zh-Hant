---
product: campaign
title: Campaign Classic 相容性矩陣
description: Campaign Classic 相容性矩陣
feature: Overview
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: f7c4603e389b19c057ee72bb50ed30d03b60f4bc
workflow-type: ht
source-wordcount: '652'
ht-degree: 100%

---

# 相容性比較表{#compatibility-matrix}

![](../../assets/v7-only.svg)

本文件列出 [最新版本編號](../../rn/using/latest-release.md)之 **Adobe Campaign Classic v7** 支援的所有系統及元件。此清單上未列出的產品和版本即與 Adobe Campaign 不相容。

如果您是 [!DNL Gold Standard] 使用者，請參閱 [[!DNL Gold Standard]  相容性矩陣](../../rn/using/compatibility-matrix-gs.md)。

## 重要備註{#important-notes}

除非另有提及，否則支援所有次要版本。

在其[最新建置版本](../../rn/using/latest-release.md)中，Adobe Campaign Classic 與此頁面列出的所有系統和工具相容。這些協力廠商系統和工具的特定版本生命週期結束 (EOL) 時，Adobe Campaign 不再與那些版本相容：我們將不再使用這些系統和功能，後續的產品發行版本亦會將這些系統和功能從我們的相容性矩陣移除。請確保您使用相容性矩陣列出的任何系統的支援版本，以避免出現任何問題。

若要進一步瞭解已棄用的項目，請瀏覽[本頁面](../../rn/using/deprecated-features.md)。

>[!CAUTION]
>
>此矩陣會定期更新、新增支援的項目，並會移除已啟用的項目。

## 作業系統{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x（64 位元） </br><strong>重要：</strong> CentOS Linux 8 即將於 2021 年 12 月 31 日結束生命週期 (EOL)。 如需詳細資訊，請參閱<a href="../../rn/using/deprecated-features.md">已棄用功能</a>頁面。</p>
<p>7.x（64 位元）</p>
<p><strong>重要：</strong>如果您使用 RHEL，您必須願意停用 SELinux，或讓架構設計人員編寫自訂 SELinux 規則，以檢查啟用的 SELinux 是否不會造成 Campaign 作業的問題。</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>10（64 位元）</p>
<p>9（64 位元）</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x（64 位元）</p>
<p>7.x（64 位元）</p>
<p><strong>重要：</strong>如果您使用 RHEL，您必須願意停用 SELinux，或讓架構設計人員編寫自訂 SELinux 規則，以檢查啟用的 SELinux 是否不會造成 Campaign 作業的問題。</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

## 網頁伺服器{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>Windows Server 2016 上的 10.0</p>
<p>Windows Server 2012 R2 上的 8.5</p>
<p>Windows Server 2012 上的 8.0 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 for RHEL7 - CentOS 7、Debian 8/9、Windows（64 位元）</p>
</td>
</tr>
</tbody>
</table>

## 工具{#Tools}

<table>
<tbody>
<tr>
<td>Java 開發套件 (JDK)</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p>此應用程式已獲得核准，而可用於 Oracle 及 OpenJDK 開發的 Java 開發套件 (JDK)。</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6（及舊版，若是內嵌在您的系統中）</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

## 關係資料庫管理系統 (RDBMS){#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p><strong>請注意：</strong>您也可以將 Amazon RDS for PostgreSQL 與上述指定版本搭配使用。</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 及 SP2</p>
<p><strong>警告：</strong>當 Campaign 伺服器在 Linux 上執行時，不支援 Microsoft SQL Server 作為主要資料庫。<a href="../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers">了解更多</a>。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS 驅動程式必須與 RDBMS 伺服器版本相符。
>
>* PostgreSQL 是托管環境的 RDBMS。


## CRM 連接器{#CRMconnectors}

與 Adobe Campaign 相容的客戶關係管理 (CRM) 系統列於下方。 [進一步瞭解](../../platform/using/crm-connectors.md) Campaign CRM 連接器。

<table>
<tbody>
<tr>
<td>Salesforce 連接器 API</td>
<td>
<p>API 49 版本</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics 連接器</td>
<td>
<p>Web API</p>
</td>
</tr>
</tbody>
</table>

## 同盟資料存取 (FDA){#FederatedDataAccessFDA}

與 Adobe Campaign [同盟資料存取模組](../../installation/using/about-fda.md)相容的外部資料庫如下所列。

<table>
<tbody>
<tr>
<td>Vertica</td>
<td> </td>
</tr>
<tr>
<td>Google Big Query</td>
<td> </td>
</tr>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 及 SP2</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>第 1 版 SPS 12</p>
</td>
</tr>
<tr><td>透過 HiveSQL 提供的 Hadoop</td>
<td>
<p>HortonWorks HDP 2.4.X、2.5.x、2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4)、3.5 (HDP 2.5)、3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## 用戶端主控台 {#ClientConsoleoperatingsystems}

使用 [Campaign 用戶端主控台](../../installation/using/installing-the-client-console.md)時，需要&#x200B;**使用**&#x200B;下列作業系統和瀏覽器。

### 作業系統

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10（建議用於日文執行個體）</p>
</td>
</tr>
</tbody>
</table>

### 瀏覽器

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>


## 行動 SDK{#MobileSDK}

您可以在下列作業系統上使用 Campaign 來傳送推播通知[，使用相關聯的[行動 SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)。](../../delivery/using/about-mobile-app-channel.md)

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x、8.x、9.0</p>
<p>搭配行動 SDK 建置版本 1.0.27。</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>與行動 SDK 建置版本 1.0.26 相容，與 32 及 64 位元版本相容。</p>
</td>
</tr>
</tbody>
</table>

## 瀏覽器{#Browsers}

下列瀏覽器與 Campaign for [Web Access](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-) 相容。

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>最新版本</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>


## 更多相關資訊{#Morelikethis}

* [Campaign Classic 發行說明](../../rn/using/latest-release.md)
* [Campaign 一般架構](../../installation/using/general-architecture.md)
* [硬體尺寸建議](../../technotes/using/hardware-sizing.md)
* [已棄用的功能及系統](../../rn/using/deprecated-features.md)
* [組建升級程序](../../production/using/build-upgrade.md)
