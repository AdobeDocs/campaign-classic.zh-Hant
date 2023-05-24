---
product: campaign
title: Web伺服器設定
description: 進一步瞭解網頁伺服器設定主要最佳實務
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

# Web伺服器設定 {#web-server-configuration}



以下是與Web伺服器(Apache/IIS)設定相關的一些主要最佳實務。

* 變更預設錯誤頁面。

* 停用舊的SSL版本和加密：

   **在Apache上**，編輯/etc/apache2/mods-available/ssl.conf。 範例如下：

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite高:MEDIUM:！aNULL：！MD5：！SSLv3：！SSLv2：！TLSv1

   **在IIS上** (請參閱 [檔案](https://support.microsoft.com/en-us/kb/245030))，執行以下設定：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中新增登入子機碼
   * 若要讓系統使用預設不會交涉的通訊協定（例如TLS 1.2），請將DisabledByDefault值的DWORD值資料變更為0x0，在下列登入機碼下 **通訊協定** 索引鍵：

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **停用SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client： DisabledByDefault： DWORD （32位元）值為1

   SCHANNEL\Protocols\SSL 3.0\Server：啟用： DWORD （32位元）值設為0

* 移除 **TRACE** 方法：

   **在Apache上**，在/etc/apache2/conf.d/security中編輯： TraceEnable **關閉**

   **在IIS上** (請參閱 [檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))，執行以下設定：

   * 請確定 **請求篩選** 角色服務或功能已安裝。
   * 在 **請求篩選** 窗格，按一下HTTP動詞索引標籤，然後按一下拒絕動詞。 在「動作」窗格中，在開啟的對話方塊中輸入TRACE。

* 移除橫幅：

   **在Apache上**，編輯/etc/apache2/conf.d/security：

   * 伺服器簽章 **關閉**
   * ServerToken **Prod**

   **在IIS上**，執行以下設定：

   * 安裝 **URLcan**.
   * 編輯 **Urlscan.ini** 要擁有的檔案 **RemoveServerHeader=1**


* 限制查詢大小以防止重要檔案上傳：

   **在Apache上**，新增 **LimitRequestBody** /目錄中的指示詞（以位元組為單位的大小）。

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **在IIS上** (請參閱 [檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits))，設定 **maxAllowedContentLength** （內容篩選選項中允許的最大內容長度）。

相關主題：

* [Adobe Marketing Cloud合規性概觀](https://experienceleague.adobe.com/docs/core-services/assets/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Adobe Campaign安全性總覽](https://www.adobe.com/content/dam/cc/en/security/pdfs/ADB-CampaignSecurity-WP.pdf) (PDF)
