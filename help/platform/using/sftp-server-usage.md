---
product: campaign
title: SFTP 伺服器使用情況
description: 進一步了解SFTP伺服器最佳實務和疑難排解。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: 69f7b494c244fdf01a65ebe8d55c141d947a0980
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 41%

---

# SFTP 伺服器最佳實務及疑難排解 {#sftp-server-usage}

## SFTP伺服器全域建議 {#global-recommendations}

管理用於 ETL 的檔案和資料時，這些檔案儲存在 Adobe 提供的代管 SFTP 伺服器上。使用SFTP伺服器時，請務必遵循下列建議。

* 使用基於密鑰的身份驗證而不是密碼身份驗證，以避免密碼過期 (密碼的有效期為 90 天)。此外，基於金鑰的身份驗證允許您生成多個金鑰，例如在管理多個實體時。相反，密碼身份驗證要求您與所管理的所有實體共享密碼。

   支持的金鑰格式為 SSH-2 RSA 2048。金鑰可以使用PyTTY(Windows)或ssh-keygen(Unix)等工具生成。您必須通過[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)向Adobe支援團隊提供公開金鑰，以便將其上載到促銷活動伺服器。

* 在 SFTP 上載和工作流程中使用批次處理。

* 處理錯誤/例外狀況。

* 按照預設，您建立的所有資料夾僅為標識符的讀/寫模式。建立需要由 Campaign 存取的資料夾時，請確保使用整個組的讀/寫權限進行配置。否則，出於安全原因，工作流程可能無法建立/刪除檔案，因為它們在同一組內的不同標識符下運行。

* 您嘗試起始SFTP連線的公用IP必須新增至Campaign執行個體的允許清單。 您可以透過[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)請求將IP位址新增至允許清單。

## 資料庫使用最佳實務 {#sftp-server-best-practices}

SFTP伺服器設計為臨時儲存空間，您可在其上控制檔案的保留和刪除。

如果未正確使用或監視，這些空間可以快速填充伺服器上可用的物理空間，並導致檔案在後續上載時被截斷。 一旦空間飽和，自動清除可以觸發並從 SFTP 儲存器中刪除最舊的檔案。

為避免這類問題，Adobe建議遵循以下最佳做法。

>[!NOTE]
>
>如果您的執行個體託管在 AWS 上，則可以使用 Campaign Classic [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html)監控 SFTP 伺服器儲存。若要檢查您的執行個體是否託管在 AWS 上，請按照[本頁面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)詳述的步驟操作。
>
>所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本頁](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel)中。
>
>請注意，您的執行個體必須升級為最新的[Gold Standard](../../rn/using/gs-overview.md)組建或[最新的GA組建(21.1.3)](../../rn/using/latest-release.md)。 在[本章節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。 

* 伺服器大小功能因許可證而異。在任何情況下，儘量保持最小資料，並且只在需要的時間內保留資料 (15 天是最長時間限制)。

* 使用工作流程正確刪除資料（管理使用資料的工作流程的保留）。

* 時常登入 SFTP 以直接檢查其內容。

* 請記住，SFTP 硬碟的管理主要是您的責任。

## 外部SFTP伺服器使用情況 {#external-SFTP-server}

如果您使用自己的SFTP伺服器，請務必盡可能遵循上述建議。

此外，當在Campaign Classic中指定外部SFTP伺服器的路徑時，路徑語法會因SFTP伺服器作業系統而異：

* 如果您的SFTP伺服器位於&#x200B;**Windows**，請一律使用相對路徑。
* 如果STP伺服器位於&#x200B;**Linux**，請始終使用相對於家庭的路徑（以&quot;~/&quot;開頭），或絕對路徑（以&quot;/&quot;開頭）。

## Adobe托管SFTP伺服器的連線問題 {#sftp-server-troubleshooting}

下節列出當與Adobe托管的SFTP伺服器發生連線問題時，要透過[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)檢查並提供給Adobe支援團隊的資訊。

1. 檢查您的執行個體是否正在運行。若要這麼做，請開啟瀏覽器，然後在例項&#x200B;**[!UICONTROL /r/test]**&#x200B;端點上進行&#x200B;**[!UICONTROL GET]**&#x200B;呼叫：

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

   如果埠未打開，請確保打開側面的傳出連線，然後重試。如果您仍遇到連線問題，請與[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)團隊共用命令的輸出。

1. 檢查您嘗試起始SFTP連線的公用IP是否為您提供給Adobe支援以取得允許清單的IP。
1. 如果您使用基於密碼的身份驗證，則您的密碼可能已過期（密碼的有效期為90天）。 因此，我們強烈建議使用金鑰式驗證（請參閱[SFTP伺服器最佳實務](#sftp-server-best-practices)）。
1. 如果您使用基於密鑰的驗證，請檢查您使用的密鑰是否與提供給[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)團隊以用於實例配置的密鑰相同。
1. 如果您使用的是 FileZilla 或類似的 FTP 工具，請在支援票證中提供連線日誌詳細資訊。

## 「無法解析主機名」錯誤

本節提供從Campaign Classic連線至FTP伺服器後收到「無法解析主機名稱」錯誤時要執行之檢查和動作的相關資訊。

工作流日誌顯示以下日誌：

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

嘗試從工作流連接FTP伺服器並從伺服器下載檔案時，如果您仍能使用FileZilla或WinSCP透過FTP連接，則會發生此錯誤。

此錯誤表示無法正確解析FTP伺服器網域名稱。 若要進行疑難排解，請執行下列動作：

1. 疑難排解&#x200B;**DNS伺服器配置**:

   1. 檢查伺服器名稱是否已添加到本地DNS伺服器中。
   1. 如果是，請在Adobe Campaign伺服器上執行下列命令以取得IP位址：

      `nslookup <server domain name>`

      這可確認FTP伺服器運作正常，並可從Adobe Campaign應用程式伺服器存取。

1. 疑難排解&#x200B;**工作階段記錄**:

   1. 在工作流程中，連按兩下[檔案傳輸](../../workflow/using/file-transfer.md)活動。
   1. 前往&#x200B;**[!UICONTROL File Transfer]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Advanced Parameters]**。
   1. 核取 **[!UICONTROL Display the session logs]** 選項。

      ![](assets/sftp-error-display-logs.png)

   1. 轉到工作流審核並檢查日誌是否顯示「無法解析主機名」錯誤。

1. 如果SFTP伺服器是由Adobe托管，請聯絡客戶服務，檢查IP是否已新增至允許清單。

   否則驗證：

   * 密碼不包含「@」。 如果密碼中有「@」，則連接失敗。
   * 沒有防火牆問題會阻礙Adobe Campaign應用程式伺服器與SFTP伺服器之間的通訊。
   * 從campaign伺服器執行tracert和telnet命令至sftp，查看是否有連線問題。
   * 沒有通信協定問題。
   * 埠已開啟。
