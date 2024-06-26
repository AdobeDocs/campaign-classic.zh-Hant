---
product: campaign
title: Campaign Classic 相容性矩陣
description: Campaign Classic 相容性矩陣
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: b23632d0718d62d61e94e636937b93aa39bbe43f
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---

# 相容性比較表 {#compatibility-matrix}

在其[最新建置版本](../../rn/using/latest-release.md)中，Adobe Campaign Classic v7 與此頁面列出的所有系統和工具相容。這些協力廠商系統和工具的特定版本生命週期結束 (EOL) 時，Adobe Campaign 不再與那些版本相容：我們將不再使用這些系統和功能，後續的產品發行版本亦會將這些系統和功能從相容性矩陣移除。請務必使用相容性矩陣所列出的任一系統支援版本，以避免出現任何問題。若要進一步瞭解已棄用的項目，請瀏覽[本頁面](../../rn/using/deprecated-features.md)。

除非另有提及，否則支援所有次要版本。

>[!CAUTION]
>
>此矩陣會定期更新、新增新支援的系統與工具，並會移除已棄用的項目。

## 作業系統 {#OperatingSystems}

身為內部部署/混合部署客戶，您必須在下列其中一種作業系統中安裝 Adobe Campaign。 請於[本頁](../../installation/using/application-server.md)進一步了解 Campaign Classic v7 安裝步驟。

<table> 
<tbody> 
<td><strong>作業系統</strong></td>
<td><strong>作業系統版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4</p>
<p>v7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>如果您使用 RHEL，您必須願意停用 [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux)，或讓架構設計人員編寫自訂 SELinux 規則，以檢查啟用的 SELinux 是否不會造成 Campaign 作業的問題。

## 網頁伺服器 {#WebServers}

身為內部部署 / 混合部署客戶，根據您的作業系統，您必須將 Campaign 整合至下列其中一個 Web 伺服器。 若要進一步瞭解 Web 伺服器設定步驟，請參閱[此頁面](../../installation/using/integration-into-a-web-server-for-windows.md) (適用於 Windows) 和[此頁面](../../installation/using/integration-into-a-web-server-for-linux.md) (適用於 Linux)。

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 於 Windows Server 上</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4</p>
</td>
</tr>
</tbody>
</table>

## 工具 {#Tools}

身為內部部署 / 混合部署客戶，您必須安裝並設定下列工具。 [了解更多](../../installation/using/application-server.md)。

<table>
<tbody>
<td><strong>工具</strong></td>
<td><strong>版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr>
<td><p>Java 開發套件 (JDK)</p>
<p>在<a href="../../installation/using/application-server.md#jdk" target="_blank">本頁</a>中瞭解更多。</p>
</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>自 v7.4.1 起需要</p>
<p>至 v7.4.1 止</p>
<p>至 v7.4.1 止</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7 (及舊版，若是內嵌在您的系統中)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## 關係資料庫管理系統 (RDBMS) {#RDBMSservers}

身為內部部署 / 混合部署客戶，您必須安裝並設定下列其中一個資料庫。 [了解更多](../../installation/using/creating-and-configuring-the-database.md)。


<table>
<tbody>
<td><strong>資料庫系統</strong></td>
<td><strong>資料庫版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>v7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Microsoft SQL Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS 驅動程式必須與 RDBMS 伺服器版本相符。
>
>* 當 Campaign 伺服器在 Linux 上執行時，不支援 Microsoft SQL Server 作為主要資料庫。[了解更多](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers)。
>
>* 您也可以將 Amazon RDS for PostgreSQL 與上述指定版本搭配使用。
>
>* PostgreSQL 是用於託管雲端服務環境的 RDBMS。


## CRM 連接器 {#CRMconnectors}

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

與 Adobe Campaign [同盟資料存取模組](../../installation/using/about-fda.md)相容的外部資料庫如下所列。相容性取決於您的[託管模式](../../installation/using/hosting-models.md)。

**受託服務** (託管)、**混合**&#x200B;及&#x200B;**內部部署**&#x200B;環境可使 Campaign 連線下列外部資料庫系統：

<table>
<tbody>
<td><strong>資料庫系統</strong></td>
<td><strong>資料庫版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 </td>
</tr>
</tbody>
</table>

此外，**混合**&#x200B;及&#x200B;**內部部署**&#x200B;環境可使 Campaign 連線下列外部資料庫系統。這些系統跟 Campaign **Managed Services** (託管) 環境&#x200B;**不相容**。

<table>
<tbody>
<td><strong>資料庫系統</strong></td>
<td><strong>資料庫版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>v7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>第 1 版 SPS 12</p>
</td>
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022 (自 Campaign v7.4 起)</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 及 SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (最新版本)</p>
</td>
<td></td>
</tr>
<tr><td>透過 HiveSQL 提供的 Hadoop</td>
<td>
<p>HortonWorks HDP 2.4.X、2.5.x、2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4)、3.5 (HDP 2.5)、3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## 用戶端主控台 {#ClientOS}

使用 [Campaign 用戶端主控台](../../installation/using/installing-the-client-console.md)時，需要&#x200B;**使用**&#x200B;下列作業系統和瀏覽器。

### 作業系統

<table>
<tbody>
<td><strong>系統</strong></td>
<td><strong>作業系統版本</strong></td>
<td><strong>最低 Campaign 版本</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.2.1</p>
<p></p>
</tbody>
</table>

### Microsoft WebView 2 執行階段 {#webview}

Campaign 用戶端主控台必須使用 Microsoft Edge WebView2 執行階段最新版本。

從 [Microsoft 開發人員網站](https://www.adobe.com/go/acc-ms-webview2-runtime-download)下載 Microsoft Edge WebView2。


## Mobile SDK {#MobileSDK}

您可以在資料收集 UI 設定 Adobe Experience Platform 擴充功能，透過 Adobe Campaign Mobile SDK 使用 Campaign 來[傳送推播通知](../../delivery/using/about-mobile-app-channel.md)。

自 Campaign v7.4 起，[已棄用](deprecated-features.md) Campaign SDK。為確保現有實施能順利轉變為 AEP Mobile SDK，您仍可在下列作業系統上使用該 SDK<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->。


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7 - 14</p>
<p>搭配行動 SDK 建置版本 1.1.1。</p>
<p>自 Campaign v7.4 起，支援 Android 13 與 14。</p>
<p>自 Campaing v7.3 起，支援 Android 12。</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 17</p>
<p>搭配行動 SDK 建置版本 1.0.26。</p>
<p>自 Campaing v7.3 起，支援 Apple iOS 15。 </p>
<p>自 Campaign v7.4 起，支援 Apple iOS 16 與 17。</p>
</td>
</tr>
</tbody>
</table>

## 瀏覽器 {#Browsers}

下列瀏覽器的最新版本與 Campaign for [Web Access](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-) 相容。

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Campaign Classic 發行說明](../../rn/using/latest-release.md)
>* [Campaign 一般架構](../../installation/using/general-architecture.md)
>* [硬體尺寸建議](../../technotes/using/hardware-sizing.md)
>* [已棄用的功能及系統](../../rn/using/deprecated-features.md)
>* [建立升級程序](../../production/using/build-upgrade.md)
