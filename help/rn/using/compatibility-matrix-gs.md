---
solution: Campaign Classic
product: campaign
title: 促銷活動的相容性矩陣 [!DNL Gold Standard]
description: ' [!DNL Gold Standard] 版本的Campaign Classic相容性表'
feature: 概觀
role: 業務從業人員
level: 初學者
translation-type: tm+mt
source-git-commit: b77a56a97e499f60c092fae45c7809f7bfd9f2ea
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 98%

---


# [!DNL Gold Standard] 相容性矩陣{#compatibility-matrix-gs}

本文件列出 **Adobe Campaign Classic[!DNL Gold Standard]** 19.1 建置版本支援的所有系統和元件。不屬於此清單的產品和版本與此版本的 Adobe Campaign 不相容。

## 重要附註{#important-notes-gs}

除非另有提及，否則支援所有次要版本。

Adobe Campaign Classic 與此頁面列出的所有系統和工具相容。這些協力廠商系統和工具的特定版本生命週期結束 (EOL) 時，Adobe Campaign 不再與那些版本相容：我們將不再使用這些系統和功能，後續的產品發行版本亦會將這些系統和功能從我們的相容性矩陣移除。請確保您使用相容性矩陣列出的任何系統的支援版本，以避免出現任何問題。

## 作業系統{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x（64 位元）</p>
<p>7.x（64 位元）</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9（64 位元）</p>
<p>8（64 位元）</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
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

## Web 伺服器{#WebServers-gs}

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
<p>2.2 for RHEL6 - 僅限於 CentOS 6（64 位元）</p>
</td>
</tr>
</tbody>
</table>

## 工具{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java 開發套件 (JDK)</td>
<td>
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

## RDBMS 伺服器{#RDBMSservers-gs}

>[!NOTE]
>
>RDBM S驅動程式必須與 RDBMS 伺服器版本相符。

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>注意：您也可以將 Amazon RDS for PostgreSQL 與上述指定版本搭配使用。</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016年</p>
<p>2014</p>
<p>2012 - SP1 及 SP2</p>
<p>警告：當 Campaign 伺服器在 Linux 上執行時，不支援 Microsoft SQL Server 作為主要資料庫。<a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">進一步瞭解</a>。</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>警告：不允許針對新安裝使用 DB2 UDB。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL 是託管環境的預設資料庫伺服器。

## CRM 連接器{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Salesforce 連接器 API</td>
<td>
<p>API 37 版</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API 21 版</p>
<p>API 15 版</p>
</td>
</tr>
<tr><td>Oracle On Demand API</td>
<td>
<p>網站服務1.0 版API</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap API - 內部部署：2007、2015、2016 年</p>
<p>Soap API - 線上：2015、2016 年</p>
<p>Web API - 內部部署與線上：365、2016、2016 更新 1</p>
</td>
</tr>
</tbody>
</table>

## 同盟資料存取 (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019年</p>
<p>2017年</p>
<p>2016年</p>
<p>2014年</p>
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
</td>
</tr>
</tbody>
</table>

## 用戶端控制台作業系統{#ClientConsoleoperatingsystems-gs}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2016年</p>
<p>2012年</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>Seven</p>
<p>8</p>
<p>10（建議用於日文執行個體）</p>
</td>
</tr>
</tbody>
</table>

## 行動 SDK{#MobileSDK-gs}

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

## 瀏覽器{#Browsers-gs}

對於下列瀏覽器，支援最新版本：Microsoft Edge、Mozilla Firefox、Google Chrome、Safari。

支援 Internet Explorer 11。

## 比較喜歡此內容{#Morelikethis-gs}

* [Campaign Classic 發行說明](../../rn/using/latest-release.md)
* [安裝指南](../../installation/using/general-architecture.md)
* [已棄用的功能及系統](../../rn/using/deprecated-features.md)
* [建立升級程序](https://helpx.adobe.com/tw/campaign/kb/acc-build-upgrade.html)
