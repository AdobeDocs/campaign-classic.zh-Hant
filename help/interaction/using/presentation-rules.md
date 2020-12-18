---
solution: Campaign Classic
product: campaign
title: 簡報規則
description: 簡報規則
audience: interaction
content-type: reference
topic-tags: case-study
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 1%

---


# 簡報規則{#presentation-rules}

## 建立演示規則{#creating-a-presentation-rule}

在我們的資料庫中，有幾份旅行優惠，適用於歐洲、非洲、美國和加拿大。 我們想要寄送優惠到加拿大，但如果收件者拒絕此類優惠，我們不想再寄給他們

我們將設定規則，讓每位收件者僅能提供一次加拿大之行，若拒絕，則不再提供。

1. 在Adobe Campaign樹狀結構中，前往&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]**&#x200B;節點。
1. 建立新的&#x200B;**[!UICONTROL Offer presentation]**&#x200B;類型規則。

   ![](assets/offer_typology_example_001.png)

1. 如有必要，請變更其標籤和說明。

   ![](assets/offer_typology_example_002.png)

1. 選擇&#x200B;**[!UICONTROL All channels]**&#x200B;選項，將規則延伸至所有頻道。

   ![](assets/offer_typology_example_003.png)

1. 按一下&#x200B;**[!UICONTROL Edit expression]**&#x200B;連結，然後選擇&#x200B;**[!UICONTROL Category]**&#x200B;節點作為表達式。

   ![](assets/offer_typology_example_004.png)

1. 選擇與您的加拿大旅行優惠相符的類別，然後按一下&#x200B;**[!UICONTROL OK]**&#x200B;以關閉查詢視窗。

   ![](assets/offer_typology_example_005.png)

1. 在&#x200B;**[!UICONTROL Offer presentation]**&#x200B;標籤中，選擇與環境中配置的維相同。

   ![](assets/offer_typology_example_006.png)

1. 指定套用規則的期間。

   ![](assets/offer_typology_example_007.png)

1. 將提案限制在一個，讓已拒絕加拿大之行的收件者不會再收到類似的提案。

   ![](assets/offer_typology_example_008.png)

1. 選擇&#x200B;**[!UICONTROL Offers for the same category]**&#x200B;篩選條件，排除&#x200B;**Canada**&#x200B;類別中的所有選件。

   ![](assets/offer_typology_example_020.png)

1. 選擇&#x200B;**[!UICONTROL Rejected propositions]**&#x200B;篩選器，以僅考慮收件人拒絕的主張。

   ![](assets/offer_typology_example_021.png)

1. 選擇將套用此規則的收件者。

   在我們的示例中，我們將選擇&#x200B;**頻繁旅行者**&#x200B;收件人。

   ![](assets/offer_typology_example_009.png)

1. 在選件類型學中參考規則。

   ![](assets/offer_typology_example_013.png)

1. 前往選件環境（本例中為&#x200B;**環境——收件者**），並參考使用&#x200B;**[!UICONTROL Eligibility]**&#x200B;標籤中下拉式清單剛建立的新類型學。

   ![](assets/offer_typology_example_014.png)

## 應用演示規則{#applying-the-presentation-rule}

以下是先前建立的排版規則的應用程式範例。

我們想傳送屬於加拿大類別的第一個選件提案。 如果選件遭任何收件者拒絕一次，就不會再次提供給他們。

1. 在&#x200B;**Frequent travelers**&#x200B;收件者資料夾中，選擇其中一個描述檔以檢查符合資格的選件：按一下&#x200B;**[!UICONTROL Propositions]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤。

   在我們的範例中，**Tim Ramsey**&#x200B;符合&#x200B;**Americas**&#x200B;類別的選件資格。

   ![](assets/offer_typology_example_015.png)

1. 首先，建立電子郵件傳送，以您的&#x200B;**常旅客**&#x200B;收件者為目標，並提供優惠。
1. 選取選件引擎呼叫參數。

   在我們的範例中，選擇&#x200B;**Travel in America**&#x200B;類別，其中包含&#x200B;**Canada**&#x200B;和&#x200B;**United States**&#x200B;子類別。

   ![](assets/offer_typology_example_016.png)

1. 將選件插入訊息內文並傳送傳送。 有關詳細資訊，請參閱[關於出站通道](../../interaction/using/about-outbound-channels.md)。

   收件者收到符合資格的選件。

1. 如提案歷史所示，收件者拒絕了加拿大提案。

   ![](assets/offer_typology_example_018.png)

1. 檢查目前符合資格的選件。

   我們可以看到加拿大沒有選擇任何優惠。

   ![](assets/offer_typology_example_019.png)

**相關主題**

* [跨通道管理選件和控制冗餘](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Manageoffersandcontrolredundancyacrosschannels)