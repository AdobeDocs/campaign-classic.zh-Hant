---
product: campaign
title: 設定 SpamAssassin
description: 設定 SpamAssassin
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 2%

---

# 設定 SpamAssassin{#configuring-spamassassin}



>[!NOTE]
>
>某些配置只能通過Adobe執行由Adobe承載的部署。 例如，訪問伺服器和實例配置檔案。 要瞭解有關不同部署的詳細資訊，請參閱 [托管模型](../../installation/using/hosting-models.md) 或 [此頁](../../installation/using/capability-matrix.md)。

## 概覽 {#overview}

SpamAssassin是一款用於過濾不期望的電子郵件的軟體。 與此軟體配合使用，Adobe Campaign可以為電子郵件分配分數，並確定在發送前是否可能認為不受歡迎。 為此，必須在Adobe Campaign的應用伺服器上安裝並配置SpamAssassin，並且需要一定數量的附加Perl模組才能運行。

本章中所述的SpamAssassin的部署和整合基於預設軟體安裝，過濾和評分規則也基於預設軟體安裝，這些規則是SpamAssassin提供的，不進行任何更改或優化。 評分屬性和消息限定僅基於SpamAssasin選項的配置和過濾規則。 網路管理員負責使他們適應公司的需求。

>[!IMPORTANT]
>
>SpamAssassin對電子郵件的不受歡迎程度的認定完全基於過濾和評分規則。
>
>因此，必須每天至少更新這些規則一次，以便SpamAssassin的安裝及其與Adobe Campaign的整合能夠充分發揮作用，並確保在發送前分配給您交貨的分數的相關性。
>
>此更新由托管SpamAssassin的伺服器管理員負責。

使用Adobe Campaign的SpamAssassin提供使用SpamAssassin的郵件伺服器在接收Adobe Campaign發送的電子郵件時的可能行為。 但是，網際網路提供商的郵件伺服器或線上郵件伺服器可能仍然認為Adobe Campaign發送的郵件不受歡迎。

在Perl中部署SpamAssassin及其模組要求Adobe Campaign應用程式伺服器通過HTTP連接（TCP/80流）進行Internet訪問。

## 在Windows電腦上安裝 {#installing-on-a-windows-machine}

要在Windows上安裝和配置SpamAssassin以啟用與Adobe Campaign的整合，請應用以下步驟：

1. 安裝SpamAssassin
1. 將SpamAssassin整合到Adobe Campaign

### 安裝SpamAssassin {#installing-spamassassin}

1. 連接到 [軟體分發門戶](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) 使用用戶憑據。 瞭解有關中軟體分發的詳細資訊 [此頁](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant)。
1. 下載 **Neolane Spam Assassin（Windows安裝）(2.0)** 檔案(neolane_spamassassin.2.0.zip)。
1. 將此檔案複製到Adobe Campaign伺服器，然後解壓。

   >[!NOTE]
   >
   >只要路徑由下列任意規則運算式字元組成，則可以選擇解壓縮檔案： **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**。 安裝路徑不能包含任何空格字元。

1. 轉到已解壓檔案的檔案，然後按兩下 **run_me_bat** 檔案啟動安裝指令碼。

   如果出現Windows Shell並繼續顯示幾秒鐘，請等待安裝和更新完成，然後按一下 **輸入**。

   如果Windows Shell在立即消失之前未顯示或未顯示，請執行以下步驟，按兩下 **攜帶型Shell.bat** 檔案以顯示Windows Shell並檢查Shell路徑是否與 **spamassin.zip** 檔案已解壓縮。 如果不是，請使用 **cd** 的子菜單。

   輸入 **run_me_bat** 按一下 **輸入** 啟動安裝和更新過程。 該操作返回以下值之一以指示更新結果。

   * **0**:已執行更新。
   * **1**:沒有新的更新可用。
   * **2**:沒有新的更新可用。
   * **3**:更新在先前驗證期間失敗。
   * **4** 或更多：發生錯誤。

1. 要檢查SpamAssassin安裝是否成功，請使用GTUBEtest(未經請求的批量電子郵件的通用Test)，按下列步驟操作：

   1. 建立文本檔案並將其保存在 **C:\TestSpamMail.txt**。
   1. 將以下內容插入檔案：

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

   1. 按兩下 **攜帶型Shell.bat** 檔案以顯示Windows Shell，然後啟動以下命令(或「`<root>`&#39;&#39;在解壓縮時指定建立的資料夾  **spamassin.zip** 檔案):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      此test電子郵件的內容觸發SpamAssassin的1,000分。 這表示已檢測到不需要安裝，並且安裝已成功並且完全正常。

### 將SpamAssassin整合到Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. 編輯 **`[INSTALL]/conf/serverConf.xml`** 的子菜單。 中的所有可用參數 **serverConf.xml** 列在 [節](../../installation/using/the-server-configuration-file.md)。
1. 更改 **垃圾郵件檢查** 元素 **命令** 屬性 **Web** 的下界。 為此，請運行以下命令：

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >所有路徑都必須是絕對路徑。

   停止並啟動 **[!UICONTROL Adobe Campaign]** 服務。

1. 要檢查SpamAssassin在Adobe Campaign的整合，請使用GTBUEtest(非請求批量電子郵件的通用Test):

   按兩下 **波塔貝地獄** 的子菜單。 這將觸發Windows Shell的顯示。 然後運行以下命令：

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   此test電子郵件的內容觸發了SpamAssassin分配的1,000點。 這意味著它被認為是不可取的，在Adobe Campaign的整合是成功的，並且是完全有效的。

1. 更新SpamAssassin篩選和評分規則

   要初始更新篩選和計分規則，請開始 **攜帶型Shell.bat** 並運行以下命令：

   ```
   sa-update --no-gpg
   ```

   要運行篩選規則和計分規則的自動更新，請在計畫的系統任務中使用此命令：

   ```
   sa-update --no-gpg
   ```

## 在Linux電腦上安裝 {#installing-on-a-linux-machine}

### Debian中的安裝步驟 {#installation-steps-in-debian}

* 如有必要，請使用以下命令安裝Perl和SpamAssassin:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* 在 **serverConf.xml** 檔案（可用） `/usr/local/[INSTALL]/nl6/conf/`)，更改 **垃圾郵件檢查** 行：

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### RHEL/CentOS中的安裝步驟 {#installation-steps-in-rhel-centos}

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

### 更新篩選器規則 {#updating-filter-rules}

可以使用 **sa更新** 工具欄。 請參閱官方的SpamAssassin網站 [https://spamassassin.apache.org/](https://spamassassin.apache.org/) 的子菜單。

在Debian中，更新每天都自動進行。

如果不是這樣（例如，手動安裝Debian時），請建立指令碼以自動更新規則。

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

將此指令碼插入 **crontab** 使用以下命令：

```
crontab-e
```

### 效能優化 {#performance-optimization}

要提高Linux的效能，請編輯 **/etc/spamassassin/local.cf** 檔案，並在檔案末尾添加以下行：

```
dns_available no
```
