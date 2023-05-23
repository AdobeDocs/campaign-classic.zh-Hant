---
product: campaign
title: 無法連線
description: 無法連線
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3c793dc1-9654-4289-a3d2-30c3078fd848
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 4%

---

# 無法連線{#failure-to-connect}



連接問題的原因可能是多個，並且取決於各種上下文。

您可以嘗試以下test，如果連接故障仍然存在，請與 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。



<table> 
<thead> 
<tr> 
<th>檢查<br /> </th> 
<th>解決方法<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>您的電腦是否可訪問Internet?</td> 
<td>檢查是否可以連接到Internet上的網站（例如）。 如果無法連接，則問題出在您的電腦上。 請與系統管理員聯繫。</td>
</tr>
<tr> 
<td>您能否通過其他服務連接到承載Adobe Campaign的伺服器？</td> 
<td>通過SSH或任何其他方式連接到伺服器。 如果不可能，則您的主機公司有問題。 請與系統管理員聯繫。</td>
</tr>
<tr> 
<td>Web伺服器是否響應？</td> 
<td>使用Web瀏覽器連接到Adobe Campaign伺服器訪問URL: <b>http(s):// &lt;urlserver&gt;</b>。 如果它未響應，則Web伺服器在電腦上停止。 請與主機公司的系統管理員聯繫以重新啟動服務。</td>
</tr>
<tr> 
<td>Adobe Campaign是否正確整合了？</td> 
<td>登錄到： <b>http(s)://&lt;urlserver&gt;/r/test</b> URL。 伺服器應返回以下類型的消息： &lt;redir status="OK" date="YYYY/MM/DD HH&lt;span id="0" translate="no"/&gt;SS" build="XXXX" host="&lt;hostname&gt;" localhost="&lt;server&gt;" /&gt;
如果未獲得此結果，請簽入Web伺服器配置，以便將整合考慮在內。:MM:</td>
</tr>
<tr> 
<td>連接到以下URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>如果獲取Tomcat Java錯誤，請檢查JAVA整合是否正確執行。 它整合在檔案[應用程式路徑]/nl6/customer.sh中</td>
</tr>
<tr> 
<td>連接到以下URL: <b>http(s)://&lt;urlserver&gt;/nl/jsp/logon.jsp</b></td>
<td>如果獲取空白頁面，請檢查Adobe CampaignWeb模組是否已啟動。 命令nlserver pdump應返回DD/MM/YYYY的Adobe Campaign Classic(7.X YY.R build XXX@SHA1)的應用程式伺服器。 否則，使用命令nlserver start web（nlserver啟動Web）重新啟動模組</td>
</tr>
<tr>
<td>檢查安全區域的常規配置。</td>
<td>有關配置安全區域的詳細資訊，請參閱 <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html#configuring-campaign-server"/>此部分。</a></td>
</tr>
<tr>
<td>命令nlserver pdump返回 <b>無任務</b></td>
<td>必須重新啟動整個Adobe Campaign應用程式。 為此，請使用以下命令： <b>nlserver監視程式 — svc -noconsole</b></td>
</tr>
</tbody> 
</table>
