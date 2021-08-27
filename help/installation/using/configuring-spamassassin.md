---
product: campaign
title: 設定 SpamAssassin
description: 設定 SpamAssassin
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 2%

---

# 設定 SpamAssassin{#configuring-spamassassin}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>某些設定只能由Adobe執行，以供Adobe托管的部署使用。 例如，要訪問伺服器和實例配置檔案。 若要進一步了解不同部署，請參閱[托管模型](../../installation/using/hosting-models.md)區段或[此頁面](../../installation/using/capability-matrix.md)。

## 概覽 {#overview}

SpamAssassin是一款軟體，用於過濾不期望的電子郵件。 結合此軟體後，Adobe Campaign可為電子郵件指派分數，並在啟動傳送前判斷訊息是否可能被視為不受歡迎。 要執行此操作，必須在Adobe Campaign的應用程式伺服器上安裝並配置SpamAssassin，並需要特定數量的額外Perl模組才能運行。

本章中所述的SpamAssassin的部署和整合基於預設軟體安裝，篩選和計分規則也是基於預設軟體安裝，這些規則由SpamAssassin提供，無需任何更改或優化。 分數歸因和訊息資格僅根據SpamAssassin選項的設定和篩選規則。 網路管理員負責根據公司的需要調整它們。

>[!IMPORTANT]
>
>SpamAssassin將電子郵件認定為不受歡迎的郵件，完全基於篩選和計分規則。
>
>因此，必須每天至少更新一次這些規則，才能讓您的SpamAssassin安裝及其與Adobe Campaign的整合完整運作，並保證在傳送前將分數指派給您的傳送的相關性。
>
>此更新由托管SpamAssassin的伺服器管理員負責。

在Adobe Campaign中使用SpamAssassin可指出使用SpamAssassin的郵件伺服器在收到Adobe Campaign傳送的電子郵件時的可能行為。 但是，網際網路提供者或線上郵件伺服器的郵件伺服器可能仍認為Adobe Campaign發送的郵件不受歡迎。

在Perl中部署SpamAssassin及其模組需要Adobe Campaign應用程式伺服器通過HTTP連接（TCP/80流）配備Internet訪問。

## 在Windows電腦上安裝 {#installing-on-a-windows-machine}

若要在Windows上安裝和設定SpamAssassin以啟用與Adobe Campaign的整合，請套用下列步驟：

1. 安裝SpamAssassin
1. 將SpamAssassin整合至Adobe Campaign

### 安裝SpamAssassin {#installing-spamassassin}

1. 使用您的用戶憑據連接到[Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。 了解更多[本頁](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant?lang=en)中的軟體分發。
1. 下載&#x200B;**Neolane Spam Assassin（Windows安裝）(2.0)**&#x200B;檔案(neolane_spamassassin.2.0.zip)。
1. 將此檔案複製到Adobe Campaign伺服器，然後解壓縮。

   >[!NOTE]
   >
   >只要路徑由下列任何規則運算式字元組成，您就可以選擇將檔案解壓縮到任何需要的位置：**`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**。 安裝路徑不得包含任何空白字元。

1. 轉到已解壓檔案的檔案，然後按兩下&#x200B;**run_me.bat**&#x200B;檔案以啟動安裝指令碼。

   如果出現Windows Shell並繼續顯示幾秒，請等到安裝和更新完成，然後按一下&#x200B;**Enter**。

   如果Windows Shell在立即消失之前未出現或未顯示，請執行這些步驟，按兩下&#x200B;**portableShell.bat**&#x200B;檔案以顯示Windows Shell，並檢查Shell路徑是否與&#x200B;**spamassassin.zip**&#x200B;檔案已解壓縮的資料夾相對應。 如果不是，請使用&#x200B;**cd**&#x200B;命令訪問它。

   輸入&#x200B;**run_me.bat**，然後按一下&#x200B;**Enter**&#x200B;以啟動安裝和更新過程。 操作將返回以下值之一，以指示更新的結果。

   * **0**:已執行更新。
   * **1**:沒有新的更新可用。
   * **2**:沒有新的更新可用。
   * **3**:在先前驗證期間更新失敗。
   * **4** 或更多：發生錯誤。

1. 若要檢查SpamAssassin安裝是否成功，請使用下列程式進行GTUBE測試（未經請求的大量電子郵件的一般測試）:

   1. 建立文本檔案並將其保存在&#x200B;**C:\TestSpamMail.txt**&#x200B;下。
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

   1. 連按兩下&#x200B;**portableShell.bat**&#x200B;檔案以顯示Windows Shell，然後啟動以下命令（或在解壓縮&#x200B;**spamassassin.zip**&#x200B;檔案時指定已建立的資料夾&quot;`<root>`&quot;）:

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      此測試電子郵件的內容會觸發SpamAssassin的1,000分。 這意味著，它被檢測為不受歡迎，並且安裝成功並且完全正常。

### 將SpamAssassin整合至Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. 編輯&#x200B;**`[INSTALL]/conf/serverConf.xml`**&#x200B;檔案。 **serverConf.xml**&#x200B;中所有可用的參數都列在此[節](../../installation/using/the-server-configuration-file.md)中。
1. 更改&#x200B;**Web**&#x200B;節點中&#x200B;**spamCheck**&#x200B;元素&#39; **command**&#x200B;屬性的值。 要執行此操作，請運行以下命令：

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >所有路徑都必須是絕對路徑。

   停止並啟動&#x200B;**[!UICONTROL Adobe Campaign]**&#x200B;服務。

1. 若要使用GTBUE測試（未經請求的大量電子郵件的一般測試）來檢查Adobe Campaign中SpamAssassin的整合：

   連按兩下&#x200B;**portableshell.bat**&#x200B;檔案。 這會觸發Windows殼層的顯示。 然後執行下列命令：

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   此測試電子郵件的內容會觸發SpamAssassin指派的1,000點。 這表示，Adobe Campaign的整合工作成功且完全正常運作，因此被偵測為不樂見。

1. 更新SpamAssassin篩選和計分規則

   有關篩選和計分規則的初始更新，請啟動&#x200B;**portableShell.bat**&#x200B;並運行以下命令：

   ```
   sa-update --no-gpg
   ```

   要運行篩選和計分規則的自動更新，請在計畫系統任務中使用以下相同命令：

   ```
   sa-update --no-gpg
   ```

## 在Linux電腦上安裝 {#installing-on-a-linux-machine}

### 在Debian中安裝步驟 {#installation-steps-in-debian}

* 如有必要，請使用以下命令安裝Perl和SpamAssassin:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* 在&#x200B;**serverConf.xml**&#x200B;檔案（可在`/usr/local/[INSTALL]/nl6/conf/`中取得）中，變更&#x200B;**spamCheck**&#x200B;行，如下所示：

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### 在RHEL/CentOS中安裝步驟 {#installation-steps-in-rhel-centos}

如有必要，請安裝Perl並使用CPAN恢復包：

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

可使用&#x200B;**sa-update**&#x200B;工具自動更新篩選規則。 如需詳細資訊，請參閱官方的SpamAssassin網站[http://spamassassin.apache.org/](http://spamassassin.apache.org/) 。

在Debian中，每天會自動進行更新。

若非如此（例如手動安裝Debian時），請建立指令碼以自動進行規則更新。

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

使用以下命令將此指令碼插入&#x200B;**crontab**&#x200B;中：

```
crontab-e
```

### 效能最佳化 {#performance-optimization}

若要改善Linux中的效能，請編輯&#x200B;**/etc/spamassassin/local.cf**&#x200B;檔案，並在檔案結尾處新增下列行：

```
dns_available no
```
