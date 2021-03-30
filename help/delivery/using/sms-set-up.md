---
solution: Campaign Classic
product: campaign
title: 設定促銷活動SMS頻道
description: 瞭解如何在Campaign中設定SMS頻道
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 64f5b108173806aff53f7240e8c9d499cc332d72
workflow-type: tm+mt
source-wordcount: '1679'
ht-degree: 34%

---


# 設定SMS通道{#setting-up-sms-channel}

若要傳送至行動電話，您需要：

1. 指定連接器和消息類型的外部帳戶。

   請注意，舊式連接器現已過時。 淘汰的功能仍然可用，但將不會進一步增強，也不支援。 在本頁瞭解更多[的資訊。](../../rn/using/deprecated-features.md)

1. 參考此外部帳戶的傳送範本。

## 建立SMPP外部帳戶{#creating-an-smpp-external-account}

若要將SMS傳送至行動電話，您首先需要建立SMPP外部帳戶。
有關SMS協定和設定的詳細資訊，請參閱此[頁](../../delivery/using/sms-protocol.md)。

要執行此操作，請遵循下列步驟：

1. 在樹的&#x200B;**[!UICONTROL Platform]** > **[!UICONTROL External accounts]**&#x200B;節點中，按一下&#x200B;**[!UICONTROL New]**&#x200B;表徵圖。
1. 將帳戶類型定義為&#x200B;**路由**，渠道定義為&#x200B;**移動(SMS)**，傳送模式定義為&#x200B;**批量傳送**。

   ![](assets/extended_smpp_create_account.png)

1. 選中&#x200B;**[!UICONTROL Enabled]**&#x200B;框。
1. 在&#x200B;**[!UICONTROL Mobile]**&#x200B;標籤中，從&#x200B;**[!UICONTROL Connector]**&#x200B;下拉式清單中選擇&#x200B;**[!UICONTROL Extended generic SMPP]**。

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > 從20.2版開始，舊版連接器已過時且不受支援。 建議使用&#x200B;**[!UICONTROL Extended generic SMPP]**&#x200B;連接器。 有關如何遷移到建議連接器的詳細資訊，請參閱此[頁](../../delivery/using/unsupported-connector-migration.md)。

1. **[!UICONTROL Enable verbose SMPP traces in the log file]**&#x200B;選項允許您將所有SMPP通信轉儲到日誌檔案中。 必須啟用此選項，才能疑難排解連接器，並與提供者所看到的流量進行比較。

1. 請連絡您的SMS服務供應商，該服務提供商將向您解釋如何從&#x200B;**[!UICONTROL Connection settings]**&#x200B;頁籤填寫不同的外部帳戶欄位。

   然後，請根據您選擇的供應商，與您聯繫，由誰為您提供輸入&#x200B;**[!UICONTROL SMSC implementation name]**&#x200B;欄位的值。

   您可以定義每個MTA子代與提供者的連線數。 依預設，會設為1。

1. 根據預設，SMS中的字元數量符合GSM標準。

   使用 GSM 編碼的 SMS 訊息最多只能有 160 個字元，若是以多個部分傳送的訊息，則每個 SMS 的 SMS 訊息最多只能有 153 個字元。

   >[!NOTE]
   >
   >某些字元會計為兩個字元（括弧、方括弧、歐元符號等）。
   >
   >以下列出可用的GSM字元。

   您也可以核取相對應的方塊，以授權字元音譯。

   ![](assets/extended_smpp_transliteration.png)

   如需詳細資訊，請參閱[本章節](#about-character-transliteration)。

1. 在&#x200B;**[!UICONTROL Throughput and delays]**&#x200B;頁籤中，可以指定每秒MT的出站消息（「MT」,「已終止移動」）的最大吞吐量。 如果您在對應欄位中輸入　&quot;0&quot;，則吞吐量將無限制。

   與持續時間對應的所有欄位的值需要以秒為單位完成。

1. 在&#x200B;**[!UICONTROL Mapping of encodings]**&#x200B;標籤中，您可以定義編碼。

   如需詳細資訊，請參閱[本章節](#about-text-encodings)。

1. 在&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;標籤中，**[!UICONTROL Send full phone number]**&#x200B;選項預設為停用。 如果要遵守SMPP協定並僅將數字傳輸到SMS提供器(SMSC)的伺服器，請不要啟用它。

   但是，由於某些提供者需要使用&#39;+&#39;首碼，建議您與提供者確認，並建議您視需要啟用此選項。

   使用&#x200B;**[!UICONTROL Enable TLS over SMPP]**&#x200B;複選框可以加密SMPP通信。 如需關於此項目的詳細資訊，請參閱此[頁面](../../delivery/using/sms-protocol.md)。

1. 如果您要設定&#x200B;**[!UICONTROL Extended generic SMPP]**&#x200B;連接器，則可以設定自動回覆。

   如需詳細資訊，請參閱[本章節](#automatic-reply)。

## SMS字母音譯{#about-character-transliteration}

字母音譯可在SMPP行動傳送外部帳戶中設定，位於&#x200B;**[!UICONTROL Mobile]**&#x200B;標籤下。

音譯包括當 GSM 標準未考慮到 SMS 的一個字元時，用另一個字元取代該字元。

* 如果音譯是&#x200B;**[!UICONTROL authorized]**，則在傳送訊息時，未考慮的每個字元都會由GSM字元取代。 例如，字元 &quot;ë&quot; 會由 &quot;e&quot; 取代。因此，訊息會稍微變更，但字元限制將維持不變。
* 當音譯為&#x200B;**[!UICONTROL not authorized]**&#x200B;時，每個包含未納入考量的字元的訊息都會以二進位格式(Unicode)傳送：因此，所有字元都將按原樣發送。 不過，使用 Unicode 的 SMS 訊息最多只能有 70 個字元（若是以多個部分傳送的訊息，則每個 SMS 有 67 個字元）。如果超出字元數上限，則會傳送數則訊息，這可能會造成額外成本。

>[!IMPORTANT]
>
>將個人化欄位插入您的 SMS 訊息內容，可能會引入 GSM 編碼未考慮的字元。

依預設，會停用字元音譯。如果您希望 SMS 訊息中的所有字元都保持原樣，不要變更正確名稱（例如），建議您不要啟用此選項。

不過，如果您的 SMS 訊息包含許多產生 Unicode 訊息的字元，您可以選取啟用此選項，以限制傳送訊息的成本。

下表列出GSM標準所考慮的字元。 除下面提及的字元外，所有插入訊息內文的字元都會將整個訊息轉換為二進位格式 (Unicode)，因此限制為 70 個字元。

**基本字元**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> 「 </td> 
   <td> P </td> 
   <td> 。 </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> 英鎊 </td> 
   <td> _ </td> 
   <td> ! </td> 
   <td> 1 </td> 
   <td> A </td> 
   <td> Q </td> 
   <td> a </td> 
   <td> q </td> 
  </tr> 
  <tr> 
   <td> $ </td> 
   <td> <img height="21px" src="assets/phi.png" /> </td> 
   <td> 」 </td> 
   <td> 2 </td> 
   <td> B </td> 
   <td> R </td> 
   <td> b </td> 
   <td> r </td> 
  </tr> 
  <tr> 
   <td> ¥ </td> 
   <td> <img height="21px" src="assets/gamma.png" /> </td> 
   <td> # </td> 
   <td> 3 </td> 
   <td> C </td> 
   <td> S </td> 
   <td> c </td> 
   <td> s </td> 
  </tr> 
  <tr> 
   <td> è </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> ∮ </td> 
   <td> 4 </td> 
   <td> D </td> 
   <td> T </td> 
   <td> d </td> 
   <td> t </td> 
  </tr> 
  <tr> 
   <td> é </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> ù </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> ì </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> ò </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> Ç </td> 
   <td> <img height="21px" src="assets/theta.png" /> </td> 
   <td> ） </td> 
   <td> 9 </td> 
   <td> I </td> 
   <td> Y </td> 
   <td> i </td> 
   <td> y </td> 
  </tr> 
  <tr> 
   <td> LF </td> 
   <td> <img height="21px" src="assets/xi.png" /> </td> 
   <td> * </td> 
   <td> : </td> 
   <td> J </td> 
   <td> Z </td> 
   <td> j </td> 
   <td> z </td> 
  </tr> 
  <tr> 
   <td> Ø </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ä </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> ø </td> 
   <td> Æ </td> 
   <td> 的 </td> 
   <td> &lt;&gt; </td> 
   <td> L </td> 
   <td> Ö </td> 
   <td> l </td> 
   <td> ö </td> 
  </tr> 
  <tr> 
   <td> CR </td> 
   <td> æ </td> 
   <td> - </td> 
   <td> = </td> 
   <td> M </td> 
   <td> Ñ </td> 
   <td> m </td> 
   <td> ñ </td> 
  </tr> 
  <tr> 
   <td> Å </td> 
   <td> ß </td> 
   <td> . </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> Ü </td> 
   <td> n </td> 
   <td> ü </td> 
  </tr> 
  <tr> 
   <td> å </td> 
   <td> É </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> à </td> 
  </tr> 
 </tbody> 
</table>

SP：Space

ESC：Escape

LF：換行

CR：歸位

**進階字元（計算兩次）**

^ { } `[ ~ ]` |€

## 關於文字編碼{#about-text-encodings}

傳送 SMS 訊息時，Adobe Campaign 可以使用一或多種文字編碼。每個編碼都有其專屬的字元集，並決定符合 SMS 訊息的字元數。

在配置新的SMPP移動傳送外部帳戶時，您可以在&#x200B;**[!UICONTROL Mobile]**&#x200B;標籤中定義&#x200B;**[!UICONTROL Mapping of encodings]**:**[!UICONTROL data_coding]**&#x200B;欄位可讓Adobe Campaign通訊SMSC使用哪種編碼。

>[!NOTE]
>
>**data_coding** 值及實際使用編碼之間的對應是標準化的。然而，某些SMSC有其自己的具體對應：在這種情況下，您的&#x200B;**Adobe Campaign**&#x200B;管理員需要聲明此映射。 請洽詢您的提供者以瞭解更多資訊。

您可以宣告&#x200B;**data_codings**，並視需要強制編碼：若要這麼做，請在表格中指定單一編碼。

* 當未定義編碼的映射時，連接器會採取一般行為：

   * 它會嘗試使用 GSM 編碼，將 **data_coding = 0** 的值指派給它。
   * 如果 GSM 編碼失敗，則會使用 **UCS2** 編碼，並對其指派值 **data_coding = 8**。

* 當您定義要使用的編碼以及連結的&#x200B;**[!UICONTROL data_coding]**&#x200B;欄位值時，Adobe Campaign會嘗試使用清單中的第一個編碼，如果第一個編碼不可能，則下列。

>[!IMPORTANT]
>
>宣告的順序非常重要：建議您以&#x200B;**成本**&#x200B;的遞增順序顯示清單，以利於編碼，讓您在每則 SMS 訊息中盡可能多地顯示字元。
>
>僅宣告您要使用的編碼。如果SMSC提供的某些編碼不符合您的使用目的，請勿在清單中宣告。

## 自動回覆{#automatic-reply}

在設定擴展的通用SMPP連接器時，可以配置自動回覆。

當訂閱者回覆透過Adobe Campaign傳送給他們的SMS訊息，且其訊息包含關鍵字（例如「STOP」）時，您可在&#x200B;**[!UICONTROL Automatic reply sent to the MO]**&#x200B;區段中設定自動傳回給他們的訊息。

>[!NOTE]
>
>關鍵字不區分大小寫。

對於每個關鍵字，請指定一個簡短代碼，此代碼通常用於發送傳送，並用作發送者名稱，然後輸入要發送給訂閱者的消息。

您也可以將動作連結至自動回應：**[!UICONTROL Send to quarantine]**&#x200B;或&#x200B;**[!UICONTROL Remove from quarantine]**。 例如，如果收件者傳送關鍵字&quot;STOP&quot;，他們會自動收到取消訂閱的確認，並傳送至隔離。

![](assets/extended_smpp_reply.png)

如果您將&#x200B;**[!UICONTROL Remove from quarantine]**&#x200B;動作連結至自動回應，傳送對應關鍵字的收件者會自動從隔離中移除。

**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**&#x200B;功能表提供的&#x200B;**[!UICONTROL Non deliverables and addresses]**&#x200B;表中列出了收件者。

* 若要傳送相同的回覆，不論是短程式碼，請將&#x200B;**[!UICONTROL Short code]**&#x200B;欄留空。
* 若要傳送相同的回覆，不論關鍵字為何，請將&#x200B;**[!UICONTROL Keyword]**&#x200B;欄留空。
* 要執行不發送響應的操作，請將&#x200B;**[!UICONTROL Response]**&#x200B;列保留為空。 例如，這可讓您從隔離使用「STOP」以外訊息回覆的使用者移除。

如果您使用具有相同提供者帳戶的擴充通用SMPP連接器，有多個外部帳戶，可能會發生下列問題：當傳送回覆至簡短程式碼時，可能會在您的任何外部帳戶連線上收到回覆。 因此，所發送的自動回覆不能是預期訊息。
若要避免此情況，請根據您使用的提供者，套用下列其中一個解決方案：

* 為每個外部帳戶建立一個提供程式帳戶。
* 使用&#x200B;**[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]**&#x200B;標籤中的&#x200B;**[!UICONTROL System type]**&#x200B;欄位來區分每個簡短代碼。 請向您的供應商洽詢每個帳戶的不同值。

   ![](assets/extended_smpp_system-type.png)

使用擴展通用SMPP連接器設定外部帳戶的步驟在[建立SMPP外部帳戶](#creating-an-smpp-external-account)部分中有詳細說明。

## 變更傳送範本{#changing-the-delivery-template}

Adobe Campaign為您提供傳送至行動裝置的範本。 此模板在&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;節點中可用。 有關詳細資訊，請參閱[關於templates](../../delivery/using/about-templates.md)部分。

若要透過SMS頻道傳送，您必須建立參考頻道連接器的範本。

為了保留原生傳送範本，建議您先複製範本，然後加以設定。

在以下範例中，我們建立範本，以透過先前啟用的SMPP帳戶傳送訊息。 操作步驟：

1. 轉至&#x200B;**[!UICONTROL Delivery templates]**&#x200B;節點。
1. 按一下右鍵&#x200B;**[!UICONTROL Send to mobiles]**&#x200B;模板，然後選擇&#x200B;**[!UICONTROL Duplicate]**。

   ![](assets/s_user_mobile_template_change_01.png)

1. 變更範本的標籤，例如&#x200B;**傳送至行動裝置(SMPP)**。

   ![](assets/s_user_mobile_template_change_02.png)

1. 按一下 **[!UICONTROL Properties]**。
1. 在&#x200B;**[!UICONTROL General]**&#x200B;標籤中，選擇與您在前面步驟中建立的外部帳戶相對應的路由模式。

   ![](assets/s_user_mobile_template_change_03.png)

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;以建立範本。

   ![](assets/s_user_mobile_template_list.png)

您現在擁有外部帳戶和傳送範本，可讓您透過SMS傳送。
