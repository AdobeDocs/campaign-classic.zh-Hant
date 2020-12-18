---
solution: Campaign Classic
product: campaign
title: 無法連線
description: 無法連線
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 85fae38f864b031f069058dae79ce6753dc4bf03
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---


# 無法連線{#failure-to-connect}

連接問題的原因可以是多個，並且取決於各種上下文。

您可以試用下列測試，如果連線失敗持續，請連絡&#x200B;**Adobe Campaign支援**。



<table> 
<thead> 
<tr> 
<th>Checks<br /> </th> 
<th>解析度<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>您是否可從電腦存取網際網路？</td> 
<td>檢查您是否可以連線至網際網路上的網站（例如）。 如果您無法連線，問題就在您的電腦上。 請連絡您的系統管理員。</td>
</tr>
<tr> 
<td>您是否可透過其他服務連線至代管Adobe Campaign的伺服器？</td> 
<td>通過SSH或任何其他方式連接到伺服器。 如果不可能，則您的主機公司有問題。 聯繫其系統管理員。</td>
</tr>
<tr> 
<td>Web伺服器是否響應？</td> 
<td>使用網頁瀏覽器連線至Adobe Campaign伺服器存取URL:<b>http(s):// &lt;urlserver&gt;</b>。 如果未響應，則Web伺服器將停止在電腦上。 請洽詢您主機公司的系統管理員以重新啟動服務。</td>
</tr>
<tr> 
<td>Adobe Campaign是否已正確整合？</td> 
<td>登入：<b>http(s):///&lt;urlserver&gt;/r/test</b> URL。 伺服器應傳回下列類型的訊息：&lt;redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt;
如果未獲得此結果，請檢查Web伺服器配置中已考慮到整合。</td>
</tr>
<tr> 
<td>連線至下列URL:<b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>如果獲得Tomcat Java錯誤，請檢查JAVA整合是否正確執行。 它已整合在檔案[應用程式路徑]/nl6/customer.sh中</td>
</tr>
<tr> 
<td>連線至下列URL:<b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>如果您取得空白頁面，請檢查Adobe Campaign Web模組是否已啟動。 命令nlserver pdump應傳回Adobe Campaign Classic(7.X YY.R組建版本XXX@SHA1)的Application Server,DD/MM/YYYY。 否則，使用命令nlserver啟動Web重新啟動模組</td>
</tr>
<tr>
<td>檢查安全區的常規配置。</td>
<td>有關配置安全區的詳細資訊，請參閱<a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>本節。</a></td>
</tr>
<tr>
<td>命令nlserver pdump返回<b> No tasks</b></td>
<td>您必須重新啟動整個Adobe Campaign應用程式。 若要這麼做，請使用下列命令：<b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
