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

您可以翻譯使用Adobe Campaign數字內容編輯器(DCE)建立的Web應用程式頁面。

如果您透過 **[!UICONTROL Localization]** 標籤 **[!UICONTROL Properties]** 在使用DCE編輯的頁面中添加HTML內容塊時，新選項可用。

此選項可讓您指出區塊內容是否必須翻譯。

要翻譯的字串，會透過 **[!UICONTROL Translations]** 頁簽。 如需詳細資訊，請參閱[此頁面](translating-a-web-form.md)。

若要標籤要翻譯的字串：

1. 在Web應用程式中開啟使用DCE編輯的內容頁。

   ![](assets/dce_translation_3.png)

1. 選取HTML區塊。
1. 在右側的參數區塊中， **[!UICONTROL Localization]** 選項可讓您標幟所選取區塊的內容。 依預設，只會翻譯頁面標題。

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >字串不得超過1023個字元。

   有三個具體案例：

   * 當選取的區塊包含數個字串/區塊時，會將其標示為要轉譯的單一字串。 字串則包含此區塊內元素的HTML代碼。
   * 如果要標籤包含數個字串的區塊，並且至少已標籤其中一個字串，則會顯示警告。 然後，您可以從隔離字串中移除標幟，並新增整個區塊。

      ![](assets/dce_translation_4.png)

   * 如果要從已標籤的塊中包含的字串中刪除該標誌，則無法直接修改字串轉換選項。 不過，您可以存取包含字串的區塊以進行變更。

      ![](assets/dce_translation_2.png)

1. 完成字串的標幟後，返回Web應用程式並選取 **[!UICONTROL Translations]** 標籤。
1. 選取 **[!UICONTROL Collect the strings to translate]**。DCE中標籤的字串將添加到Web應用程式的字串中。

   >[!NOTE]
   >
   >收集到字串後，如果您刪除DCE中的翻譯標籤，這些字串將不會從清單中刪除。 這可以將它們保留在翻譯記憶庫中。

1. 翻譯並核准字串。

   然後，您可以從 **[!UICONTROL Preview]** 頁簽。
