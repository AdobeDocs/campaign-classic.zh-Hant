---
product: campaign
title: 編輯表單
description: 編輯表單
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: 42717f3ef3bcda4108dad6a4c0ece752ada579a2
workflow-type: tm+mt
source-wordcount: '1647'
ht-degree: 2%

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

## 容器

在表單中，您可以將容器用於各種用途：

* 在表單中組織內容
* 定義輸入欄位的存取權
* 在其他表單中巢狀內嵌表單

[顯示全文](form-structure.md#containers)。

### 組織內容

使用容器來組織表單中的內容：

* 您可以將欄位分組為區段。
* 您可以將頁面新增至多頁表單。

若要插入容器，請使用 `<container>` 元素。 [顯示全文](form-structure.md#containers)。

#### 群組欄位

使用容器將輸入欄位分組為有組織的區段。

若要將區段插入表單中，請使用此元素： `<container type="frame">`. （可選）要添加節標題，請使用 `label` 屬性。

語法： `<container type="frame" label="`*section_title*`"> […] </container>`

在此範例中，容器定義 **建立** 部分，包括 **[!UICONTROL Created by]** 和 **[!UICONTROL Name]** 輸入欄位：

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### 將頁面新增至多頁表單

對於多頁表單，請使用容器建立表單頁面。

此範例顯示 **一般** 和 **詳細資料** 表單頁面：

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### 定義欄位存取

使用容器來定義可見項目，並定義欄位的存取權。 您可以開啟或關閉欄位群組。

### 巢狀表單

使用容器在其他表單中巢狀內嵌表單。 [顯示全文](#add-pages-to-multipage-forms)。

## 影像參考

要查找影像，請選擇 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** 的上界。

若要將影像與表單中的元素（例如圖示）建立關聯，您可以將參照新增至影像。 使用 `img` 屬性，例如 `<container>` 元素。

語法: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

此範例顯示 `book.png` 和 `detail.png` 影像 `ncm` 命名空間：

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

這些影像用於使用者點按以導覽多頁表單的圖示：

![](assets/nested_forms_preview.png)

## 建立簡單表單 {#create-simple-form}

要建立表單，請執行以下步驟：

1. 從功能表中，選擇 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
1. 按一下 **[!UICONTROL New]** 按鈕。

   ![](assets/input-form-create-1.png)

1. 指定表單屬性：

   * 指定表單名稱和命名空間。

      表單名稱和命名空間可以符合相關資料架構。  此範例顯示 `cus:order` 資料架構：

      ```xml
      <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
        […]
      </form>
      ```

      或者，您可以在 `entity-schema` 屬性。

      ```xml
      <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
        […]
      </form>
      ```

   * 指定要在表單上顯示的標籤。
   * （可選）指定表單類型。 如果您未指定表單類型，預設會使用主控台螢幕類型。

      ![](assets/input-form-create-2.png)

      如果您要設計多頁表單，可以忽略 `<form>` 元素，並指定容器中的類型。

1. 按一下&#x200B;**[!UICONTROL Save]**。

1. 插入表單元素。

   例如，若要插入輸入欄位，請使用 `<input>` 元素。 設定 `xpath` 屬性作為XPath表達式。 [顯示全文](schema-structure.md#referencing-with-xpath)。

   此範例顯示以 `nms:recipient` 綱要。

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. 如果表單是以特定架構類型為基礎，您可以查找此架構的欄位：

   1. 按一下 **[!UICONTROL Insert]** > **[!UICONTROL Document fields]**.

      ![](assets/input-form-create-4.png)

   1. 選取欄位，然後按一下 **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. （可選）指定欄位編輯器。

   預設欄位編輯器與每個資料類型相關聯：
   * 對於日期類型欄位，表單會顯示輸入日曆。
   * 對於枚舉類型欄位，表單顯示選擇清單。

   您可以使用下列欄位編輯器類型：

   | 欄位編輯器 | 表單屬性 |
   | --- | --- |
   | 選項按鈕 | `type="radiobutton"` |
   | 核取方塊 | `type="checkbox"` |
   | 編輯樹 | `type="tree"` |

   深入了解 [記憶體清單控制項](form-structure.md#memory-list-controls).

1. （可選）定義欄位的訪問：

   | 元素 | 屬性 | 說明 |
   | --- | --- | --- |
   | `<input>` | `read-only:"true"` | 提供欄位的唯讀存取權 |
   | `<container>` | `type="visibleGroup" visibleIf="`*編輯 — expr*`"` | 有條件地顯示一組欄位 |
   | `<container>` | `type="enabledGroup" enabledIf="`*編輯 — expr*`"` | 有條件地啟用一組欄位 |

   範例:

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. （可選）使用容器將欄位分組為各節。

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## 建立多頁表單 {#create-multipage-form}

您可以建立多頁表單。 您也可以在其他表單中巢狀內嵌表單。

### 建立 `iconbox` 表單

使用 `iconbox` 表單類型，顯示表單左側的圖示，這會帶使用者前往表單中的不同頁面。

![](assets/iconbox_form_preview.png)

將現有表單的類型更改為 `iconbox`，請遵循下列步驟：

1. 變更 `type` 屬性 `<form>` 元素 `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. 為每個表單頁面設定容器：

   1. 新增 `<container>` 元素作為的子項 `<form>` 元素。
   1. 若要定義圖示的標籤和影像，請使用 `label` 和 `img` 屬性。

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```
   或者，移除 `type="frame"` 屬性 `<container>` 元素。

### 建立筆記本表單

使用 `notebook` 表單類型，可在表單頂端顯示索引標籤，讓使用者前往不同的頁面。

![](assets/notebook_form_preview.png)

將現有表單的類型更改為 `notebook`，請遵循下列步驟：

1. 變更 `type` 屬性 `<form>` 元素 `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. 為每個表單頁面新增容器：

   1. 新增 `<container>` 元素作為的子項 `<form>` 元素。
   1. 若要定義圖示的標籤和影像，請使用 `label` 和 `img` 屬性。

   ```xml
     <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
         <container label="General">
             <input xpath="@label"/>
             <input xpath="@name"/>
             […]
         </container>
         <container label="Details">
             <input xpath="@address"/>
             […]
         </container>
         <container label="Services">
             […]
         </container>
     </form>
   ```

   或者，移除 `type="frame"` 屬性 `<container>` 元素。

### 巢狀表單 {#nest-forms}

您可以在其他表單內巢狀內嵌表單。 例如，您可以在iconbox表單內巢狀內嵌筆記型電腦表單。

嵌套控制項的導航級別。 使用者可以向下切入子表單。

要在其他表單中嵌套表單，請插入 `<container>` 元素並設定 `type` 屬性。 對於頂層表單，您可以在外部容器或 `<form>` 元素。

### 範例

此範例顯示複雜表單：

* 頂層表單是iconbox表單。 該形式包括兩個標籤的容器 **一般** 和 **詳細資料**.

   因此，外部表單會顯示 **一般** 和 **詳細資料** 頁面。 若要存取這些頁面，使用者請按一下表單左側的圖示。

* 子表單是嵌套在 **一般** 容器。 該子表單包括兩個標籤的容器 **名稱** 和 **連絡人**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

因此， **一般** 外部表單的頁面顯示 **名稱** 和 **連絡人** 頁簽。

![](assets/nested_forms_preview.png)

## 修改工廠輸入表單 {#modify-factory-form}

要修改工廠表單，請執行以下步驟：

1. （可選）擴展相關資料架構：

   1. 從功能表中，選擇 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**.
   1. 選取資料結構並加以擴充。 例如，您可以新增欄位。 [顯示全文](extending-a-schema.md)。

      >[!CAUTION]
      > 請勿在工廠命名空間中修改原始資料，而是在自訂命名空間中擴充資料。 原因在於，在軟體升級期間，工廠命名空間中的所有資料都會遭到覆寫。 例如， `xtk`, `ncm`，和 `nms` 工廠命名空間會遭覆寫。 未修改自訂命名空間中的資料。

1. 修改工廠輸入表單：

   1. 從功能表中，選擇 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
   1. 選取輸入表單並加以修改。

   您可以擴展工廠資料結構，但無法擴展工廠輸入表單。 建議您直接修改工廠輸入表單，而不重新建立。 在軟體升級期間，您在工廠輸入表單中的修改將與升級合併。 如果自動合併失敗，您可以解決衝突。 [顯示全文](../../production/using/upgrading.md#resolving-conflicts)。

   例如，如果您使用其他欄位擴展出廠架構，則可以將此欄位添加到相關的工廠表單。

## 驗證表單 {#validate-forms}

您可以在表單中加入驗證控制項。

### 授予欄位的唯讀存取權

若要授予欄位的唯讀存取權，請使用 `readOnly="true"` 屬性。 例如，您可能想要顯示記錄的主要索引鍵，但具有唯讀存取權。 [顯示全文](form-structure.md#non-editable-fields)。

在此範例中，主鍵(`iRecipientId`) `nms:recipient` 架構以唯讀存取顯示：

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### 檢查必填欄位

您可以檢查必填資訊：

* 使用 `required="true"` 屬性。
* 使用 `<leave>` 節點來檢查這些欄位並顯示錯誤訊息。

在此範例中，需要電子郵件地址，如果使用者未提供此資訊，則會顯示錯誤訊息：

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

深入了解 [運算式欄位](form-structure.md#expression-field) 和 [表單內容](form-structure.md#context-of-forms).

### 驗證值

您可以使用JavaScript SOAP呼叫，從主控台驗證表單資料。 例如，使用這些呼叫進行複雜驗證，以根據授權值清單檢查值。 [顯示全文](form-structure.md#soap-methods)。

1. 在JS檔案中建立驗證函式。

   範例:

   ```js
   function nms_recipient_checkValue(value)
   {
     logInfo("checking value " + value)
     if (…)
     {
       logError("Value " + value + " is not valid")
     }
     return 1
   }
   ```

   在此範例中，函式的名稱為 `checkValue`. 此函式用於檢查 `recipient` 資料類型 `nms` 命名空間。 系統會記錄正在檢查的值。 如果值無效，則會記錄錯誤訊息。 如果值有效，則返回值1。

   您可以使用傳回的值來修改表單。

1. 在表單中，新增 `<soapCall>` 元素 `<leave>` 元素。

   在此範例中，SOAP呼叫用於驗證 `@valueToCheck` 字串：

   ```xml
   <form name="recipient" (…)>
   (…)
     <leave>
       <soapCall name="checkValue" service="nms:recipient">
         <param exprIn="@valueToCheck" type="string"/>
       </soapCall>
     </leave>
   </form>
   ```

   在此範例中， `checkValue` 方法與 `nms:recipient` 服務已使用：

   * 服務是命名空間和資料類型。
   * 方法是函式名稱。 名稱區分大小寫。

   呼叫會同步執行。

   將顯示所有例外。 如果您使用 `<leave>` 元素，則使用者必須等到輸入的資訊經過驗證後，才能儲存表單。

此範例說明如何從表單進行服務呼叫：

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

在此範例中，輸入是ID，此為主鍵。 當使用者填寫此ID的表單時，會以此ID作為輸入參數進行SOAP呼叫。 輸出是寫入此欄位的布林值： `/tmp/@count`. 您可以在表單內使用此布林值。 深入了解 [表單內容](form-structure.md#context-of-forms).
