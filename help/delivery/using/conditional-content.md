---
product: campaign
title: 條件式內容
description: 瞭解如何新增條件式內容
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Personalization, Multilingual Messages
role: User
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 6%

---

# 條件式內容{#conditional-content}

例如，透過設定條件式內容欄位，您可以根據收件者的設定檔建立動態個人化。 當滿足特定條件時，會取代文字區塊及/或影像。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#conditionnal-content-video)


## 在電子郵件中使用條件 {#using-conditions-in-an-email}

在下列範例中，您將會瞭解如何建立訊息，並動態個人化收件者的性別和興趣。

* 顯示「先生」的顯示器 或「女士」 根據的值 **[!UICONTROL Gender]** 欄位（M或F），
* 根據所顯示或偵測到的興趣，個人化地組合電子報或促銷優惠方案：

   * 興趣1 — >區塊1
   * 興趣2 — >區塊2
   * 興趣3 — >區塊3
   * 興趣4 — >區塊4

若要根據欄位值建立條件式內容，請套用下列步驟：

1. 按一下個人化圖示並選取 **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   個人化元素會插入訊息內文中。 您現在必須加以設定。

1. 接下來，填寫 **如果** 運算式。

   操作步驟：

   * 選取運算式的第一個元素， **`<field>`**， (依預設，在插入期間，此元素會反白顯示 **如果** 運算式)，然後按一下個人化圖示，以測試欄位取代它。

     ![](assets/s_ncs_user_conditional_content03.png)

   * 取代 **`<value>`** ，並使用將滿足條件的欄位值。 此值必須在引號中。
   * 指定滿足條件時要插入的內容。 這可能包括文字、影像、表單、超文字連結等。

     ![](assets/s_ncs_user_conditional_content04.png)

1. 按一下 **[!UICONTROL Preview]** 索引標籤以根據傳遞收件者檢視訊息內容：

   * 選取條件為真的收件者：

     ![](assets/s_ncs_user_conditional_content05.png)

   * 選取條件不為真的收件者：

     ![](assets/s_ncs_user_conditional_content06.png)

您可以新增其他案例，並根據一或多個欄位的值定義不同的內容。 若要這麼做，請使用 **[!UICONTROL Conditional content > Else]** 和 **[!UICONTROL Conditional content > Else if]**. 這些運算式的設定方式與 **如果** 運算式。

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>如要遵循JavaScript語法， **%> &lt;%** 新增後必須刪除字元 **否則** 和 **否則，如果** 條件。

按一下 **[!UICONTROL Preview]** 並選取收件者以檢視條件式內容。

![](assets/s_ncs_user_conditional_content08.png)

## 建立多語言電子郵件 {#creating-multilingual-email}

在下列範例中，您將瞭解如何建立多語言電子郵件。 內容將會根據收件者偏好的語言，以一種或另一種語言顯示。

1. 建立電子郵件並選取目標母體。 在此範例中，顯示某個版本的條件將以 **語言** 收件者設定檔的值。 在此範例中，這些值設定為 **EN**， **FR**， **ES**.
1. 在電子郵件HTML內容中，按一下 **[!UICONTROL Source]** 並貼上下列程式碼：

   ```
   <% if (language == "EN" ) { %>
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %>
   <% if (language == "FR" ) { %>
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %>
    <% if (language == "ES" ) { %>
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %>
   ```

1. 在中測試電子郵件內容 **[!UICONTROL Preview]** 索引標籤中，選取具有不同偏好語言的收件者。

   >[!NOTE]
   >
   >由於電子郵件內容中未定義替代版本，因此在傳送電子郵件前請務必篩選目標母體。

## 教學課程影片 {#conditionnal-content-video}

此影片以多語言電子報為範例，示範如何新增條件式內容至傳遞。

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

提供其他Campaign Classic操作影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
