---
product: campaign
title: Web伺服器配置
description: 進一步了解Web伺服器配置的主要最佳做法。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Web伺服器配置 {#web-server-configuration}

![](../../assets/v7-only.svg)

您將在下方找到一些與Web伺服器(Apache/IIS)配置相關的主要最佳做法。

* 更改預設錯誤頁。

* 停用舊版SSL和密碼：

   **在Apache**&#x200B;上編輯/etc/apache2/mods-available/ssl.conf。以下是範例：

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **在IIS** (請參閱 [本檔案](https://support.microsoft.com/en-us/kb/245030))上，執行下列設定：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中添加註冊表子項
   * 要使系統能夠使用預設不會協商的協定（如TLS 1.2），請在&#x200B;**Protocols**&#x200B;鍵下的以下註冊表項中，將DisabledByDefault值的DWORD值資料更改為0x0:

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **禁用SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client網站：DisabledByDefault:DWORD（32位）值為1

   SCHANNEL\Protocols\SSL 3.0\Server網站：已啟用：DWORD（32位）值為0

* 移除&#x200B;**TRACE**&#x200B;方法：

   **在Apache**&#x200B;上，在/etc/apache2/conf.d/security中編輯：TraceEnable  **Off**

   **在IIS** (請參閱 [本檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))上，執行下列設定：

   * 請確定已安裝&#x200B;**請求篩選**&#x200B;角色服務或功能。
   * 在&#x200B;**請求篩選**&#x200B;窗格中，按一下HTTP動詞頁簽，然後按一下拒絕動詞。 在「操作」窗格中，在開啟的對話框中輸入TRACE。

* 移除橫幅：

   **在Apache上**，編輯/etc/apache2/conf.d/安全性：

   * ServerSignature **Off**
   * ServerTokens **Prod**

   **在IIS**&#x200B;上，執行下列配置：

   * 安裝&#x200B;**URLScan**。
   * 編輯&#x200B;**Urlscan.ini**&#x200B;檔案，使其具有&#x200B;**RemoveServerHeader=1**


* 限制查詢大小以防止上傳重要檔案：

   **在Apache**&#x200B;上，在/目 **** 錄中新增LimitRequestBodydirective（以位元組為單位）。

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **在IIS** (請參閱 [檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits))上，在內容篩選選項 **中設定maxAllowedContentLength** （最大允許的內容長度）。

相關主題：

* [Adobe Marketing Cloud法規遵循概述](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Adobe Campaign安全性概觀](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf) (PDF)
