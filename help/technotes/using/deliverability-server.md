---
product: campaign
title: 更新至新的傳遞能力伺服器
description: 瞭解如何更新至新的Campaign傳遞能力伺服器
feature: Technote, Deliverability
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 65b6f91e083c955df044ffeb10f5338104d1ce56
workflow-type: tm+mt
source-wordcount: '1356'
ht-degree: 3%

---

# 更新至新的傳遞能力伺服器 {#acc-deliverability}

正在啟動 [v7.2.2版本](../../rn/using/latest-release.md#release-7-2-2)， Adobe Campaign仰賴全新的傳遞伺服器，以提供高可用性並解決安全性法規遵循問題。 Campaign Classic現在會將與之間的傳遞能力規則、broadlog和隱藏位址同步到新的傳遞能力伺服器。 舊的傳遞伺服器將於2022年8月31日淘汰。

作為Campaign Classic客戶，您必須實作新的傳遞能力伺服器 **2022年8月31日前**.

>[!NOTE]
>
>如需這些變更的詳細資訊，請參閱 [常見問題集](#faq)，或連絡人 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.
>

## 哪些部分有所變更？{#acc-deliverability-changes}

基於安全性法規遵循原因，Adobe正在淘汰較舊的資料中心。 Adobe Campaign Classic使用者端需要移轉至新的傳遞服務，託管於Amazon網站服務(AWS)。

這款新伺服器可確保高可用性(99.9)，並提供安全且經過驗證的端點，讓Campaign伺服器能夠擷取所需的資料：新的傳遞伺服器會快取資料，儘可能為請求提供服務，而非連線至資料庫&#x200B;。 此機制可改善回應時間&#x200B;。

## 您有受到影響嗎？{#acc-deliverability-impacts}

所有客戶都受到影響，必須升級至 [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) 並實作其環境，以受益於新的傳遞能力伺服器。

## 如何更新？{#acc-deliverability-update}

作為 **託管客戶**，Adobe將會與您合作，將您的執行個體升級至更新的版本，並在Adobe Developer主控台中建立專案。

作為 **內部部署/混合客戶**，您必須升級至 [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) （或更多）以受益於新的傳遞能力伺服器。 升級所有執行個體後，您必須 [實施新的整合](#implementation-steps) 以Adobe傳遞伺服器，並確保順暢轉換。

## 實施步驟 {#implementation-steps}

>[!WARNING]
>
>這些步驟只應在混合及內部部署實作中執行。

作為新傳遞能力伺服器整合的一部分，Campaign需要透過Identity Management Service (IMS)驗證與Adobe Shared Services通訊。 首選的方式是使用Adobe Developer型閘道權杖(也稱為技術帳戶權杖或AdobeIO JWT)。

>[!AVAILABILITY]
>
> JWT （JSON Web權杖）目前正在折舊中，將由OAuth取代。 此轉換在Campaign即將發行的版本中逐步執行，檔案將會更新以反映這些更新。

### 必要條件{#prerequisites}

在開始實作之前，請檢查您的執行個體設定。

1. 開啟Campaign使用者端主控台，並以管理員身分登入Adobe Campaign。
1. 瀏覽至 **管理>平台>選項**.
1. 檢查 `DmRendering_cuid` 填入選項值。

   * 如果填入選項，您可以開始實作。
   * 如果未填入任何值，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} 以取得您的CUID。

   您必須在所有Campaign執行個體(MKT、MID、RT、EXEC)上以正確的值填入此選項。 身為混合型客戶，請聯絡Adobe以在MID、RT和EXEC執行個體上設定選項。

身為內部部署客戶，您也必須檢查促銷活動 **[!UICONTROL Product profile]** 可供您的組織使用。 若要執行此作業，請依照下列步驟操作：

1. 以管理員身分，連線至 [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. 存取 **產品與服務** 區段和檢查 **Adobe Campaign** 會列出。
如果您看不到 **Adobe Campaign** 連絡人 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} 以將其新增。
1. 按一下 **Adobe Campaign** 並選取您的組織。
   **注意**：如果您有多個組織，請務必選取正確的組織。 進一步瞭解組織 [在此頁面中](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.

1. 檢查 **[!UICONTROL Product profile]** 「 」已存在。 如果沒有，請建立它。 此許可權不需任何許可權 **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>身為內部部署客戶，如果您已實施防火牆，則必須新增此URL `https://deliverability-service.adobe.io` 加入您的允許清單。 [了解更多](../../installation/using/url-permissions.md)。


### 步驟1：建立/更新您的Adobe Developer專案 {#adobe-io-project}

1. 存取 [Adobe Developer Console](https://developer.adobe.com/console/home) 並使用貴組織的開發人員存取權登入。 請確定您已登入正確的組織入口網站。
   **注意**：如果您有多個組織，請務必選取正確的組織。 進一步瞭解組織 [在此頁面中](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.
1. 選取 **[!UICONTROL Create new project]**。
   ![](assets/New-Project.png)

   >[!CAUTION]
   >
   >如果您已將AdobeIO JWT驗證功能用於其他整合，例如Analytics聯結器或Adobe觸發器，則必須透過新增來更新專案 **Campaign API** 至該專案。

1. 選擇 **[!UICONTROL Add API]**.
   ![](assets/Add-API.png)
1. 在 **[!UICONTROL Add an API]** 視窗，選取 **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. 如果您的使用者端ID是空的，請選取 **[!UICONTROL Generate a key pair]** 以建立公開和私密金鑰組。
   ![](assets/Generate-a-key-pair.png)

   之後，金鑰將會自動下載，預設到期日為365天。 到期後，您需要建立新的金鑰組並更新設定檔案中的整合。 使用選項2，您可以選擇手動建立並上傳 **[!UICONTROL Public key]** 到期日較長。
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >您應儲存 `config.zip` 出現下載提示時的檔案，因為您將無法再次下載。

1. 按一下&#x200B;**[!UICONTROL Next]**。
1. 選擇任何現有的 **[!UICONTROL Product profile]** 或視需要建立新檔案。 此許可權不需任何許可權 **[!UICONTROL Product profile]**. 如需詳細資訊，請參閱 **[!UICONTROL Product Profiles]**，請參閱 [此頁面](https://helpx.adobe.com/enterprise/using/manage-developers.html){_blank}.
   ![](assets/Product-Profile-API.png)

   然後，按一下 **[!UICONTROL Save configured API]**.

1. 在您的專案中，選取 **[!UICONTROL Adobe Campaign]** 並將下列資訊複製到 **[!UICONTROL Service Account (JWT)]**

   ![](assets/Config-API.png)

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>Adobe Developer憑證將在12個月後到期。 您需要每年產生新的金鑰組。

### 步驟2：在Adobe Campaign中新增專案認證 {#add-credentials-campaign}

私密金鑰應該以base64 UTF-8格式編碼。

若要這麼做：

1. 使用上述步驟中產生的私密金鑰。
1. 使用下列命令編碼私密金鑰： `base64 ./private.key > private.key.base64`. 這會將base64內容儲存至新檔案 `private.key.base64`.

   >[!NOTE]
   >
   >複製/貼上私密金鑰時，有時會自動新增額外的行。 在編碼您的私密金鑰之前，請記得移除它。

1. 從檔案複製內容 `private.key.base64`.
1. 透過SSH登入已安裝Adobe Campaign執行個體的每個容器，並透過以下命令在Adobe Campaign中新增Project認證： `neolane` 使用者。 這將會插入 **[!UICONTROL Technical Account]** 執行個體組態檔中的認證。

   ```sql
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. 您必須先停止再重新啟動伺服器，才能考慮修改。 您也可以執行 `config -reload` 命令。

### 步驟3：啟用新的傳遞能力伺服器

您現在可以啟用新的傳遞能力伺服器。 若要執行此動作：

1. 開啟使用者端主控台，並以管理員身分登入Adobe Campaign。
1. 瀏覽至 **管理>平台>選項**.
1. 存取 `NewDeliverabilityServer_FeatureFlag` 選項並將值設為 `1`. 此設定應在您的所有Campaign執行個體(MKT、MID、RT、EXEC)上執行。 身為混合型客戶，請聯絡Adobe以在MID、RT和EXEC執行個體上設定選項。

### 步驟4：驗證設定

若要檢查整合是否成功，請遵循下列步驟：

1. 開啟使用者端主控台並登入Adobe Campaign。
1. 瀏覽至 **管理>生產>技術工作流程**.
1. 重新啟動 **重新整理傳遞能力** (deliverabilityUpdate)工作流程。 這應在您的所有Campaign執行個體(MKT、MID、RT、EXEC)上執行。 身為混合型客戶，請聯絡Adobe讓工作流程在您的MID、RT和EXEC執行個體上重新啟動。
1. 檢查記錄：工作流程應該會在沒有錯誤的情況下執行。

>[!CAUTION]
>
>更新後， **更新收件匣轉譯的種子網路(updateRenderingSeeds)** 工作流程必須停止，因為它將不再套用且會失敗。

## 常見問題集 {#faq}

### 更新的時間表為何？

從7月22日起，託管客戶將開始轉換至新的傳遞伺服器，以便新增這些改良功能並增強安全性(Campaign Managed Services)。 所有託管客戶將於8月底前更新。

內部部署和混合客戶必須在相同時間範圍內進行轉換。

### 如果不升級環境會發生什麼事？

8月31日前未升級的Campaign執行個體將無法再連線至Campaign傳遞伺服器。 因此， **重新整理傳遞能力** (deliverabilityUpdate)工作流程將失敗，而這會影響您的傳遞能力。

如果您不升級環境，電子郵件設定將停止同步（MX管理規則、傳入電子郵件規則、網域管理規則和退回限定規則）。 這可能會隨著時間影響您的傳遞能力。 若對這些規則進行重大變更，則必須從此刻手動套用這些規則。

僅適用於MKT執行個體 [全域隱藏清單](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) 會受到影響。
