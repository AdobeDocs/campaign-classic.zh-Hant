---
product: campaign
title: 設定 SpamAssassin
description: 設定 SpamAssassin
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 2%

---

# 設定 SpamAssassin{#configuring-spamassassin}



>[!NOTE]
>
>某些設定只能由Adobe執行，以供Adobe托管的部署使用。 例如，要訪問伺服器和實例配置檔案。 若要進一步了解不同部署，請參閱 [托管模型](../../installation/using/hosting-models.md) 區段或 [本頁](../../installation/using/capability-matrix.md).

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

1. 連線至 [軟體發佈門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 使用您的使用者憑證。 深入了解Software Distribution，位於 [本頁](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant?lang=en).
1. 下載 **Neolane Spam Assassin（Windows安裝）(2.0)** 檔案(neolane_spamassassin.2.0.zip)。
1. 將此檔案複製到Adobe Campaign伺服器，然後解壓縮。

   >[!NOTE]
   >
   >只要路徑由下列任何規則運算式字元組成，您就可以選擇將檔案解壓縮到任何需要的位置： **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. 安裝路徑不得包含任何空白字元。

1. 前往已解壓縮檔案的檔案，然後連按兩下 **run_me.bat** 檔案來啟動安裝指令碼。

   如果出現Windows殼層並繼續顯示幾秒，請等到安裝和更新完成，然後按一下 **輸入**.

   如果在立即消失之前Windows殼層未出現或未顯示，請執行這些步驟，按兩下 **portableShell.bat** 檔案，以顯示「Windows殼層」，並檢查「殼層」路徑是否與 **spamassassin.zip** 檔案已解壓縮。 若非如此，請使用 **cd** 命令。

   輸入 **run_me.bat** 然後按一下 **輸入** 以啟動安裝和更新過程。 操作將返回以下值之一，以指示更新的結果。

   * **0**:已執行更新。
   * **1**:沒有新的更新可用。
   * **2**:沒有新的更新可用。
   * **3**:在先前驗證期間更新失敗。
   * **4** 或更多：發生錯誤。

1. 若要檢查SpamAssassin安裝是否成功，請使用下列程式進行GTUBE測試（未經請求的大量電子郵件的一般測試）:

   1. 建立文字檔案並儲存在 **C:\TestSpamMail.txt**.
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

   1. 按兩下 **portableShell.bat** 檔案，顯示Windows殼層，然後啟動以下命令(或「`<root>`&quot;會在解壓縮  **spamassassin.zip** 檔案):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      此測試電子郵件的內容會觸發SpamAssassin的1,000分。 這意味著，它被檢測為不受歡迎，並且安裝成功並且完全正常。

### 將SpamAssassin整合至Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. 編輯 **`[INSTALL]/conf/serverConf.xml`** 檔案。 中所有可用的參數 **serverConf.xml** 列於此 [節](../../installation/using/the-server-configuration-file.md).
1. 變更 **spamCheck** 元素 **命令** 屬性 **Web** 節點。 要執行此操作，請運行以下命令：

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >所有路徑都必須是絕對路徑。

   停止並啟動 **[!UICONTROL Adobe Campaign]** 服務。

1. 若要使用GTBUE測試（未經請求的大量電子郵件的一般測試）來檢查Adobe Campaign中SpamAssassin的整合：

   按兩下 **portableshell.bat** 檔案。 這會觸發Windows殼層的顯示。 然後執行下列命令：

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   此測試電子郵件的內容會觸發SpamAssassin指派的1,000點。 這表示，Adobe Campaign的整合工作成功且完全正常運作，因此被偵測為不樂見。

1. 更新SpamAssassin篩選和計分規則

   如需篩選和計分規則的初始更新，請開始 **portableShell.bat** 並運行以下命令：

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

* 在 **serverConf.xml** 檔案(可在 `/usr/local/[INSTALL]/nl6/conf/`)，變更 **spamCheck** 行，如下所示：

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

可使用 **sa-update** 工具。 請參閱官方的SpamAssassin網站 [https://spamassassin.apache.org/](https://spamassassin.apache.org/) 以取得更多資訊。

在Debian中，每天會自動進行更新。

若非如此（例如手動安裝Debian時），請建立指令碼以自動進行規則更新。

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

將此指令碼插入 **crontab** 使用下列命令：

```
crontab-e
```

### 效能最佳化 {#performance-optimization}

若要改善Linux的效能，請編輯 **/etc/spamassassin/local.cf** 檔案，並在檔案結尾處新增下列行：

```
dns_available no
```
