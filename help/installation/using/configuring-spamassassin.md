---
product: campaign
title: 設定SpamAssassin
description: 設定SpamAssassin
feature: Installation, Instance Settings
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# 設定SpamAssassin{#configuring-spamassassin}



>[!NOTE]
>
>部分設定只能由Adobe代管的部署Adobe執行。 例如，存取伺服器和執行個體組態檔。 若要瞭解不同部署的詳細資訊，請參閱[託管模型](../../installation/using/hosting-models.md)區段或[此頁面](../../installation/using/capability-matrix.md)。

## 概覽 {#overview}

SpamAssassin是專為篩選不想要的電子郵件而設計的軟體。 結合此軟體，Adobe Campaign可為電子郵件指派分數，並在啟動傳遞前判斷訊息是否有可能被視為不想要的訊息。 為此，必須在Adobe Campaign的應用程式伺服器上安裝和設定SpamAssassin，並需要一定數量的額外Perl模組才能運作。

本章所述的SpamAssassin部署和整合是以預設軟體安裝為基礎，篩選和評分規則也是如此，這些是SpamAssassin所提供的規則，沒有任何變更或最佳化。 評分歸因和訊息資格完全以SpamAssassin選項的設定和篩選規則為基礎。 網路管理員負責根據公司的需求調整其內容。

>[!IMPORTANT]
>
>SpamAssassin會將電子郵件限定為不受歡迎，這完全是根據篩選和評分規則。
>
>因此，這些規則必須每天至少更新一次，才能讓您的SpamAssassin安裝及其與Adobe Campaign的整合全面運作，並確保在傳送之前指派給您傳送的評分具有相關性。
>
>此更新由裝載SpamAssassin的伺服器管理員負責。

在Adobe Campaign中使用SpamAssassin可指示使用SpamAssassin的郵件伺服器在收到Adobe Campaign傳送的電子郵件時的可能行為。 不過，網際網路提供者或線上郵件伺服器的郵件伺服器可能仍認為Adobe Campaign傳送的郵件不合需要。

在Perl中部署SpamAssassin及其模組，需要Adobe Campaign應用程式伺服器配備透過HTTP連線（TCP/80流程）的網際網路存取。

## 在Windows電腦上安裝 {#installing-on-a-windows-machine}

若要在Windows上安裝和設定SpamAssassin以啟用與Adobe Campaign的整合，請套用下列步驟：

1. 安裝SpamAssassin
1. 將SpamAssassin整合至Adobe Campaign

### 安裝SpamAssassin {#installing-spamassassin}

1. 使用您的使用者認證連線至[軟體發佈入口網站](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。 在[此頁面](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant)中進一步瞭解軟體發佈。
1. 下載&#x200B;**Neolane Spam Assassin （Windows安裝） (2.0)**&#x200B;檔案(neolane_spamassassin.2.0.zip)。
1. 將此檔案複製到Adobe Campaign伺服器，然後解壓縮。

   >[!NOTE]
   >
   >只要路徑由下列任一規則運算式字元組成，您就可以選擇在任何地方將檔案解壓縮： **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**。 安裝路徑不得包含任何空白字元。

1. 移至您解壓縮檔案的檔案，然後按兩下&#x200B;**run_me.bat**&#x200B;檔案以啟動安裝指令碼。

   如果Windows Shell出現並持續顯示幾秒鐘，請等候安裝與更新完成，然後按一下&#x200B;**進入**。

   如果Windows Shell未出現或未在立即消失之前顯示，請依照下列步驟，連按兩下&#x200B;**portableShell.bat**&#x200B;檔案以顯示Windows Shell，並檢查Shell路徑是否對應到&#x200B;**spamassassin.zip**&#x200B;檔案已解壓縮的資料夾。 如果不是這種情況，請使用&#x200B;**cd**&#x200B;命令來存取它。

   輸入&#x200B;**run_me.bat**，然後按一下&#x200B;**Enter**&#x200B;以開始安裝和更新程式。 作業會傳回下列其中一個值，以表示更新結果。

   * **0**：已執行更新。
   * **1**：沒有可用的新更新。
   * **2**：沒有可用的新更新。
   * **3**：先前驗證期間更新失敗。
   * **4**&#x200B;或更多：發生錯誤。

1. 若要檢查SpamAssassin安裝是否成功，請使用以下程式使用GTUBE測試（針對未經請求的大量電子郵件的通用測試）：

   1. 建立文字檔，並儲存在&#x200B;**C:\TestSpamMail.txt**&#x200B;下。
   1. 將下列內容插入檔案中：

      ```
      Subject: Test Spam Mail (GTUBE)
      Message-ID: <1010101@example.net>
      Date: MM-DD-YY
      From: Sender <sender@example.net>
      To: Recipient <recipient@example.net>
      Precedence: junk
      MIME-Version: 1.0
      Content-Type: text/plain; charset=us-ascii
      Content-Transfer-Encoding: 7bit
      
      XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
      ```

   1. 連按兩下&#x200B;**portableShell.bat**&#x200B;檔案以顯示Windows Shell，然後啟動下列命令（或在解壓縮&#x200B;**spamassassin.zip**&#x200B;檔案時指定&quot;`<root>`&quot;已建立的資料夾）：

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      此測試電子郵件的內容會觸發SpamAssassin的1,000分評分。 這表示偵測到它是不想要的，而且安裝成功且完全正常運作。

### 將SpamAssassin整合至Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. 編輯&#x200B;**`[INSTALL]/conf/serverConf.xml`**&#x200B;檔案。 **serverConf.xml**&#x200B;中可用的所有引數都列在此[區段](../../installation/using/the-server-configuration-file.md)中。
1. 變更&#x200B;**Web**&#x200B;節點中&#x200B;**spamCheck**&#x200B;專案&#39; **命令**&#x200B;屬性的值。 要執行此操作，請執行以下命令：

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >所有路徑都必須是絕對路徑。

   停止並啟動&#x200B;**[!UICONTROL Adobe Campaign]**&#x200B;服務。

1. 若要檢查Adobe Campaign中SpamAssassin的整合，請使用GTBUE測試（未經請求的大量電子郵件的通用測試）：

   連按兩下&#x200B;**portableshell.bat**&#x200B;檔案。 這會觸發Windows Shell的顯示。 然後執行下列命令：

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   此測試電子郵件的內容會觸發SpamAssassin指派的1,000點。 這表示系統偵測到不想要的專案，且Adobe Campaign中的整合已順利完成，且可完全正常運作。

1. 更新SpamAssassin篩選和評分規則

   若要進行篩選和評分規則的初始更新，請啟動&#x200B;**portableShell.bat**，然後執行下列命令：

   ```
   sa-update --no-gpg
   ```

   若要執行篩選和評分規則的自動更新，請在排程的系統工作中使用此相同的命令：

   ```
   sa-update --no-gpg
   ```

## 在Linux機器上安裝 {#installing-on-a-linux-machine}

### Debian中的安裝步驟 {#installation-steps-in-debian}

* 如有必要，請使用以下命令安裝Perl和SpamAssassin：

  ```
  apt-get install spamassassin libxml-writer-perl
  ```

* 在&#x200B;**serverConf.xml**&#x200B;檔案（可在`/usr/local/[INSTALL]/nl6/conf/`中使用）中，變更&#x200B;**spamCheck**&#x200B;行，如下所示：

  ```
  <spamCheck command="perl
  /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
  ```

### RHEL/CentOS中的安裝步驟 {#installation-steps-in-rhel-centos}

如有必要，請安裝Perl並使用CPAN復原套件：

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### 更新篩選規則 {#updating-filter-rules}

可使用&#x200B;**sa-update**&#x200B;工具自動更新篩選器規則。 如需詳細資訊，請參閱官方SpamAssassin網站[https://spamassassin.apache.org/](https://spamassassin.apache.org/)。

在Debian中，每天都會自動進行更新。

如果不是這種情況（例如當Debian手動安裝時），請建立指令碼以自動化規則更新。

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

使用以下命令將此指令碼插入&#x200B;**crontab**：

```
crontab-e
```

### 效能最佳化 {#performance-optimization}

若要在Linux中改善效能，請編輯&#x200B;**/etc/spamassassin/local.cf**&#x200B;檔案，並在檔案結尾加入下列行：

```
dns_available no
```
