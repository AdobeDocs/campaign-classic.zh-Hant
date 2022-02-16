---
product: campaign
title: Web伺服器配置
description: 瞭解有關Web伺服器配置的主要最佳實踐的詳細資訊。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: 3709aaf0543a50ff6c2e65a75e7189ab805cd742
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Web伺服器配置 {#web-server-configuration}

![](../../assets/v7-only.svg)

您將在下面找到與Web伺服器(Apache/IIS)配置相關的一些主要最佳實踐。

* 更改預設錯誤頁。

* 禁用舊SSL版本和密碼：

   **在Apache上**&#x200B;編輯/etc/apache2/mods-available/ssl.conf。 下面是一個示例：

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite高級:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **在IIS上** (請參閱 [文檔](https://support.microsoft.com/en-us/kb/245030))，執行以下配置：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中添加註冊表子項
   * 要使系統使用預設情況下不會協商的協定（如TLS 1.2），請在以下註冊表項下的DisabledByDefault值的DWORD值資料更改為0x0 **協定** 鍵：

      SCHANNEL\Protocols\TLS 1.2\客戶端

      SCHANNEL\Protocols\TLS 1.2\Server
   **禁用SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client:DisabledByDefault:DWORD（32位）值為1

   SCHANNEL\Protocols\SSL 3.0\Server:已啟用：DWORD（32位）值到0

* 刪除 **TRACE** 方法：

   **在Apache上**，請在/etc/apache2/conf.d/security中編輯：跟蹤啟用 **關閉**

   **在IIS上** (請參閱 [文檔](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))，執行以下配置：

   * 確保 **請求篩選** 角色服務或功能已安裝。
   * 在 **請求篩選** 窗格，按一下HTTP謂詞頁籤，然後按一下拒絕謂詞。 在「操作」窗格中，在開啟的對話框中輸入TRACE。

* 刪除標題：

   **在Apache上**，編輯/etc/apache2/conf.d/security:

   * 伺服器簽名 **關閉**
   * 伺服器令牌 **生產**

   **在IIS上**，執行以下配置：

   * 安裝 **URLScan**。
   * 編輯 **烏爾斯坎.ini** 檔案 **RemoveServerHeader=1**


* 限制查詢大小以阻止上載重要檔案：

   **在Apache上**&#x200B;的子菜單。 **LimitRequestBody** /目錄中的指令（位元組大小）。

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **在IIS上** (請參閱 [文檔](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits))，設定 **maxAllowedContentLength** （允許的最大內容長度）。

相關主題：

* [Adobe Marketing Cloud法規遵從性概述](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Adobe Campaign安全概述](https://www.adobe.com/content/dam/cc/en/security/pdfs/ADB-CampaignSecurity-WP.pdf) (PDF)
