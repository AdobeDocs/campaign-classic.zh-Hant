---
product: campaign
title: 自動隱私權請求流程
description: 瞭解如何設定自動化隱私權請求流程
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: a93bac61-f615-4178-bc12-0f056e48687d
source-git-commit: 42b420d7dae7d38e9f4df442146d3b484c25e831
workflow-type: ht
source-wordcount: '652'
ht-degree: 100%

---

# 自動隱私權請求流程 {#automatic-privacy-request-api}

![](../../assets/v7-only.svg)

Adobe Campaign 提供&#x200B;**API**，可讓您設定自動隱私權請求流程。

使用 API 時，一般的隱私權流程與使用介面](privacy-requests-ui.md)的[流程相同。 唯一的不同是隱私權請求的建立。系統不會在 Adobe Campaign 建立請求，而會傳送包含請求資訊的 POST 至 Campaign。 對於每個請求，都會在 **[!UICONTROL Privacy Requests]** 畫面中新增一個項目。 然後，隱私權技術工作流程會處理請求，與使用介面新增請求的方式相同。

如果您使用 API 來提交隱私權請求，建議您保留針對第一個刪除請求啟動的&#x200B;**兩步驟流程**，以測試傳回的資料。 測試完成後，您可以停用兩步驟流程，讓刪除請求流程自動執行。

**[!UICONTROL CreateRequestByName]** JS API 的定義如下。

>[!NOTE]
>
>如果您使用 **gdprRequest** API，您仍可使用它，但建議使用新的 **privacyRequest** API。

>[!IMPORTANT]
>
>**[!UICONTROL Privacy Data Right]** 已命名權限是使用 API 的必要條件。

```
<method library="nms:gdpr.js" name="CreateRequestByName" static="true">
 <help>Create a new GDPR Request using namespace internal name</help>
 <parameters>
  <param name="namespaceName" type="string" desc="Namespace internal name"/>
  <param name="reconciliationValue" type="string" desc="Reconciliation value"/>
  <param name="type" type="long" desc="Reconciliation value"/>
  <param name="confirmDeletePending" type="boolean" desc="Request confirm before deleting data"/>
  <param name="regulation" type="long" desc="regulation of newly created request"/>
  <param name="id" type="long" inout="out" desc="ID of newly created request"/>
 </parameters>
</method>
```

>[!NOTE]
>
>只有當您使用 Campaign Classic 20.2 (build 9178+) 時，「規則」欄位才可用。
>
>如果您要移轉至 20.2，而且已使用 API，則必須新增「規則」欄位，如上所示。 如果您使用先前的建置版本，則可繼續使用 API，而不使用「規則」欄位。

## 在外部叫用 API {#invoking-api-externally}

以下是如何從外部叫用 API 的範例 (特別透過 API 以及隱私權 API 的詳細資訊進行驗證)。 如需隱私權 API 的詳細資訊，請參閱 [API 文件](https://experienceleague.adobe.com/developer/campaign-api/api/s-nms-privacyRequest.html?lang=zh-Hant)。 您也可以參閱 [Web 服務呼叫文件](../../configuration/using/web-service-calls.md)。

首先，您需要透過 API 執行驗證：

1. 透過此 URL 下載 **xtk:session** WSDL：**`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**。

1. 使用「登入」方法，並將使用者名稱和密碼傳入請求中作為參數。 您將會收到包含工作階段權杖的回應。 以下是使用 SoapUI 的範例。

   ![](assets/do-not-localize/privacy-api.png)

1. 使用回傳的工作階段權杖作為所有後續 API 呼叫的驗證。 24 小時後過期。

接著叫用隱私權 API：

1. 從此 URL 下載WSDL：**`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**。

1. 使用 **[!UICONTROL CreateRequestByName]** 建立特定的隱私權請求。

   以下是使用 **[!UICONTROL CreateRequestByName]** 的範例。 請注意我們使用上述的工作階段權杖做為驗證的方法。 回應是已建立請求的 ID。

   ![](assets/do-not-localize/privacy-api-2.png)

   若要協助您執行上述步驟，請考慮下列事項：

   * 您可以在 **nms:gdprRequest** 架構上使用 **queryDef** 來檢查存取請求的狀態。
   * 您可以在 **nms:gdprRequestData** 架構上使用 **queryDef** 來取得存取請求的結果。
   * 若要能夠從 **「$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id」**&#x200B;下載 XML 檔案，您必須登入並從加入允許清單中所包含的 IP 進行存取。 為此，請建立網站應用程式，讓您存取 JSSP 產生的檔案。

## 從 JS 叫用 API {#invoking-api-from-js}

以下範例說明如何從 Campaign Classic 內的 JS 叫用 API。

>[!NOTE]
>
>只有當您使用 Campaign Classic 20.2 (build 9178+) 時，「規則」欄位才可用。
>
>如果您要移轉至 20.2，而且已使用 API，則必須新增「規則」欄位。 如果您使用先前的建置版本，則可繼續使用 API，而不使用「規則」欄位。

* 如果您&#x200B;**使用先前的組建版本 (含 GDPR 套件)**，則可繼續使用 API 而不使用「規則」欄位，如下所示：

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 4 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // GDPR_REQUEST_TYPE_ACCESS = 1;
   // GDPR_REQUEST_TYPE_DELETE = 2;
   var requestType = GDPR_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* 如果您正在&#x200B;**移轉至 20.2，且您已使用 API，則必須新增「規則」欄位，如下所示：**

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is mandatory parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* 如果您&#x200B;**正在使用 Campaign Classic 20.2 (build 9178+) 或更高版本**，可自行選擇是否使用「規則」欄位，如下所示：

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values 
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is optional parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```
