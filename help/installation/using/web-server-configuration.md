---
product: campaign
title: Web伺服器設定
description: 深入瞭解網頁伺服器設定主要最佳實務
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: dba90a154e08400ae6ab6478623a50d48d72207c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Web伺服器設定 {#web-server-configuration}



您將會找到與網頁伺服器(Apache/IIS)設定相關的一些主要最佳實務。

* 變更預設錯誤頁面。

* 停用舊的SSL版本和加密：

  **在Apache上**，編輯/etc/apache2/mods-available/ssl.conf。 範例如下：

   * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
   * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

  **在IIS上** (請參閱 [檔案](https://support.microsoft.com/en-us/kb/245030))，執行以下設定：

   * 在HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL中新增登入子機碼
   * 若要讓系統使用預設不會交涉的通訊協定（例如TLS 1.2），請將DisabledByDefault值的DWORD值資料變更為0x0，其位於下列的登入機碼下 **通訊協定** 索引鍵：

     SCHANNEL\Protocols\TLS 1.2\Client

     SCHANNEL\Protocols\TLS 1.2\Server

  **停用SSL x.0**

  SCHANNEL\Protocols\SSL 3.0\Client： DisabledByDefault： DWORD （32位元）值為1

  SCHANNEL\Protocols\SSL 3.0\Server：啟用： DWORD （32位元）值為0

* 移除 **TRACE** 方法：

  **在Apache上**，在/etc/apache2/conf.d/security中編輯： TraceEnable **關閉**

  **在IIS上** (請參閱 [檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs))，執行以下設定：

   * 請確定 **要求篩選** 角色服務或功能已安裝。
   * 在 **要求篩選** 窗格，按一下HTTP動詞索引標籤，然後按一下拒絕動詞。 在「動作」窗格中，在開啟的對話方塊中輸入TRACE。

* 移除橫幅：

  **在Apache上**，編輯/etc/apache2/conf.d/security：

   * ServerSignal **關閉**
   * ServerTokens **Prod**

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

  **在IIS上** (請參閱 [檔案](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits))，設定 **Maxallowedcontentlength** （內容篩選選項中的「最大允許內容長度」）。

相關主題：

* [Adobe Marketing Cloud合規性概觀](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#privacy)
* [Adobe Campaign安全性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#security)
