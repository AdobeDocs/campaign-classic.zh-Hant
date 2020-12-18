---
solution: Campaign Classic
product: campaign
title: 篩選規則
description: 篩選規則
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 2%

---


# 篩選規則{#filtering-rules}

篩選規則可讓您根據在查詢中定義的准則定義要排除的訊息。 這些規則會連結至定位維度。

篩選規則可連結至其他類型的規則（控制項、壓力等） 排版，或分組為專屬&#x200B;**篩選**&#x200B;排版。 有關詳細資訊，請參閱[建立和使用過濾類型學](#creating-and-using-a-filtering-typology)。

## 建立篩選規則{#creating-a-filtering-rule}

例如，您可以篩選電子報訂閱者，以防止將通訊傳送給未成年的收件者。

若要定義此篩選，請套用下列步驟：

1. 建立適用於所有通訊管道的&#x200B;**[!UICONTROL Filtering]**&#x200B;類型規則。

   ![](assets/campaign_opt_create_filter_01.png)

1. 更改預設目標維並選擇預訂(**nms:subscription**)。

   ![](assets/campaign_opt_create_filter_02.png)

1. 使用&#x200B;**[!UICONTROL Edit the query from the targeting dimension...]**&#x200B;連結建立篩選。

   ![](assets/campaign_opt_create_filter_03.png)

1. 將此規則連結至促銷活動類型學，並加以儲存。

   ![](assets/campaign_opt_create_filter_04.png)

當此規則用於傳送時，未成年訂閱者會自動排除。 特定消息表示規則應用程式：

![](assets/campaign_opt_create_filter_05.png)

## 調整篩選規則{#conditioning-a-filtering-rule}

您可以根據連結的傳送或傳送大綱來限制篩選規則的應用程式欄位。

若要這麼做，請前往排版規則的&#x200B;**[!UICONTROL General]**&#x200B;標籤，選取要套用的限制類型並建立篩選，如下所示：

![](assets/campaign_opt_create_filter_06.png)

在此情況下，即使規則已連結至所有傳送，也只會套用至符合已定義篩選條件的傳送。

>[!NOTE]
>
>在工作流程中，**[!UICONTROL Delivery outline]**&#x200B;活動中可以使用類型和篩選規則。 如需詳細資訊，請參閱[本章節](../../workflow/using/delivery-outline.md)。

## 建立和使用過濾類型學{#creating-and-using-a-filtering-typology}

您可以建立&#x200B;**[!UICONTROL Filtering]**&#x200B;類型：它們只包含篩選規則。

![](assets/campaign_opt_create_typo_filtering.png)

選取目標時，這些特定類型可以連結至傳送：在傳送精靈中，按一下&#x200B;**[!UICONTROL To]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Exclusions]**&#x200B;標籤。

![](assets/campaign_opt_apply_typo_filtering.png)

然後選取要套用至傳送的篩選類型學。 要執行此操作，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並選擇要應用的類型。

您也可以透過此索引標籤直接連結篩選規則，而不將規則分組至類型。 若要這麼做，請使用視窗的下方區段。

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>選擇窗口中只提供類型和過濾規則。
>
>這些設定可在傳送範本中定義，以便自動套用至使用範本建立的所有新傳送。


## 預設可傳遞性排除規則{#default-deliverability-exclusion-rules}

預設提供兩個篩選規則：**[!UICONTROL Exclude addresses]**(**[!UICONTROL addressExclusions]**)和&#x200B;**[!UICONTROL Exclude domains]**(**[!UICONTROL domainExclusions]**)。 在電子郵件分析期間，這些規則會比較收件者電子郵件地址與傳送能力例項中管理之加密全域隱藏清單中所包含之禁止地址或網域名稱。 如果有相符項目，則不會傳送訊息給該收件者。

這是為了避免由於惡意活動（尤其是使用Spamtrap）而被添加到密鑰清單中。 例如，如果使用Spamtrap來透過您的其中一個Web表單進行訂閱，系統會自動傳送確認電子郵件給該Spamtrap，這會導致您的位址自動新增至密文清單。

>[!NOTE]
>
>全局隱藏清單中包含的地址和域名將被隱藏。 傳送分析記錄中只會指出已排除的收件者數目。

