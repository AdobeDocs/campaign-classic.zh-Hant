---
title: SFTP伺服器最佳範例與疑難排解
description: 進一步瞭解SFTP伺服器最佳範例和疑難排解。
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc7ba0c26bd57a75c3dbeaec541844a3b1196ef3
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 58%

---


# SFTP伺服器最佳範例與疑難排解 {#sftp-server-usage}

## SFTP 伺服器最佳實作 {#sftp-server-best-practices}

管理用於 ETL 的檔案和資料時，這些檔案儲存在 Adobe 提供的代管 SFTP 伺服器上。此 SFTP 旨在作為臨時儲存空間，您可以在其上控製檔案的保留和刪除。

如果未正確使用或監視此空間，則此空間可以快速填充伺服器上可用的物理空間，並導致在後續上載時截斷檔案。一旦空間飽和，自動清除可以觸發並從 SFTP 儲存器中刪除最舊的檔案。

為避免此類問題，Adobe建議遵循下列最佳實務。

>[!NOTE]
>
>如果您的執行個體託管在 AWS 上，則可以使用 Campaign Classic [控制面板](https://docs.adobe.com/content/help/en/control-panel/using/sftp-management/sftp-storage-management.html)監控 SFTP 伺服器儲存。
>
>要檢查您的執行個體是否託管在 AWS 上，請按照[本節](https://docs.adobe.com/content/help/zh-Hant/control-panel/using/faq.html#ims-org-id)詳述的步驟操作。

* 伺服器大小功能因許可證而異。在任何情況下，儘量保持最小資料，並且只在需要的時間內保留資料 (15 天是最長時間限制)。
* 使用基於密鑰的身份驗證而不是密碼身份驗證，以避免密碼過期 (密碼的有效期為 90 天)。此外，基於金鑰的身份驗證允許您生成多個金鑰，例如在管理多個實體時。相反，密碼身份驗證要求您與所管理的所有實體共享密碼。

   支持的金鑰格式為 SSH-2 RSA 2048。金鑰可以通過PuTTY (Windows) 或 ssh-keygen (UNIX) 等工具生成。你將必須通過[支援票證](https://support.neolane.net) 為 Adobe 支援團隊提供公共金鑰，將它上傳到活動伺服器上。

* 使用工作流程正確刪除資料（管理使用資料的工作流程的保留）。
* 在 SFTP 上載和工作流程中使用批次處理。
* 處理錯誤/例外狀況。
* 時常登入 SFTP 以直接檢查其內容。
* 請記住，SFTP 硬碟的管理主要是您的責任。
* 按照預設，您建立的所有資料夾僅為標識符的讀/寫模式。建立需要由 Campaign 存取的資料夾時，請確保使用整個組的讀/寫權限進行配置。否則，出於安全原因，工作流程可能無法建立/刪除檔案，因為它們在同一組內的不同標識符下運行。
* 您嘗試從中啟動SFTP連線的公用IP必須新增至促銷活動例項的允許清單。 將IP位址新增至允許清單可透過支援票證 [要求](https://support.neolane.net)。

>[!CAUTION]
>
>如果您使用自己的 SFTP 伺服器，請務必儘可能遵循上述建議。

## Adobe代管SFTP伺服器的連線問題 {#sftp-server-troubleshooting}

以下部分列出了在遇到與 Adobe 託管的 SFTP 伺服器的連接問題時，通過[支援票證](https://support.neolane.net)檢查並提供給 Adobe 支援團隊的資訊。

1. 檢查您的執行個體是否正在運行。To do this, open your browser, then make a **[!UICONTROL GET]** call on the instance **[!UICONTROL /r/test]** endpoint:

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

   如果埠未打開，請確保打開側面的傳出連線，然後重試。如果仍遇到連接問題，請與 Adobe 支援團隊分享該命令的輸出。

1. 檢查您嘗試從中啟動SFTP連線的公用IP是否是您提供給Adobe支援的允許清單。
1. 如果您使用密碼驗證，您的密碼可能已過期（密碼的有效期為90天）。 因此，我們強烈建議使用基於密鑰的驗證(請參 [閱SFTP伺服器最佳實務](#sftp-server-best-practices))。
1. 如果您使用的是基於金鑰的身份驗證，請檢查您使用的金鑰是否與為執行個體配置提供給 Adobe 支援團隊的金鑰相同。
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

1. 疑難排 **解DNS伺服器組態**:

   1. 檢查伺服器名稱是否已添加到本地DNS伺服器中。
   1. 如果是，請在Adobe Campaign伺服器上執行下列命令以取得IP位址：

   `nslookup <server domain name>`

   這可確認FTP伺服器是否運作，並可從Adobe Campaign應用程式伺服器存取。

1. 疑難排 **解作業記錄**:

   1. 在工作流程中，連按兩下「檔 [案傳輸](../../workflow/using/file-transfer.md) 」活動。
   1. 移至標 **[!UICONTROL File Transfer]** 簽，然後按一下 **[!UICONTROL Advanced Parameters]**。
   1. 核取 **[!UICONTROL Display the session logs]** 選項。

   ![](assets/sftp-error-display-logs.png)

   1. 轉至工作流審計並檢查日誌是否顯示「無法解析主機名」錯誤。

   如果SFTP伺服器由Adobe代管，請聯絡客戶服務以檢查IP是否已新增至允許清單。

   否則請驗證：

   * 密碼不包含「@」。 如果密碼中有「@」，則連接失敗。
   * 沒有防火牆問題會妨礙Adobe Campaign應用程式伺服器與SFTP伺服器之間的通訊。
   * 從促銷活動伺服器執行tracert和telnet命令至sftp，以查看是否有連線問題。
   * 沒有通信協定問題。
   * 埠已開啟。
