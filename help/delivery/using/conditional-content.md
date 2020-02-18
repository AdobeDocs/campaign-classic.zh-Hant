---
title: 條件式內容
seo-title: 條件式內容
description: 條件式內容
seo-description: null
page-status-flag: never-activated
uuid: d1c38263-a163-448c-8822-8b3e776e45cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 167cc61a-fbc7-48cb-89ff-fbdbf9321c01
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# 條件式內容{#conditional-content}

例如，透過設定條件式內容欄位，您可以根據收件者的個人檔案建立動態個人化。 當滿足特定條件時，替代文字塊和／或影像。

## 在電子郵件中使用條件 {#using-conditions-in-an-email}

在下列範例中，您將學習如何建立訊息，根據收件者的性別和興趣動態個人化。

* 顯示&quot;Mr&quot;的顯示。 或「Ms」 根據資料來源 **[!UICONTROL Gender]** 中欄位（M或F）的值，
* 根據所顯示或偵測到的興趣，個人化組合電子報或促銷優惠：

   * 興趣1 — >塊1
   * 興趣2 — >區塊2
   * 興趣3 — >區塊3
   * 興趣4 — >塊4

若要根據欄位值建立條件式內容，請套用下列步驟：

1. 按一下個人化圖示並選取 **[!UICONTROL Conditional content > If]**。

   ![](assets/s_ncs_user_conditional_content02.png)

   個人化元素會插入訊息內文。 您現在必須設定它們。

1. 接著，填入if運算式的 **參數** 。

   操作步驟：

   * 選取運算式的第一個元素 **`<field>`**(依預設，在插入 **if** expression時會反白顯示此元素)，然後按一下個人化圖示，以測試欄位取代它。

      ![](assets/s_ncs_user_conditional_content03.png)

   * 以 **`<value>`** 滿足條件的欄位的值替換。 此值必須用引號表示。
   * 指定滿足條件時要插入的內容。 這可能由文字、影像、表單、超文字連結等組成。

      ![](assets/s_ncs_user_conditional_content04.png)

1. 按一下 **[!UICONTROL Preview]** 標籤，以根據傳送收件者檢視訊息的內容：

   * 選擇條件為true的收件者：

      ![](assets/s_ncs_user_conditional_content05.png)

   * 選擇條件不正確的收件者：

      ![](assets/s_ncs_user_conditional_content06.png)

您可以新增其他案例，並根據一或多個欄位的值來定義不同的內容。 若要這麼做，請使用 **[!UICONTROL Conditional content > Else]** 和 **[!UICONTROL Conditional content > Else if]**。 這些運算式的設定方式與 **if** 運算式相同。

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>若要遵循JavaScript語法，必 **須在新增Else和Else（如果條件）後刪除** % **> &lt;%** 字元 **** 。

按一 **[!UICONTROL Preview]** 下並選取收件者，以檢視條件式內容。

![](assets/s_ncs_user_conditional_content08.png)

## 建立多語言電子郵件 {#creating-multilingual-email}

在以下範例中，您將學習如何建立多語言電子郵件。 內容會根據收件者偏好的語言，以一種或另一種語言顯示。

1. 建立電子郵件並選取目標人口。 在此範例中，顯示一個或另一個版本的條件將以收件者描述檔的 **Language** value為基礎。 在此範例中，這些值設 **為EN**、 **FR**、 **ES**。
1. 在電子郵件HTML內容中，按一下標 **[!UICONTROL Source]** 簽並貼上下列程式碼：

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

1. 選擇使用不同慣用語 **[!UICONTROL Preview]** 言的收件者，以測試標籤中的電子郵件內容。

   >[!NOTE]
   >
   >由於電子郵件內容中未定義任何替代版本，請務必在傳送電子郵件前先篩選目標人口族群。
