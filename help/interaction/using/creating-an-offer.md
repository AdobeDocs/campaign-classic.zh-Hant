---
product: campaign
title: 建立優惠方案
description: 建立優惠方案
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: c6dd2709-06e3-4227-bbec-99f3d80144fe
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 2%

---

# 建立優惠方案{#creating-an-offer}

## 建立選件{#creating-the-offer}

若要建立優惠方案，請套用下列步驟：

1. 前往&#x200B;**[!UICONTROL Campaigns]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Offers]**&#x200B;連結。

   ![](assets/offer_create_001.png)

1. 按一下 **[!UICONTROL Create]** 按鈕。

   ![](assets/offer_create_005.png)

1. 變更標籤，並選取選件應屬於的類別。

   ![](assets/offer_create_002.png)

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;以建立選件。

   ![](assets/offer_create_003.png)

   此選件可在平台中使用，且可設定其內容。

   ![](assets/offer_create_004.png)

## 配置優惠方案資格{#configuring-offer-eligibility}

在&#x200B;**[!UICONTROL Eligibility]**&#x200B;索引標籤中，定義選件對有效的期間，以及可以顯示的期間、要套用至目標的篩選器以及選件加權。

### 定義優惠方案的資格期{#defining-the-eligibility-period-of-an-offer}

若要定義優惠方案的資格期間，請使用下拉式清單，並在日曆中選取開始和結束日期。

![](assets/offer_eligibility_create_002.png)

在這些日期以外，互動引擎將不會選取選件。 如果您也已設定優惠方案類別的資格日期，則會套用限制最嚴格的期間。

### 目標{#filters-on-the-target}上的篩選器

您可以將篩選器套用至選件目標。

要執行此操作，請按一下&#x200B;**[!UICONTROL Edit query]**&#x200B;連結並選取要套用的篩選器。 （請參閱[此區段](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)）。

![](assets/offer_eligibility_create_003.png)

如果已建立預先定義的篩選，您可以從使用者篩選清單中選取這些篩選。 有關詳細資訊，請參閱[建立預先定義的篩選器](../../interaction/using/creating-predefined-filters.md)。

![](assets/offer_eligibility_create_004.png)

### 選件權重{#offer-weight}

若要讓引擎在目標符合資格的多個選件之間做出決定，您需要為選件指派一或多個加權。 您也可以視需要將篩選器套用至目標，或限制權數要套用的選件空間。 較重量較輕的優惠方案，更偏好權重較重的優惠方案。

您可以為相同選件設定多個加權，例如區分特定期間、特定目標甚至選件空間。

例如，對於年齡在18到25歲的接觸，選件可以具有A的重量，對於超過該範圍的接觸，可以具有B的重量。 如果優惠方案在整個夏天都符合資格，在7月也可以有A的權重，在8月有B的權重。

>[!NOTE]
>
>您可以根據選件所屬類別的參數來暫時修改指派的加權。 如需詳細資訊，請參閱[建立優惠方案類別](../../interaction/using/creating-offer-categories.md)。

若要在選件中建立權重，請套用下列步驟：

1. 按一下 **[!UICONTROL Add]**。

   ![](assets/offer_weight_create_001.png)

1. 變更標籤並指派權數。 預設為1。

   ![](assets/offer_weight_create_006.png)

   >[!IMPORTANT]
   >
   >如果未輸入權重(0)，則目標將不被視為符合優惠方案的資格。

1. 如果要將權重應用於指定期間，請定義資格日期。

   ![](assets/offer_weight_create_002.png)

1. 如有必要，請限制特定優惠方案空間的權重。

   ![](assets/offer_weight_create_003.png)

1. 將篩選器套用至目標。

   ![](assets/offer_weight_create_004.png)

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;以儲存權重。

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >如果目標符合所選選件的多個加權，引擎會保留最佳（最高）加權。 呼叫優惠方案引擎時，每個連絡最多會選取一次優惠方案。

### 優惠方案適用性規則摘要{#a-summary-of-offer-eligibility-rules}

完成設定後，優惠方案控制面板就會提供資格規則的摘要。

若要檢視，請按一下&#x200B;**[!UICONTROL Schedule and eligibility rules]**&#x200B;連結。

![](assets/offer_eligibility_create_005.png)

## 建立選件內容{#creating-the-offer-content}

1. 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Content]**&#x200B;標籤。

   ![](assets/offer_content_create_001.png)

1. 填妥優惠方案內容的各種欄位。

   * **[!UICONTROL Title]** :指定您要在選件中顯示的標題。警告：這並非指在&#x200B;**[!UICONTROL General]**&#x200B;索引標籤中定義的選件標籤。
   * **[!UICONTROL Destination URL]** :指定您選件的URL。若要正確處理，其開頭必須為「http://」或「https://」。
   * **[!UICONTROL Image URL]** :指定選件影像的URL或存取路徑。
   * **[!UICONTROL HTML content]** /  **[!UICONTROL Text content]** :在您想要的索引標籤中輸入優惠方案的內文。若要產生追蹤，**[!UICONTROL HTML content]**&#x200B;必須由HTML元素組成，這些元素可封閉在`<div>`類型元素中。 例如，HTML頁面中`<table>`元素的結果如下：

   ```
      <div> 
       <table>
        <tr>
         <th>Month</th>
         <th>Savings</th>   
        </tr>   
        <tr>    
         <td>January</td>
         <td>$100</td>   
        </tr> 
       </table> 
      </div>
   ```

   定義接受URL顯示在[設定接受主張時的狀態](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted)區段中。

   ![](assets/offer_content_create_002.png)

   若要尋找在優惠方案空間設定期間所定義的必要欄位，請按一下&#x200B;**[!UICONTROL Content definitions]**&#x200B;連結以顯示清單。 如需詳細資訊，請參閱[建立優惠方案空間](../../interaction/using/creating-offer-spaces.md)。

   ![](assets/offer_content_create_003.png)

   在此範例中，選件必須包含標題、影像、HTML內容和目的地URL。

## 預覽選件{#previewing-the-offer}

設定優惠方案內容後，您就可以預覽優惠方案的收件者外觀。 操作步驟：

1. 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤。

   ![](assets/offer_preview_create_001.png)

1. 選取您要檢視之選件的表示法。

   ![](assets/offer_preview_create_002.png)

1. 如果您已個人化優惠方案內容，請選取優惠方案目標以檢視個人化。

   ![](assets/offer_preview_create_003.png)

## 在選件{#creating-a-hypothesis-on-an-offer}上建立假設

您可以對您的優惠方案提出假設。 這可讓您判斷優惠方案對針對相關產品執行的購買所產生的影響。

>[!NOTE]
>
>這些假設會透過「回應管理員」執行。 請檢查您的授權合約。

對優惠方案主張執行的假設會在其&#x200B;**[!UICONTROL Measure]**&#x200B;標籤中參考。

在[本頁](../../campaign/using/about-response-manager.md)中會詳細說明建立假設。

![](assets/offer_hypothesis_001.png)
