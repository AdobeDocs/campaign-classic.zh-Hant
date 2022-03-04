---
product: campaign
title: 追蹤網站應用程式
description: 追蹤網站應用程式
feature: Web Apps
exl-id: 82c5c610-8161-4686-aa79-1b690e763765
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 5%

---

# 追蹤網站應用程式{#translating-a-web-application}

![](../../assets/common.svg)

可以翻譯使用Adobe Campaign數字內容編輯器(DCE)建立的Web應用程式頁。

如果通過 **[!UICONTROL Localization]** 的 **[!UICONTROL Properties]** 在使用DCE編輯的頁面中添加HTML內容塊時，將出現新選項。

此選項用於指示是否必須翻譯塊內容。

要轉換的字串通過 **[!UICONTROL Translations]** 頁籤。 如需詳細資訊，請參閱[此頁面](translating-a-web-form.md)。

要標籤要轉換的字串：

1. 在Web應用程式中開啟使用DCE編輯的內容頁。

   ![](assets/dce_translation_3.png)

1. 選擇HTML塊。
1. 在右側的參數塊中， **[!UICONTROL Localization]** 選項可標籤選定塊的內容。 預設情況下，僅翻譯頁面標題。

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >字串不能超過1023個字元。

   有三個具體案例：

   * 當所選塊包含多個字串/塊時，它被標籤為要轉換的單個字串。 然後，該字串包含此塊內元素的HTML代碼。
   * 如果要標籤包含多個字串的塊，並且至少已標籤其中一個字串，則會顯示警告。 然後，可以從隔離字串中刪除該標誌，並添加整個塊。

      ![](assets/dce_translation_4.png)

   * 如果要從已標籤的塊中包含的字串中刪除該標籤，則不能直接修改字串轉換選項。 但是，您可以訪問包含字串的塊以更改它。

      ![](assets/dce_translation_2.png)

1. 標籤完字串後，返回Web應用程式並選擇 **[!UICONTROL Translations]** 頁籤。
1. 選取 **[!UICONTROL Collect the strings to translate]**。在DCE中標籤的字串將添加到Web應用程式的字串中。

   >[!NOTE]
   >
   >收集字串後，如果刪除DCE中的轉換標誌，則不會從清單中刪除它們。 這樣，它們就可以保留在翻譯記憶庫中。

1. 翻譯和批准字串。

   然後，通過從 **[!UICONTROL Preview]** 的子菜單。
