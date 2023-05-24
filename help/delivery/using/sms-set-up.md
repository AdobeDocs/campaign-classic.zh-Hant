---
product: campaign
title: 設定Campaign簡訊頻道
description: 瞭解如何在Campaign中設定簡訊頻道
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: SMS
exl-id: a2783a5e-6d38-41a1-b5c6-24ab489116f8
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1722'
ht-degree: 34%

---

# 設定簡訊頻道 {#setting-up-sms-channel}



若要傳送至行動電話，您需要：

1. 指定聯結器和訊息型別的外部帳戶。

   請注意，舊版聯結器現已棄用。 已棄用的功能仍可使用，但將不會進一步增強或支援。 在[本頁](../../rn/using/deprecated-features.md)中深入瞭解。

1. 引用此外部帳戶的傳遞範本。

>[!NOTE]
>
> 針對SMS傳遞，型別應使用中建立的特定SMS相似性 **一** 專用應用程式伺服器容器。 [了解更多](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

## 建立SMPP外部帳戶 {#creating-an-smpp-external-account}

>[!IMPORTANT]
>
>對多個外部SMS帳戶使用相同的帳戶和密碼可能會導致帳戶之間的衝突和重疊。 請參閱 [簡訊疑難排解頁面](troubleshooting-sms.md#external-account-conflict).

若要將SMS傳送至行動電話，您首先需要建立SMPP外部帳戶。
有關SMS通訊協定和設定的詳細資訊，請參閱此 [頁面](sms-protocol.md).

要執行此操作，請遵循下列步驟：

1. 在 **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** 樹狀結構節點，按一下 **[!UICONTROL New]** 圖示。
1. 將帳戶型別定義為 **路由**，頻道為 **行動裝置（簡訊）**，而傳送模式為 **大量傳遞**.

   ![](assets/extended_smpp_create_account.png)

1. 檢查 **[!UICONTROL Enabled]** 方塊。
1. 在 **[!UICONTROL Mobile]** 索引標籤，選取 **[!UICONTROL Extended generic SMPP]** 從 **[!UICONTROL Connector]** 下拉式清單。

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > 自版本20.2起，舊版聯結器已棄用且不受支援。 我們建議使用 **[!UICONTROL Extended generic SMPP]** 聯結器。 有關如何遷移至建議聯結器的詳細資訊，請參閱此 [頁面](unsupported-connector-migration.md).

1. 此 **[!UICONTROL Enable verbose SMPP traces in the log file]** 選項可讓您將所有SMPP流量傾印到記錄檔案中。 必須啟用此選項，才能疑難排解連接器，並與提供者所看到的流量進行比較。

1. 請聯絡您的SMS服務提供者，他們會向您說明如何填寫以下欄位的不同外部帳戶： **[!UICONTROL Connection settings]** 標籤。

   然後，請根據所選供應商聯絡您的提供者，他們會為您提供要輸入到 **[!UICONTROL SMSC implementation name]** 欄位。

   您可以定義每個MTA子系與提供者的連線數目。 預設會設為1。

1. 根據預設，SMS中的字元數符合GSM標準。

   使用 GSM 編碼的 SMS 訊息最多只能有 160 個字元，若是以多個部分傳送的訊息，則每個 SMS 的 SMS 訊息最多只能有 153 個字元。

   >[!NOTE]
   >
   >某些字元會計為兩個字元（括弧、方括弧、歐元符號等）。
   >
   >可用GSM字元的清單如下所示。

   您也可以核取相對應的方塊，以授權字元音譯。

   ![](assets/extended_smpp_transliteration.png)

   如需詳細資訊，請參閱[本章節](#about-character-transliteration)。

1. 在 **[!UICONTROL Throughput and delays]** 索引標籤中，您可以指定輸出訊息（「MT」，行動裝置已終止）的最大輸送量（以每秒MT為單位）。 如果您在對應欄位中輸入　&quot;0&quot;，則吞吐量將無限制。

   與持續時間對應的所有欄位的值需要以秒為單位完成。

1. 在 **[!UICONTROL Mapping of encodings]** 標籤，您可以定義編碼。

   如需詳細資訊，請參閱[本章節](#about-text-encodings)。

1. 在 **[!UICONTROL SMSC specificities]** 標籤， **[!UICONTROL Send full phone number]** 選項預設為停用。 如果您想遵守SMPP通訊協定，並且只將數位傳輸到SMS提供者(SMSC)的伺服器，請勿啟用它。

   不過，由於某些提供者需要使用「+」首碼，因此建議您向提供者查詢，並建議您視需要啟用此選項。

   此 **[!UICONTROL Enable TLS over SMPP]** 核取方塊可讓您加密SMPP流量。 如需關於此項目的詳細資訊，請參閱此[頁面](sms-protocol.md)。

1. 如果您要設定 **[!UICONTROL Extended generic SMPP]** connector時，您可以設定自動回覆。

   如需詳細資訊，請參閱[本章節](#automatic-reply)。

## 簡訊字母音譯 {#about-character-transliteration}

字母音譯可在SMPP行動傳遞外部帳戶中設定，位於 **[!UICONTROL Mobile]** 標籤。

音譯包括當 GSM 標準未考慮到 SMS 的一個字元時，用另一個字元取代該字元。

* 如果音譯為 **[!UICONTROL authorized]**，則在傳送訊息時，未考慮的每個字元會由GSM字元取代。 例如，字元 &quot;ë&quot; 會由 &quot;e&quot; 取代。因此，訊息會稍微變更，但字元限制將維持不變。
* 音譯為時 **[!UICONTROL not authorized]**，包含未納入考量之字元的每則訊息都會以二進位格式(Unicode)傳送：因此，所有字元都會照原樣傳送。 不過，使用 Unicode 的 SMS 訊息最多只能有 70 個字元（若是以多個部分傳送的訊息，則每個 SMS 有 67 個字元）。如果超出字元數上限，則會傳送數則訊息，這可能會造成額外成本。

>[!IMPORTANT]
>
>將個人化欄位插入您的 SMS 訊息內容，可能會引入 GSM 編碼未考慮的字元。

依預設，會停用字元音譯。如果您希望 SMS 訊息中的所有字元都保持原樣，不要變更正確名稱（例如），建議您不要啟用此選項。

不過，如果您的 SMS 訊息包含許多產生 Unicode 訊息的字元，您可以選取啟用此選項，以限制傳送訊息的成本。

下表顯示GSM標準所考慮的字元。 除下面提及的字元外，所有插入訊息內文的字元都會將整個訊息轉換為二進位格式 (Unicode)，因此限制為 70 個字元。

**基本字元**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> ¡ </td> 
   <td> P </td> 
   <td> ¿ </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
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
   <td> ¤ </td> 
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
   <td> ) </td> 
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
   <td> , </td> 
   <td> &lt; </td> 
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
   <td>  嗎? </td> 
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

^ { } `[ ~ ]` | €

## 文字編碼 {#about-text-encodings}

傳送 SMS 訊息時，Adobe Campaign 可以使用一或多種文字編碼。每個編碼都有其專屬的字元集，並決定符合 SMS 訊息的字元數。

設定新的SMPP行動傳遞外部帳戶時，您可以定義 **[!UICONTROL Mapping of encodings]** 在 **[!UICONTROL Mobile]** 標籤： **[!UICONTROL data_coding]** 欄位可讓Adobe Campaign通訊要對SMSC使用哪種編碼。

>[!NOTE]
>
>**data_coding** 值及實際使用編碼之間的對應是標準化的。然而，某些SMSC有他們自己的特定對應：在這種情況下，您的 **Adobe Campaign** 管理員需要宣告此對應。 請洽詢您的提供者以瞭解更多資訊。

您可以宣告 **data_codings** 和會視需要強制編碼：若要這麼做，請在表格中指定單一編碼。

* 未定義任何編碼對應時，聯結器會採取一般行為：

   * 它會嘗試使用 GSM 編碼，將 **data_coding = 0** 的值指派給它。
   * 如果 GSM 編碼失敗，則會使用 **UCS2** 編碼，並對其指派值 **data_coding = 8**。

* 定義要使用的編碼以及連結的編碼時 **[!UICONTROL data_coding]** 欄位值，Adobe Campaign會嘗試使用清單中的第一種編碼，如果第一種編碼被證實無法使用，則會進行後續操作。

>[!IMPORTANT]
>
>宣告的順序非常重要：建議您以&#x200B;**成本**&#x200B;的遞增順序顯示清單，以利於編碼，讓您在每則 SMS 訊息中盡可能多地顯示字元。
>
>僅宣告您要使用的編碼。如果SMSC提供的某些編碼不符合您的使用目的，請勿在清單中宣告。

## 自動回覆 {#automatic-reply}

設定延伸通用SMPP聯結器時，您可以設定自動回覆。

當訂閱者回覆透過Adobe Campaign傳送給他們的簡訊訊息，且訊息包含「STOP」之類的關鍵字時，您可以設定訊息，這些訊息會在以下位置自動傳回給他們： **[!UICONTROL Automatic reply sent to the MO]** 區段。

>[!NOTE]
>
>關鍵字不區分大小寫。

請為每個關鍵字指定簡短代碼，這是通常用於傳送傳遞內容並做為寄件者名稱的數字，然後輸入將傳送給訂閱者的訊息。

您也可以將動作連結至自動回應： **[!UICONTROL Send to quarantine]** 或 **[!UICONTROL Remove from quarantine]**. 例如，如果收件者傳送關鍵字「STOP」，則會自動收到取消訂閱確認並傳送至隔離區。

![](assets/extended_smpp_reply.png)

如果您連結 **[!UICONTROL Remove from quarantine]** 自動回應動作，傳送對應關鍵字的收件者會自動從隔離中移除。

收件者會列於 **[!UICONTROL Non deliverables and addresses]** 表格可透過 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** 功能表。

* 若要無論簡碼為何，都傳送相同的回覆，請將 **[!UICONTROL Short code]** 欄空白。
* 若要無論關鍵字為何，都傳送相同的回覆，請將 **[!UICONTROL Keyword]** 欄空白。
* 若要在不傳送回應的情況下執行動作，請將 **[!UICONTROL Response]** 欄空白。 例如，這可讓您從隔離區中移除回複訊息不是「STOP」的使用者。

如果您有多個外部帳戶使用Extended generic SMPP聯結器且提供者帳戶相同，則可能會發生以下問題：當傳送回復到短程式碼時，您的任何外部帳戶連線可能會收到該回覆。 因此，傳送的自動回覆不能是預期的訊息。
為避免此問題，請根據您使用的提供者，套用下列解決方案之一：

* 為每個外部帳戶建立一個提供者帳戶。
* 使用 **[!UICONTROL System type]** 欄位來自 **[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]** 標籤來區分每個簡短代碼。 請向您的提供者詢問每個帳戶的不同值。

   ![](assets/extended_smpp_system-type.png)

有關使用Extended generic SMPP聯結器設定外部帳戶的詳細步驟，請參見 [建立SMPP外部帳戶](#creating-an-smpp-external-account) 區段。

## 變更傳遞範本 {#changing-the-delivery-template}

Adobe Campaign提供您傳送至行動裝置的範本。 此範本可在 **[!UICONTROL Resources > Templates > Delivery templates]** 節點。 如需詳細資訊，請參閱 [關於範本](about-templates.md) 區段。

若要透過SMS頻道傳送，您必須建立其中引用頻道聯結器的範本。

若要保留原生傳遞範本，建議您複製並加以設定。

在以下範例中，我們會建立範本，透過先前啟用的SMPP帳戶傳遞訊息。 操作步驟：

1. 前往 **[!UICONTROL Delivery templates]** 節點。
1. 以滑鼠右鍵按一下 **[!UICONTROL Send to mobiles]** 範本，並選取 **[!UICONTROL Duplicate]**.

   ![](assets/s_user_mobile_template_change_01.png)

1. 變更範本的標籤，例如 **傳送至行動裝置(SMPP)**.

   ![](assets/s_user_mobile_template_change_02.png)

1. 按一下&#x200B;**[!UICONTROL Properties]**。
1. 在 **[!UICONTROL General]** 標籤中，選取與您在前一步驟中建立的外部帳戶對應的製程模式。

   ![](assets/s_user_mobile_template_change_03.png)

1. 按一下 **[!UICONTROL Save]** 以建立範本。

   ![](assets/s_user_mobile_template_list.png)

您現在擁有外部帳戶和傳遞範本，可讓您透過SMS傳遞。
