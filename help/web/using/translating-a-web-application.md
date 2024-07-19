---
product: campaign
title: 追蹤網站應用程式
description: 追蹤網站應用程式
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Apps
exl-id: 82c5c610-8161-4686-aa79-1b690e763765
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 5%

---

# 追蹤網站應用程式{#translating-a-web-application}



您可以翻譯使用Adobe Campaign數位內容編輯器(DCE)建立的網頁應用程式頁面。

如果您透過Web應用程式的&#x200B;**[!UICONTROL Properties]**&#x200B;中的&#x200B;**[!UICONTROL Localization]**&#x200B;索引標籤至少選取一種其他語言，則在使用DCE編輯的頁面中新增HTML內容區塊時，便可使用新選項。

此選項可讓您指定是否必須翻譯區塊內容。

要翻譯的字串收集方式與網頁應用程式的其他字串收集方式相同，是透過應用程式的&#x200B;**[!UICONTROL Translations]**&#x200B;索引標籤進行。 如需詳細資訊，請參閱[此頁面](translating-a-web-form.md)。

標幟要翻譯的字串：

1. 在Web應用程式中開啟使用DCE編輯的內容頁面。

   ![](assets/dce_translation_3.png)

1. 選取HTML區塊。
1. 在右側的引數區塊中，**[!UICONTROL Localization]**&#x200B;選項可讓您標幟所選區塊的內容。 依預設，僅翻譯頁面標題。

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >字串不得超過1023個字元。

   有三個特定案例：

   * 當選取的區塊包含數個字串/區塊時，系統會將其標示為單一字串以供翻譯。 字串則包含此區塊中元素的HTML程式碼。
   * 當您想要標幟包含數個字串的區塊時，如果至少其中一個字串已經標幟，則會顯示警告。 然後，您可以從隔離字串中移除標幟，並新增整個區塊。

     ![](assets/dce_translation_4.png)

   * 當您想要從已標幟的區塊中包含的字串中移除標幟時，無法直接修改字串轉譯選項。 不過，您可以存取包含字串的區塊以進行變更。

     ![](assets/dce_translation_2.png)

1. 完成標幟字串後，請返回Web應用程式並選取&#x200B;**[!UICONTROL Translations]**&#x200B;標籤。
1. 選取 **[!UICONTROL Collect the strings to translate]**。在DCE中標幟的字串會新增至Web應用程式的字串。

   >[!NOTE]
   >
   >收集到字串後，如果您在DCE中移除翻譯旗標，就不會從清單中移除這些字串。 這樣可讓翻譯記憶庫儲存它們。

1. 翻譯及核准字串。

   然後，您可以從Web應用程式的&#x200B;**[!UICONTROL Preview]**&#x200B;索引標籤中選取所需的語言來預覽翻譯。
