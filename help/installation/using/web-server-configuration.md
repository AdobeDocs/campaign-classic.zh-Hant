---
product: campaign
title: Web伺服器配置
description: 進一步了解Web伺服器配置的主要最佳做法
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Web伺服器配置 {#web-server-configuration}



您將在下方找到一些與Web伺服器(Apache/IIS)配置相關的主要最佳做法。

* 更改預設錯誤頁。

* 停用舊版SSL和密碼：

   **在Apache上**，編輯/etc/apache2/mods-available/ssl.conf 。 以下是範例：

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **在IIS上** (請參閱 [檔案](https://support.microsoft.com/en-us/kb/245030))，請執行下列設定：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中添加註冊表子項
   * 若要讓系統使用預設不會議定的通訊協定（例如TLS 1.2），請在下列登錄機碼下的 **通訊協定** 索引鍵：

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **禁用SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\客戶端：DisabledByDefault:DWORD（32位）值為1

   SCHANNEL\Protocols\SSL 3.0\Server:已啟用：DWORD（32位）值為0

* 移除 **TRACE** 方法：

   **在Apache上**，在/etc/apache2/conf.d/security中編輯：TraceEnable **關閉**

   **在IIS上** (請參閱 [檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))，請執行下列設定：

   * 確保 **請求篩選** 角色服務或功能已安裝。
   * 在 **請求篩選** 窗格，按一下「HTTP動詞」頁簽，然後按一下「拒絕動詞」。 在「操作」窗格中，在開啟的對話框中輸入TRACE。

* 移除橫幅：

   **在Apache上**，編輯/etc/apache2/conf.d/安全性：

   * 伺服器簽名 **關閉**
   * 伺服器代號 **生產**

   **在IIS上**，請執行下列設定：

   * 安裝 **URLcan**.
   * 編輯 **Urlscan.ini** 檔案 **RemoveServerHeader=1**


* 限制查詢大小以防止上傳重要檔案：

   **在Apache上**，新增 **LimitRequestBody** /目錄中的指令（位元組大小）。

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **在IIS上** (請參閱 [檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits))，設定 **maxAllowedContentLength** （允許的內容長度上限）。

相關主題：

* [Adobe Marketing Cloud法規遵循概述](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Adobe Campaign安全性概觀](https://www.adobe.com/content/dam/cc/en/security/pdfs/ADB-CampaignSecurity-WP.pdf) (PDF)
