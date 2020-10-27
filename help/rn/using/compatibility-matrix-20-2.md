---
title: 相容性矩陣
description: 相容性矩陣
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 3402212bc6904dd5587d3b5a16fca7f4857fb908
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 16%

---


# 相容性矩陣{#compatibility-matrix}

本檔案列出最新版 **Adobe Campaign Classic（v6.11和v7）支援的所有系統和元件**。 不屬於此清單的產品和版本與Adobe Campaign不相容。

## 重要附註{#important-notes}

此矩陣會定期更新，新增支援的項目，並移除不建議使用的項目。

除非另有提及，否則支援所有次要版本。

Adobe Campaign Classic與本頁所列的所有系統和工具相容。 由於這些協力廠商系統和工具的特定版本已與其各自的建立者達成生命週期結束(EOL),Adobe Campaign將不再與這些版本相容，而且會在後續的產品版本中，從我們的相容性矩陣中移除這些版本。 請確保您使用相容性矩陣列出的任何系統的支援版本，以避免出現任何問題。

若要進一步瞭解已過時的項目，請造 [訪本頁](../../rn/using/deprecated-features.md)。

## Operating Systems{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x（64位）</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>8（64位）</p>
<p>9（64位）</p>
<p>10（64位）</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x（64位）</p>
<p><strong>重要：</strong> 如果您使用RHEL，您必須願意停用SELinux，或讓架構設計人員編寫自訂SELinux規則，以檢查啟用的SELinux是否不會造成促銷活動作業的問題。</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2012</p>
<p>2012年R2</p>
<p>2016</p>
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
<p>Windows Server 2012上的8.0 - Windows 8</p>
<p>Windows Server 2012 R2上的8.5</p>
<p>Windows Server 2016上的10.0</p>
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
<p>8</p>
<p>9</p>
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

## RDBMS驅動程式{#RDBMSdrivers}

支援以下RDBMS驅動程式：

* Oracle SQL*Net 11

* Oracle SQL*Net 12

* PostgreSQL(libpq)

* SQLServer

* DB2（ODBC驅動程式）


>[!NOTE]
>
>RDBMS驅動程式必須與RDBMS伺服器版本匹配。

## RDBMS伺服器{#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>11g R2</p>
<p>12c</p>
<p>18c</p>
<p>19c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
<p>注意：您也可以將Amazon RDS for PostgreSQL與上述指定的版本一起使用。</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2012 - SP1和SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
<p>警告：當Campaign伺服器在Linux上執行時，不支援Microsoft SQL Server做為主資料庫。 <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">進一步瞭解</a>。</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL是托管環境的預設資料庫伺服器。

## CRM connectors{#CRMconnectors}

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
<p>API 15版</p>
<p>API第21版</p>
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
<p>Soap API —— 內部部署：2007、2015、2016年</p>
<p>Soap API —— 線上：2015年、2016年</p>
<p>Web API —— 內部部署與線上：365、2016、2016更新1</p>
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
<p>11g</p>
<p>12c</p>
<p>18c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2012 SP1和SP2</p>
<p>2014</p>
<p>2016</p>
<p>2017</p>
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
<p>15.0</p>
<p>15.10</p>
<p>16</p>
<p>16.20</p>
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
<p>2012</p>
<p>2016</p>
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
<p>7.x</p>
<p>8.x</p>
<p>9.0</p>
<p>和行動SDK 1.0.27版。</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9</p>
<p>iOS 10</p>
<p>iOS 11</p>
<p>iOS 12</p>
<p>iOS 13</p>
<p>與行動SDK建置版本1.0.26相容，與32和64位元版本相容。</p>
</td>
</tr>
</tbody>
</table>

## 瀏覽器{#Browsers}

支援Internet Explorer第11版。

對於下列瀏覽器，支援最新版本：

* Microsoft Edge

* Firefox

* Chrome

* Safari

## Experience Cloud 整合{#ExperienceCloudintegrations}

如需與Adobe解決方案的整合，請參閱本 [節](https://docs.adobe.com/content/help/en/campaign-classic/using/integrating-with-adobe-experience-cloud/about-campaign-integrations.html#experience-cloud-integrations)。

## 更像這樣{#Morelikethis}

* [Campaign Classic發行說明](https://docs.adobe.com/content/help/zh-Hant/campaign-classic/using/release-notes/latest-release.html)
* [安裝指南](https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/general-architecture.html)
* [不建議使用的功能和系統](https://helpx.adobe.com/tw/campaign/kb/deprecated-and-removed-features.html)
* [建立升級程式](https://helpx.adobe.com/tw/campaign/kb/acc-build-upgrade.html)
* [19.0版的Campaign Classic相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix-19-0.html)
* [19.1版的Campaign Classic相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix-19-1.html)

