---
solution: Campaign Classic
product: campaign
title: 設定 SpamAssassin
description: 設定 SpamAssassin
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 33debcd6e399d2780277644103a620d46c22022e
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 1%

---


# 設定 SpamAssassin{#configuring-spamassassin}

>[!NOTE]
>
>有些組態只能由Adobe針對Adobe代管的部署執行。 例如，訪問伺服器和實例配置檔案。 若要進一步瞭解不同的部署，請參閱[代管模型](../../installation/using/hosting-models.md)一節或[本頁](../../installation/using/capability-matrix.md)。

## 概觀 {#overview}

SpamAssassin是一套軟體，可用來篩選不想要的電子郵件。 搭配本軟體，Adobe Campaign可以指派分數給電子郵件，並判斷在傳送啟動之前，訊息是否可能被視為不需要。 為此，必須在Adobe Campaign的應用程式伺服器上安裝並設定SpamAssassin，並需要特定數量的額外Perl模組才能運作。

本章所述的SpamAssassin的部署和整合基於預設軟體安裝，過濾和計分規則也基於預設軟體安裝，這些規則是SpamAssassin提供的，無需進行任何更改或優化。 分數歸因和訊息限定完全以SpamAssassin選項的設定和篩選規則為基礎。 網路管理員負責根據公司的需要調整網路管理員。

>[!IMPORTANT]
>
>SpamAssassin將電子郵件視為不想要的，完全以篩選和計分規則為基礎。
>
>因此，您必須每天至少更新這些規則一次，才能讓SpamAssassin安裝及其與Adobe Campaign的整合功能完整運作，並確保在傳送前指派給傳送的分數相關性。
>
>此更新由代管SpamAssassin的伺服器管理員負責。

在Adobe Campaign中使用SpamAssassin可指出使用SpamAssassin的郵件伺服器在收到Adobe Campaign傳送的電子郵件時的可能行為。 不過，網際網路供應商或線上郵件伺服器的郵件伺服器仍可能認為Adobe Campaign傳送的訊息不受歡迎。

在Perl中部署SpamAssassin及其模組需要Adobe Campaign應用程式伺服器具備透過HTTP連線（TCP/80流程）進行網際網路存取的功能。

## 在Windows電腦上安裝{#installing-on-a-windows-machine}

若要在Windows上安裝並設定SpamAssassin，以便與Adobe Campaign整合，請套用下列步驟：

1. 安裝SpamAssassin
1. 將SpamAssassin整合至Adobe Campaign

### 安裝SpamAssassin {#installing-spamassassin}

1. 使用您的用戶憑證連接到[軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。 在[本頁](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)中進一步瞭解軟體分發。
1. 下載&#x200B;**Neolane Spam Assassin（Windows安裝）(2.0)**&#x200B;檔案(neolane_spamassassin.2.0.zip)。
1. 將此檔案複製至Adobe Campaign伺服器，然後解壓縮。

   >[!NOTE]
   >
   >只要路徑由下列任何規則運算式字元組成，您就可以選擇隨處解壓縮檔案：**`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**。 安裝路徑不得包含任何空格字元。

1. 轉至已解壓縮檔案的檔案，然後按兩下&#x200B;**run_me.bat**&#x200B;檔案以啟動安裝指令碼。

   如果出現Windows Shell並繼續顯示幾秒鐘，請等待安裝和更新完成，然後按一下&#x200B;**Enter**。

   如果Windows Shell未出現或未在立即消失之前顯示，請遵循下列步驟，按兩下&#x200B;**portableShell.bat**&#x200B;檔案以顯示Windows Shell，並檢查Shell路徑是否與&#x200B;**spamassassin檔案已解壓縮的資料夾相對應。**&#x200B;如果不是這樣，請使用&#x200B;**cd**&#x200B;命令訪問它。

   輸入&#x200B;**run_me.bat**，然後按一下&#x200B;**Enter**&#x200B;以開始安裝和更新程式。 該操作返回以下值之一，以指示更新結果。

   * **0**:已執行更新。
   * **1**:沒有新的更新可用。
   * **2**:沒有新的更新可用。
   * **3**:更新在先前驗證期間失敗。
   * **4** 或以上：發生錯誤。

1. 若要檢查SpamAssassin是否成功安裝，請使用GTUBE測試（未經請求的大量電子郵件的一般測試），請執行下列程式：

   1. 建立文字檔案並儲存在&#x200B;**C:\TestSpamMail.txt**&#x200B;下。
   1. 將下列內容插入檔案：

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

   1. 連按兩下&#x200B;**portableShell.bat**&#x200B;檔案以顯示Windows Shell，然後啟動下列命令（或&quot;`<root>`&quot;在解壓縮&#x200B;**spamassassin.zip**&#x200B;檔案時指定已建立的檔案夾）:

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      此測試電子郵件的內容會觸發SpamAssassin的1,000分分。 這表示已偵測到不需要，且安裝已成功且完全正常運作。

### 將SpamAssassin整合至Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. 編輯&#x200B;**`[INSTALL]/conf/serverConf.xml`**&#x200B;檔案。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。
1. 在&#x200B;**Web**&#x200B;節點中更改&#x200B;**spamCheck** elements&#39; **command**&#x200B;屬性的值。 要執行此操作，請運行以下命令：

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >所有路徑都必須是絕對的。

   停止並啟動&#x200B;**[!UICONTROL Adobe Campaign]**&#x200B;服務。

1. 若要檢查Adobe Campaign中SpamAssassin的整合，請使用GTBUE測試（未經請求的大量電子郵件的一般測試）:

   連按兩下&#x200B;**portableshell.bat**&#x200B;檔案。 這會觸發Windows殼層的顯示。 然後執行下列命令：

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   此測試電子郵件的內容會觸發SpamAssassin指派的1,000點。 這表示已偵測到它不需要，而且Adobe Campaign的整合是成功的，而且具備完整功能。

1. 更新SpamAssassin篩選和計分規則

   如需篩選和計分規則的初始更新，請啟動&#x200B;**portableShell.bat**&#x200B;並執行下列命令：

   ```
   sa-update --no-gpg
   ```

   要運行過濾和計分規則的自動更新，請在計畫的系統任務中使用以下相同命令：

   ```
   sa-update --no-gpg
   ```

## 在Linux電腦{#installing-on-a-linux-machine}上安裝

### Debian {#installation-steps-in-debian}中的安裝步驟

* 如有必要，請使用以下命令安裝Perl和SpamAssassin:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* 在&#x200B;**serverConf.xml**&#x200B;檔案（可在`/usr/local/[INSTALL]/nl6/conf/`中取得）中，變更&#x200B;**spamCheck**&#x200B;一行，如下所示：

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### RHEL/CentOS {#installation-steps-in-rhel-centos}中的安裝步驟

如有必要，請安裝Perl並使用CPAN恢復軟體包：

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### 更新篩選規則{#updating-filter-rules}

可使用&#x200B;**sa-update**&#x200B;工具自動更新篩選規則。 如需詳細資訊，請參閱官方的SpamAssassin網站[http://spamassassin.apache.org/](http://spamassassin.apache.org/)。

在Debian中，更新會每天自動進行。

如果不是這樣（例如手動安裝Debian時），請建立指令碼以自動更新規則。

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

使用以下命令將此指令碼插入&#x200B;**crontab**:

```
crontab-e
```

### 效能優化{#performance-optimization}

若要改善Linux的效能，請編輯&#x200B;**/etc/spamassassin/local.cf**&#x200B;檔案，並在檔案結尾加入下列行：

```
dns_available no
```

