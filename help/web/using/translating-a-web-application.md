---
title: 轉換Web應用程式
seo-title: 轉換Web應用程式
description: 轉換Web應用程式
seo-description: null
page-status-flag: never-activated
uuid: 7b24a872-d3d1-4473-a6f9-96ba2a0eee8b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 328e5b2f-8596-4eda-8ac5-57cb29bfb691
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 轉換Web應用程式{#translating-a-web-application}

您可以翻譯使用Adobe Campaign數位內容編輯器(DCE)建立的網頁應用程式頁面。

如果您通過Web應用程式的頁籤至少 **[!UICONTROL Localization]** 選擇了 **[!UICONTROL Properties]** 一種其他語言，則在使用DCE編輯的頁面中添加HTML內容塊時，將會出現一個新選項。

此選項可讓您指出是否必須翻譯區塊內容。

要翻譯的字串會透過應用程式的標籤，以與Web應用程式其他字串相同的 **[!UICONTROL Translations]** 方式收集。 有關詳細資訊，請參見[此頁面](../../web/using/translating-a-web-form.md)。

要標籤要翻譯的字串：

1. 在Web應用程式中開啟使用DCE編輯的內容頁。

   ![](assets/dce_translation_3.png)

1. 選取HTML區塊。
1. 在右側的參數區塊中，選 **[!UICONTROL Localization]** 項可讓您標幟選取區塊的內容。 依預設，僅翻譯頁面標題。

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >字串不得超過1023個字元。

   有三種具體情況：

   * 當選取的區塊包含數個字串／區塊時，會標幟為單一字串以進行轉換。 字串接著會包含此區塊內各元素的HTML程式碼。
   * 當您要標籤包含數個字串的區塊，且至少已標籤其中一個字串時，會顯示警告。 然後，您可以從隔離字串移除標幟，並新增整個區塊。

      ![](assets/dce_translation_4.png)

   * 如果要從已標籤的塊中包含的字串中刪除該標誌，則不能直接修改字串轉換選項。 不過，您可以存取包含字串的區塊，以便加以變更。

      ![](assets/dce_translation_2.png)

1. 完成字串的標幟後，請返回Web應用程式並選取標 **[!UICONTROL Translations]** 簽。
1. Select **[!UICONTROL Collect the strings to translate]**. DCE中標籤的字串將添加到Web應用程式的字串中。

   >[!NOTE]
   >
   >收集字串後，如果刪除DCE中的轉換標誌，則不會從清單中刪除這些字串。 這樣可以將它們保留在翻譯庫中。

1. 翻譯並核准字串。

   然後，您就可以從Web應用程式的標籤中選取所需 **[!UICONTROL Preview]** 的語言來預覽翻譯。

