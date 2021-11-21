---
product: campaign
title: 無法連線
description: 無法連線
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 4%

---

# 無法連線{#failure-to-connect}

![](../../assets/v7-only.svg)

連線問題的原因可能是多個，且取決於不同的內容。

您可以嘗試下列測試，如果連線失敗持續，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).



<table> 
<thead> 
<tr> 
<th>檢查<br /> </th> 
<th>解決方案<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>您的電腦是否可訪問Internet?</td> 
<td>檢查您是否可以連線至網際網路上的網站（例如）。 如果無法連接，則問題出在您的電腦上。 請與系統管理員聯繫。</td>
</tr>
<tr> 
<td>您可以透過其他服務連線至托管Adobe Campaign的伺服器嗎？</td> 
<td>透過SSH或任何其他方式連線至伺服器。 如果無法這麼做，您的主機公司會發生問題。 請聯繫其系統管理員。</td>
</tr>
<tr> 
<td>Web伺服器是否響應？</td> 
<td>使用Web瀏覽器連線至Adobe Campaign伺服器存取URL: <b>http(s):// &lt;urlserver&gt;</b>. 如果未響應，則電腦上將停止Web伺服器。 請與主機公司的系統管理員聯繫以重新啟動服務。</td>
</tr>
<tr> 
<td>Adobe Campaign是否已正確整合？</td> 
<td>登入： <b>http(s)://&lt;urlserver&gt;/r/test</b> URL。 伺服器應傳回下列類型的訊息： &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
如果您未取得此結果，請檢查您的Web伺服器設定，確認已考慮整合。:MM:</td>
</tr>
<tr> 
<td>連線至下列URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>如果獲得Tomcat Java錯誤，請檢查JAVA整合是否正確執行。 已整合至檔案[應用程式路徑]/nl6/customer.sh</td>
</tr>
<tr> 
<td>連線至下列URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>如果您取得空白頁面，請檢查Adobe Campaign Web模組是否已啟動。 命令nlserver轉儲應返回Adobe Campaign Classic(7.X YY.R組建XXX@SHA1)的Application server，其DD/MM/YYYY。 否則，使用命令nlserver start web重新啟動模組</td>
</tr>
<tr>
<td>檢查安全區域的一般配置。</td>
<td>有關配置安全區域的詳細資訊，請參閱 <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>本節。</a></td>
</tr>
<tr>
<td>命令nlserver pdump返回 <b>無任務</b></td>
<td>您必須重新啟動整個Adobe Campaign應用程式。 要執行此操作，請使用以下命令： <b>nlserver watchgd -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
