---
product: campaign
title: 編輯表單
description: 編輯表單
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: a6549ad4d94b93d65752df66aeec39b90e4c3ec5
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 5%

---


# 編輯表單{#editing-forms}

![](../../assets/common.svg)

## 概覽

行銷人員和營運商使用輸入表單來建立、修改和預覽記錄。 Forms會顯示資訊的視覺表示法。

您可以建立和修改輸入表單：

* 您可以修改預設傳送的工廠輸入表單。 工廠輸入表單以工廠資料結構為基礎。
* 您可以根據定義的資料結構，建立自訂輸入表單。

Forms是 `xtk:form` 類型。 您可以在 `xtk:form` 綱要。 要查看此架構，請選擇 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** 的上界。 深入了解 [表單結構](form-structure.md).

要訪問輸入表單，請選擇 **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** 從功能表：

![](assets/d_ncs_integration_form_arbo.png)

要設計表單，請在XML編輯器中編輯XML內容：

![](assets/d_ncs_integration_form_edit.png)

[顯示全文](form-structure.md#formatting)。

若要預覽表單，請按一下 **[!UICONTROL Preview]** 標籤：

![](assets/d_ncs_integration_form_preview.png)

## 表單類型

您可以建立不同類型的輸入表單。 表單類型決定使用者導覽表單的方式：

* 主控台畫面

   這是預設的表單類型。 表單包含單頁。

   ![](assets/console_screen_form.png)

* 內容管理

   此表單類型用於內容管理。 看這個 [使用案例](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* 精靈

   該形式包括按特定順序排列的多個浮動螢幕。 使用者從一個畫面導覽至下一個畫面。 [顯示全文](form-structure.md#wizards)。

* Iconbox

   此表單包含多頁。 若要導覽表單，使用者需選取表單左側的圖示。

   ![](assets/iconbox_form_preview.png)

* 筆記本

   此表單包含多頁。 若要導覽表單，使用者需選取表單頂端的標籤。

   ![](assets/notebook_form_preview.png)

* 垂直窗格

   此表單顯示導航樹。

* 水準窗格

   此表單顯示項目清單。

