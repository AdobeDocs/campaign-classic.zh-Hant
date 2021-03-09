---
solution: Campaign Classic
product: campaign
title: Web-server配置
description: 進一步瞭解Web-Server組態的主要最佳實務。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Web伺服器配置{#web-server-configuration}

您將在以下找到與Web-Server(Apache/IIS)配置相關的一些主要最佳實踐。

* 變更預設錯誤頁面。

* 停用舊版SSL和密碼：

   **在Apache上**，編輯/etc/apache2/mods-available/ssl.conf。以下是範例：

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **在IIS** (請參 [閱說明檔案](https://support.microsoft.com/en-us/kb/245030))上，執行下列設定：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中添加註冊表子項
   * 要使系統使用預設情況下不會協商的協定（如TLS 1.2），請在&#x200B;**Protocols**&#x200B;鍵下的以下註冊表鍵中，將DisabledByDefault值的DWORD值資料更改為0x0:

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **停用SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client:DisabledByDefault:DWORD（32位元）值至1

   SCHANNEL\Protocols\SSL 3.0\Server:啟用：DWORD（32位元）值至0

* 刪除&#x200B;**TRACE**&#x200B;方法：

   **在Apache上**，在/etc/apache2/conf.d/security中編輯：TraceEnable  **Off**

   **在IIS** (請參 [閱說明檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))上，執行下列設定：

   * 請確定已安裝&#x200B;**請求篩選**&#x200B;角色服務或功能。
   * 在&#x200B;**請求篩選**&#x200B;窗格中，按一下HTTP動詞標籤，然後按一下拒絕動詞。 在「操作」窗格中，在開啟的對話框中輸入TRACE。

* 移除橫幅：

   **在Apache上**，編輯/etc/apache2/conf.d/安全性：

   * ServerSignature **Off**
   * ServerToken **Prod**

   **在IIS** (請參 [閱說明檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))上，執行下列設定：

   * 安裝&#x200B;**URLScan**。
   * 編輯&#x200B;**Urlscan.ini**&#x200B;檔案，使其具有&#x200B;**RemoveServerHeader=1**


* 限制查詢大小以防止上傳重要檔案：

   **在Apache** (請參 [閱說明檔案](http://httpd.apache.org/docs/2.2/mod/core.html#limitrequestbody))上，在／目錄中新增 **** LimitRequestBody指令（以位元組為單位）。

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **在IIS** (請參 [閱說明檔案](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits))上，在內容篩選選項中設定 **maxAllowedContentLength** （最大允許的內容長度）。

相關主題：

* [Adobe Marketing Cloud法規遵循概觀](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Adobe Campaign安全性概觀](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf) (PDF)
