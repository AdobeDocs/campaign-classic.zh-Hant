---
solution: Campaign Classic
product: campaign
title: SFTP 伺服器使用情況
description: 進一步瞭解SFTP伺服器最佳範例和疑難排解。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '1158'
ht-degree: 33%

---


# SFTP 伺服器最佳實務及疑難排解 {#sftp-server-usage}

## SFTP伺服器全局建議{#global-recommendations}

管理用於 ETL 的檔案和資料時，這些檔案儲存在 Adobe 提供的代管 SFTP 伺服器上。使用SFTP伺服器時，請務必遵循下列建議。

* 使用基於密鑰的身份驗證而不是密碼身份驗證，以避免密碼過期 (密碼的有效期為 90 天)。此外，基於金鑰的身份驗證允許您生成多個金鑰，例如在管理多個實體時。相反，密碼身份驗證要求您與所管理的所有實體共享密碼。

   支持的金鑰格式為 SSH-2 RSA 2048。您可以使用PyTTY(Windows)或ssh-keygen(Unix)等工具產生金鑰。您必須透過[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)將公開金鑰提供給Adobe支援團隊，才能將它上傳到促銷活動伺服器。

* 在 SFTP 上載和工作流程中使用批次處理。

* 處理錯誤/例外狀況。

* 按照預設，您建立的所有資料夾僅為標識符的讀/寫模式。建立需要由 Campaign 存取的資料夾時，請確保使用整個組的讀/寫權限進行配置。否則，出於安全原因，工作流程可能無法建立/刪除檔案，因為它們在同一組內的不同標識符下運行。

* 您嘗試從中啟動SFTP連線的公用IP必須新增至促銷活動例項的allowlist。 可通過[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)請求將IP地址添加到允許清單。

## 資料庫使用最佳實踐{#sftp-server-best-practices}

SFTP伺服器設計為臨時儲存空間，您可以在其上控制檔案的保留和刪除。

當未正確使用或監視時，這些空格可快速填滿伺服器上可用的物理空間，並導致檔案在後續上傳時遭到截斷。 一旦空間飽和，自動清除可以觸發並從 SFTP 儲存器中刪除最舊的檔案。

為避免此類問題，Adobe建議遵循以下最佳做法。

>[!NOTE]
>
>如果您的執行個體託管在 AWS 上，則可以使用 Campaign Classic [控制面板](https://docs.adobe.com/content/help/en/control-panel/using/sftp-management/sftp-storage-management.html)監控 SFTP 伺服器儲存。要檢查您的實例是否托管在AWS上，請遵循本頁[中詳細介紹的步驟。](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)
>
>所有管理員使用者都可存取控制面板。 授予使用者管理員存取權的步驟詳見[本頁](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel)。
>
>請注意，您的實例必須升級為最新的[Gold Standard](../../rn/using/gs-overview.md)組建版本或[最新的GA組建版本(21.1)](../../rn/using/latest-release.md)。 瞭解如何在[本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的版本。

* 伺服器大小功能因許可證而異。在任何情況下，儘量保持最小資料，並且只在需要的時間內保留資料 (15 天是最長時間限制)。

* 使用工作流程正確刪除資料（管理使用資料的工作流程的保留）。

* 時常登入 SFTP 以直接檢查其內容。

* 請記住，SFTP 硬碟的管理主要是您的責任。

## 外部SFTP伺服器使用{#external-SFTP-server}

如果您使用自己的SFTP伺服器，請務必盡可能遵循上述建議。

此外，在Campaign Classic到外部SFTP伺服器的路徑時，路徑語法根據SFTP伺服器作業系統而不同：

* 如果您的SFTP伺服器位於&#x200B;**Windows**&#x200B;上，請始終使用相對路徑。
* 如果STP伺服器位於&#x200B;**Linux**&#x200B;上，請始終使用相對於主目錄的路徑（從&quot;~/&quot;開始）或絕對路徑（從&quot;/&quot;開始）。

## Adobe托管SFTP伺服器{#sftp-server-troubleshooting}的連接問題

下節列出當遇到Adobe托管SFTP伺服器的連接問題時，要通過[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)檢查並向Adobe支援團隊提供的資訊。

1. 檢查您的執行個體是否正在運行。若要這麼做，請開啟您的瀏覽器，然後對例項&#x200B;**[!UICONTROL /r/test]**&#x200B;端點進行&#x200B;**[!UICONTROL GET]**&#x200B;呼叫：

   ```
   https://instanceUrl/r/test
   ```

   如果執行個體正在運行，您應該得到這種類型的回應：

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   在任何情況下，請在支援票證中提供命令回應。

1. 檢查出站端口 22 是否在嘗試啟動 SFTP 連接的站點上打開。為此，請使用以下命令：

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   >[!NOTE]
   >
   >Netcat 工具可讓您輕鬆管理各種操作系統上的網路連線 (請參見 [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/))。

   如果埠未打開，請確保打開側面的傳出連線，然後重試。如果您仍然遇到連接問題，請與[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)團隊共用命令輸出。

1. 檢查您嘗試從中啟動SFTP連接的公共IP是否是您為allowlist向Adobe支援部門提供的IP。
1. 如果您使用密碼驗證，您的密碼可能已過期（密碼的有效期為90天）。 因此，我們強烈建議使用基於密鑰的驗證（請參閱[SFTP伺服器最佳實踐](#sftp-server-best-practices)）。
1. 如果您使用基於密鑰的驗證，請檢查您使用的密鑰是否與您為實例配置提供給[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)團隊的密鑰相同。
1. 如果您使用的是 FileZilla 或類似的 FTP 工具，請在支援票證中提供連線日誌詳細資訊。

## 「無法解析主機名」錯誤

本節提供從Campaign Classic連線至FTP伺服器後，取得「無法解析主機名稱」錯誤時要執行之檢查和動作的資訊。

工作流日誌顯示以下日誌：

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

當您嘗試從工作流程連線FTP伺服器並從伺服器下載檔案時，仍能使用FileZilla或WinSCP透過FTP連線時，會發生此錯誤。

此錯誤表示無法正確解析FTP伺服器網域名稱。 若要疑難排解，請執行下列動作：

1. 疑難排解&#x200B;**DNS伺服器配置**:

   1. 檢查伺服器名稱是否已添加到本地DNS伺服器中。
   1. 如果是，請在Adobe Campaign伺服器上運行以下命令以獲取IP地址：

      `nslookup <server domain name>`

      這可確認FTP伺服器是否運作，並可從Adobe Campaign應用程式伺服器存取。

1. 疑難排解&#x200B;**會話日誌**:

   1. 在工作流中，按兩下[檔案傳輸](../../workflow/using/file-transfer.md)活動。
   1. 前往&#x200B;**[!UICONTROL File Transfer]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Advanced Parameters]**。
   1. 核取 **[!UICONTROL Display the session logs]** 選項。

      ![](assets/sftp-error-display-logs.png)

   1. 轉至工作流審計並檢查日誌是否顯示「無法解析主機名」錯誤。

1. 如果SFTP伺服器是由Adobe代管，請聯絡客戶服務以檢查是否已將IP新增至允許清單。

   否則請驗證：

   * 密碼不包含「@」。 如果密碼中有「@」，則連接失敗。
   * 沒有防火牆問題會妨礙Adobe Campaign應用程式伺服器與SFTP伺服器之間的通訊。
   * 從促銷活動伺服器執行tracert和telnet命令至sftp，以查看是否有連線問題。
   * 沒有通信協定問題。
   * 埠已開啟。
