---
solution: Campaign Classic
product: campaign
title: 相容性矩陣
description: Campaign Classic相容性矩陣
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 13%

---


# 相容性矩陣{#compatibility-matrix}

本檔案列出最新版 [Adobe Campaign Classic支援的所](../../rn/using/latest-release.md) 有系統 ****&#x200B;和元件。 不屬於此清單的產品和版本與Adobe Campaign不相容。

如果您是Gold Standard使用者，請參閱 [Gold Standard相容性表](../../rn/using/compatibility-matrix-gs.md)。

## 重要附註{#important-notes}

除非另有提及，否則支援所有次要版本。

Adobe Campaign [Classic在其最新版本中](../../rn/using/latest-release.md)，與本頁所列的所有系統和工具相容。 由於這些協力廠商系統和工具的特定版本已與其各自的建立者達成生命週期結束(EOL),Adobe Campaign將不再與這些版本相容，而且會在後續的產品版本中，從我們的相容性矩陣中移除這些版本。 請確保您使用相容性矩陣列出的任何系統的支援版本，以避免出現任何問題。

若要進一步瞭解已過時的項目，請造 [訪本頁](../../rn/using/deprecated-features.md)。

>[!CAUTION]
>
>此矩陣會定期更新，新增支援的項目，並移除不建議使用的項目。

## Operating Systems{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x（64位）</p>
<p>7.x（64位）</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>10（64位）</p>
<p>9（64位）</p>
<p>8（64位）</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x（64位）</p>
<p>7.x（64位）</p>
<p><strong>重要：</strong> 如果您使用RHEL，您必須願意停用SELinux，或讓架構設計人員編寫自訂SELinux規則，以檢查啟用的SELinux是否不會造成促銷活動作業的問題。</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012年R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

## Web Servers{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>Windows Server 2016上的10.0</p>
<p>Windows Server 2012 R2上的8.5</p>
<p>Windows Server 2012上的8.0 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 for RHEL7 - CentOS 7、Debian 8/9、Windows（64位）</p>
</td>
</tr>
</tbody>
</table>

## 工具{#Tools}

<table>
<tbody>
<tr>
<td>Java開發套件(JDK)</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p>此應用程式已獲得Oracle和OpenJDK開發的Java開發套件(JDK)的核准。</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6（及舊版，如果內嵌在您的系統中）</p>
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

## RDBMS伺服器{#RDBMSservers}

>[!NOTE]
>
>RDBMS驅動程式必須與RDBMS伺服器版本匹配。

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
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>注意：您也可以將Amazon RDS for PostgreSQL與上述指定的版本一起使用。</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1和SP2</p>
<p>警告：當Campaign伺服器在Linux上執行時，不支援Microsoft SQL Server做為主資料庫。 <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">進一步瞭解</a>。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL是托管環境的預設資料庫伺服器。

## CRM 連接器{#CRMconnectors}

<table>
<tbody>
<tr>
<td>Salesforce連接器API</td>
<td>
<p>API第37版</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API第21版</p>
<p>API 15版</p>
</td>
</tr>
<tr><td>Oracle On Demand API</td>
<td>
<p>網站服務1.0版API</p>
</td>
</tr>
<tr>
<td>MS Dynamics</td>
<td>
<p>網頁API:Dynamics 365內部部署與線上</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

<table>
<tbody>
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
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
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
<p>2012 SP1和SP2</p>
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
<td>內泰扎</td>
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
<p>第1版SP12或更高版本</p>
</td>
</tr>
<tr><td>通過HiveSQL的Hadoop</td>
<td>
<p>HortonWorks HDP 2.4.X、2.5.x、2.6.x</p>
<p>HDInsight 3.4(HDP 2.4)、3.5(HDP 2.5)、3.6(HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>雪花</td>
<td> </td>
</tr>
</tbody>
</table>

## 客戶端控制台作業系統{#ClientConsoleoperatingsystems}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>8</p>
<p>10（建議使用日文例項）</p>
</td>
</tr>
</tbody>
</table>

## 行動SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x、8.x、9.0</p>
<p>和行動SDK 1.0.27版。</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>與行動SDK建置版本1.0.26相容，與32和64位元版本相容。</p>
</td>
</tr>
</tbody>
</table>

## 瀏覽器{#Browsers}

對於下列瀏覽器，支援最新版本：Microsoft Edge、Mozilla Firefox、Google Chrome、Safari。

支援Internet Explorer 11。

## 更像這樣{#Morelikethis}

* [Campaign Classic發行說明](../../rn/using/latest-release.md)
* [安裝指南](../../installation/using/general-architecture.md)
* [不建議使用的功能和系統](../../rn/using/deprecated-features.md)
* [建立升級程式](../../production/using/build-upgrade.md)
