---
solution: Campaign Classic
product: campaign
title: 無法連線
description: 無法連線
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: cb6a2247e3b7617511aecf3d2d19985af0216494
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 2%

---


# 無法連線{#failure-to-connect}

連接問題的原因可以是多個，並且取決於各種上下文。

您可以嘗試下列測試，如果連線失敗仍持續，請連絡 **Adobe Campaign支援**。



<table> 
 <thead> 
  <tr> 
   <th>檢查<br /> </th> 
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
   <td>使用網頁瀏覽器連線至Adobe Campaign伺服器存取URL:**`http(s):// <urlserver>`**. 如果未響應，則Web伺服器將停止在電腦上。 請洽詢您主機公司的系統管理員以重新啟動服務。</td>
  </tr>
  <tr> 
   <td>Adobe Campaign是否已正確整合？</td> 
   <td>登入：**`http(s)://<urlserver>/r/test`** URL。 伺服器應返回以下類型的消息

    &quot;
    &lt;redir status=&#39;OK&#39; date=&#39;YYYY/MM/DD HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &quot;
    
    如果您未取得此結果，請檢查已考慮整合的Web伺服器組態。&lt;/td>
</tr>
  <tr> 
   <td>Adobe Campaign Web模組是否已啟動？</td> 
   <td>
   連線至下列URL:**`http(s)://<URLSERVER>/nl/jsp/logon.jsp`** *如果您獲得Tomcat Java錯誤：

    JAVA整合是否正確執行？ Adobe Campaign需要SUN JDK。
    
    它已整合在檔案***`[應用程式路徑]`/nl6/customer.sh*
    
    **如果您取得空白頁面：
    
    Adobe Campaign Web模組是否已啟動？ 您應取得：
    
    &quot;
    nlserver
    pdumpHH:MM:SS > Adobe Campaign Classic(7.X YY.R組建版本XXX@SHA1)DD/MM/YYYY
    [...]
    web@default(27515)- 55.2 Mb
    [......]
    
    
    
    
    
    
    &quot;否，請使用以下命令重新啟動它：&quot;nlserver start web td&quot;&lt;/lserver
</tr>
  <tr>
  	<td>檢查安全區的常規配置。</td>
  	<td>有關配置安全區的詳細資訊，請參閱[本節](../../installation/using/configuring-campaign-server.md#defining-security-zones)</td>
  </tr>
 </tbody> 
</table>
