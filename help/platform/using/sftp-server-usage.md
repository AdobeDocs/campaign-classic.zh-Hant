---
product: campaign
title: SFTP 伺服器使用情況
description: 深入瞭解SFTP伺服器最佳實務及疑難排解
feature: Troubleshooting
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: b02089bd205de58c6af86fc8de3d5b3294ec9975
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 21%

---

# SFTP 伺服器最佳實務及疑難排解 {#sftp-server-usage}

## SFTP伺服器全域建議 {#global-recommendations}

管理用於 ETL 的檔案和資料時，這些檔案儲存在 Adobe 提供的代管 SFTP 伺服器上。使用SFTP伺服器時，請務必遵循下列建議。

* 為避免密碼過期（密碼的有效期為90天），請使用以金鑰為基礎的驗證而非密碼驗證。 此外，以金鑰為基礎的驗證可讓您產生多個金鑰，例如在管理多個實體時。 相反，密碼身份驗證要求您與所管理的所有實體共享密碼。

  支援的金鑰格式為SSH-2 RSA 2048。 為Windows產生SSH金鑰的工具為PuTTYgen，而為Linux產生ssh-keygen。 您可以透過Campaign「控制面板」上傳公開SSH金鑰。 [了解更多](https://experienceleague.adobe.com/en/docs/control-panel/using/sftp-management/key-management){target="_blank"}

* 在 SFTP 上載和工作流程中使用批次處理。

* 處理錯誤/例外狀況。

* 依預設，您建立的所有資料夾都處於唯有識別碼的讀/寫模式。 建立需要Campaign存取的資料夾時，請務必以整個群組的讀取/寫入許可權來設定資料夾。 否則，出於安全原因，工作流程可能無法建立/刪除檔案，因為它們在同一組內的不同標識符下運行。

* 您嘗試啟動SFTP連線的公用IP必須新增至Campaign執行個體上的允許清單。 您可以透過「控制面板」新增公用IP。 [了解更多](https://experienceleague.adobe.com/en/docs/control-panel/using/sftp-management/ip-range-allow-listing){target="_blank"}

## SFTP儲存空間使用量最佳實務 {#sftp-server-best-practices}

SFTP伺服器是設計作為暫存空間，您可以在其上控制檔案的保留和刪除。

若未正確使用或監控，這些空間會快速填滿伺服器上可用的實體空間，並導致檔案在後續上傳時被截斷。 一旦空間飽和，自動清除可以觸發並從 SFTP 儲存器中刪除最舊的檔案。

為避免此類問題，Adobe建議遵循以下最佳實務。

>[!NOTE]
>
>您可以使用Campaign Classic監視SFTP伺服器儲存空間 [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html){target="_blank"}.
>
>所有管理員使用者都可存取控制面板。 授予使用者管理員存取許可權的步驟已詳載於 [此頁面](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hant#discover-control-panel){target="_blank"}.
>
>請注意，您的執行個體必須升級為 [最新GA版本](../../rn/using/rn-overview.md). 瞭解如何簽入您的版本 [本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version){target="_blank"}.

* 伺服器大小功能會依您的授權而有所不同。 在任何情況下，儘量保持最小資料，並且只在需要的時間內保留資料 (15 天是最長時間限制)。

* 使用工作流程正確刪除資料（管理使用資料的工作流程的保留）。

* 時常登入 SFTP 以直接檢查其內容。

* 請記住，SFTP 硬碟的管理主要是您的責任。

## 外部SFTP伺服器使用情況 {#external-SFTP-server}

如果您使用自己的SFTP伺服器，請務必儘可能遵循上述建議。

此外，在Campaign Classic中指定外部SFTP伺服器的路徑時，路徑語法會因SFTP伺服器作業系統而異：

* 如果您的SFTP伺服器已開啟 **Windows**，請一律使用相對路徑。
* 如果您的STP伺服器已開啟 **Linux**，請一律使用與首頁相關的路徑（以「~/」開頭）或絕對路徑（以「/」開頭）。

## Adobe代管SFTP伺服器的連線問題 {#sftp-server-troubleshooting}

以下區段列出要檢查的資訊，並透過提供給Adobe支援團隊 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"} 遇到Adobe代管SFTP伺服器的連線問題時。

1. 檢查您的執行個體是否正在執行。 若要這麼做，請開啟瀏覽器，然後進行 **[!UICONTROL GET]** 在執行個體上呼叫 **[!UICONTROL /r/test]** 端點：

   ```
   https://instanceUrl/r/test
   ```

   如果執行個體正在運行，您應該得到這種類型的回應：

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instance-name'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instance-name'/>
   ```

   在任何情況下，請在支援票證中提供命令回應。

1. 檢查輸出連線埠22是否已在您嘗試啟動SFTP連線的站台開啟。 為此，請使用以下命令：

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   如果未開啟連線埠，請確定開啟您這端的輸出連線，然後再試一次。 如果您仍然遇到連線問題，請將命令的輸出分享給 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 團隊。

1. 檢查您嘗試啟動SFTP連線的公用IP是否為允許清單提供給Adobe支援的IP。
1. 如果您使用以密碼為基礎的驗證，您的密碼可能已過期（密碼的有效期為90天）。 因此，我們強烈建議使用金鑰式驗證(請參閱 [SFTP伺服器最佳實務](#sftp-server-best-practices))。
1. 如果您使用金鑰式驗證，請檢查您使用的金鑰是否與提供給的金鑰相同 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 執行個體組態的團隊。
1. 如果您使用的是 FileZilla 或類似的 FTP 工具，請在支援票證中提供連線日誌詳細資訊。

## 「無法解析主機名稱」錯誤

本節提供從Campaign Classic連線至FTP伺服器後收到「無法解析主機名稱」錯誤時，所要執行的檢查和動作的相關資訊。

工作流程日誌會顯示以下記錄：

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

當您仍可使用FileZilla或WinSCP透過FTP連線時，嘗試從工作流程連線FTP伺服器並從伺服器下載檔案時，會發生此錯誤。

此錯誤表示無法正確解析FTP伺服器網域名稱。 若要進行疑難排解，請執行下列動作：

1. 疑難排解 **DNS伺服器設定**：

   1. 檢查伺服器名稱是否已新增至本機DNS伺服器。
   1. 如果是，請在Adobe Campaign伺服器上執行下列命令以取得IP位址：

      `nslookup <server domain name>`

      這可確認FTP伺服器是否正常運作，以及是否可從Adobe Campaign應用程式伺服器連線。

1. 疑難排解 **工作階段記錄檔**：

   1. 在工作流程中，按兩下 [檔案傳輸](../../workflow/using/file-transfer.md) 活動。
   1. 前往 **[!UICONTROL File Transfer]** 標籤，然後按一下 **[!UICONTROL Advanced Parameters]**.
   1. 核取 **[!UICONTROL Display the session logs]** 選項。

      ![](assets/sftp-error-display-logs.png)

   1. 前往工作流程稽核，並檢查記錄檔是否顯示「無法解析主機名稱」錯誤。

1. 如果SFTP伺服器是由Adobe託管，請聯絡客戶服務，以檢查IP是否已新增至允許清單。

   否則，請驗證：

   * 密碼不包含&#39;@&#39;。 如果密碼中有&#39;@&#39;，連線會失敗。
   * 沒有防火牆問題會阻礙Adobe Campaign應用程式伺服器與SFTP伺服器之間的通訊。
   * 從campaign伺服器執行tracert和telnet命令至sftp，檢視是否有任何連線問題。
   * 沒有通訊協定問題。
   * 連線埠已開啟。
