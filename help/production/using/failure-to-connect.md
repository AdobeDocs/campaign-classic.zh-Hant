---
product: campaign
title: 無法連線
description: 無法連線
feature: Monitoring
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---

# 無法連線{#failure-to-connect}



連線問題的原因可能是多方面的，且取決於不同的內容。

您可以嘗試下列測試，如果連線失敗持續發生，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>檢查<br /> </th> 
<th>解析度<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>您可從電腦存取網際網路嗎？</td> 
<td>檢查您是否可以連線到網際網路上的網站（例如）。 如果無法連線，問題會發生在您的電腦上。 請連絡您的系統管理員。</td>
</tr>
<tr> 
<td>您可以透過其他服務連線至託管Adobe Campaign的伺服器嗎？</td> 
<td>透過SSH或任何其他方式連線至伺服器。 如果無法執行此操作，表示您的主機公司發生問題。 請聯絡他們的系統管理員。</td>
</tr>
<tr> 
<td>Web伺服器會回應嗎？</td> 
<td>使用網頁瀏覽器連線至Adobe Campaign伺服器存取URL： <b>http(s)：// &lt;urlserver&gt;</b>. 如果它沒有回應，則電腦上的網頁伺服器會停止。 請連絡您主機公司的系統管理員，以重新啟動服務。</td>
</tr>
<tr> 
<td>Adobe Campaign是否已正確整合？</td> 
<td>登入： <b>http(s)：//&lt;urlserver&gt;/r/test</b> URL。 伺服器應傳回下列型別的訊息： &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
如果您沒有取得此結果，請檢查Web伺服器設定，確認整合已納入考量。:MM:</td>
</tr>
<tr> 
<td>連線至下列URL： <b>http(s)：//&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>如果您收到Tomcat Java錯誤，請檢查JAVA整合是否正確執行。 已整合至檔案[path of application]/nl6/customer.sh</td>
</tr>
<tr> 
<td>連線至下列URL： <b>http(s)：//&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>如果您取得空白頁面，請檢查Adobe Campaign網頁模組是否已啟動。 命令nlserver pdump應傳回DD/MM/YYYY的Adobe Campaign Classic (7.X YY.R建置XXX@SHA1)應用程式伺服器。 如果沒有，請使用命令nlserver start web重新啟動模組</td>
</tr>
<tr>
<td>檢查安全性區域的一般設定。</td>
<td>有關設定安全性區域的詳細資訊，請參閱 <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html#configuring-campaign-server"/>本節。</a></td>
</tr>
<tr>
<td>命令nlserver pdump傳回 <b>無任務</b></td>
<td>您必須重新啟動整個Adobe Campaign應用程式。 要執行此操作，請使用下列命令： <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
