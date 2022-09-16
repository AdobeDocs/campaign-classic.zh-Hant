---
product: campaign
title: 更新至新的傳遞能力伺服器
description: 了解如何更新至新的Campaign傳遞伺服器
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 50ef144950ca9e79b1b3acdf587ffc13e0beeec4
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 3%

---

# 更新至新的傳遞能力伺服器 {#acc-deliverability}

開始 [v7.2.2版](../../rn/using/latest-release.md#release-7-2-2),Adobe Campaign需仰賴新的傳遞能力伺服器，提供高可用性並解決安全性法規遵循問題。 Campaign Classic現在會將傳遞規則、廣播和隱藏地址從和同步到新的傳遞能力伺服器。 舊的傳遞能力伺服器將於2022年8月31日解壓縮。

身為Campaign Classic客戶，您必須實作新的傳遞能力伺服器 **2022年8月31日前**.

>[!NOTE]
>
>如需這些變更的詳細資訊，請參閱 [常見問題集](#faq)，或聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}。

## 有什麼改變？{#acc-deliverability-changes}

Adobe因安全性法規遵循原因而正在停用舊版資料中心。 Adobe Campaign Classic用戶端需要移轉至由Amazon網站服務(AWS)托管的新傳遞服務。

這部新伺服器可保證高可用性(99.9),&#x200B;並提供安全且已驗證的端點，讓行銷活動伺服器可擷取所需資料：新的傳遞能力伺服器不會針對每個請求連接到資料庫，而是會盡可能快取資料以提供請求。 此機制可改善回應時間&#x200B;。

## 您有受到影響嗎？{#acc-deliverability-impacts}

所有客戶都會受到影響，必須升級至 [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) （或更多）並實作其環境，以從新的傳遞能力伺服器中獲益。

## 如何更新？{#acc-deliverability-update}

As a **托管客戶**,Adobe會與您合作，將您的執行個體升級至較新版本，並在Adobe Developer Console中建立專案。

作為 **內部部署/混合客戶**，您需要升級至 [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) （或更多）從新的傳遞能力伺服器中獲益。 升級所有執行個體後，您必須 [實作新整合](#implementation-steps) Adobe傳遞能力伺服器，並確保順暢轉換。

## 實施步驟 {#implementation-steps}

作為新傳遞能力伺服器整合的一部分，Campaign需要透過Identity Management服務(IMS)驗證與Adobe共用服務通訊。 偏好的方式是使用Adobe Developer型閘道代號(又稱為技術帳戶代號或AdobeIO JWT)。

>[!WARNING]
>
>這些步驟只應針對混合式和內部部署實作執行。

### 必要條件{#prerequisites}

開始實作前，請檢查您的執行個體設定。

1. 開啟Campaign用戶端主控台，並以管理員身分登入Adobe Campaign。
1. 瀏覽至 **管理>平台>選項**.
1. 檢查 `DmRendering_cuid` 填入選項值。

   * 如果已填入選項，您可以開始實施。
   * 如果未填入值，請聯繫 [Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}獲取CUID。

   必須以正確的值填入所有Campaign執行個體(MKT、MID、RT、EXEC)上的此選項。 身為混合型Adobe，請洽詢，在MID、RT和EXEC執行個體上設定選項。

身為內部部署客戶，您也必須檢查促銷活動 **[!UICONTROL Product profile]** 可供您的組織使用。 若要執行此作業，請遵循下列步驟：

1. 身為管理員，請連線至 [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}。
1. 存取 **產品與服務** 區段與檢查 **Adobe Campaign** 清單中。
如果您看不到 **Adobe Campaign** 聯絡人 [Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}以添加它。
1. 按一下 **Adobe Campaign** 並選取您的組織。
   **注意**:如果您有多個組織，請務必選取正確的組織。 深入了解組織 [在本頁](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}。

1. 檢查 **[!UICONTROL Product profile]** 存在。 否則請建立它。 不需要權限 **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>身為內部部署客戶，如果您已在您的端實作防火牆，您必須新增此url `https://deliverability-service.adobe.io` 加入允許清單。 [了解更多資訊](../../installation/using/url-permissions.md)。


### 步驟1:建立/更新您的Adobe Developer專案 {#adobe-io-project}

1. 存取 [Adobe Developer Console](https://developer.adobe.com/console/home) 並使用貴組織的開發人員存取權登入。 請確定您已登入正確的組織入口網站。
   **注意**:如果您有多個組織，請務必選取正確的組織。 深入了解組織 [在本頁](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}。
1. 選取 **[!UICONTROL Create new project]**。
   ![](assets/New-Project.png)

   >[!CAUTION]
   >
   >如果您已將AdobeIO JWT驗證功能用於其他整合(例如Analytics連接器或Adobe觸發器)，則必須新增以更新專案 **行銷活動API** 到那個項目。

1. 選擇 **[!UICONTROL Add API]**.
   ![](assets/Add-API.png)
1. 在 **[!UICONTROL Add an API]** 窗口，選擇 **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. 如果您的用戶端ID為空，請選取 **[!UICONTROL Generate a key pair]** 來建立公開和私密金鑰組。
   ![](assets/Generate-a-key-pair.png)

   接著，系統會自動下載金鑰，預設到期日為365天。 到期後，您需要建立新金鑰組並更新設定檔案中的整合。 使用選項2，您可以選擇手動建立和上傳 **[!UICONTROL Public key]** 具有較長的到期日。
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >您應將 `config.zip` 下載提示出現時才會下載檔案，因為您無法再次下載。

1. 按一下&#x200B;**[!UICONTROL Next]**。
1. 選擇任何現有 **[!UICONTROL Product profile]** 或視需要建立新的。 不需要權限 **[!UICONTROL Product profile]**. 如需 **[!UICONTROL Product Profiles]**，請參閱 [本頁](https://helpx.adobe.com/enterprise/using/manage-developers.html){_blank}。
   ![](assets/Product-Profile-API.png)

   然後，按一下 **[!UICONTROL Save configured API]**.

1. 從專案中選取 **[!UICONTROL Adobe Campaign]** 並複製下列資訊 **[!UICONTROL Service Account (JWT)]**

   ![](assets/Config-API.png)

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>Adobe Developer憑證將在12個月後到期。 您每年需要產生新的金鑰組。

### 步驟2:在Adobe Campaign中新增專案認證 {#add-credentials-campaign}

私密金鑰應以base64 UTF-8格式編碼。

若要這麼做：

1. 使用上述步驟中產生的私密金鑰。
1. 使用下列命令對私密金鑰進行編碼： `base64 ./private.key > private.key.base64`. 這會將base64內容儲存至新檔案 `private.key.base64`.

   >[!NOTE]
   >
   >複製/貼上私密金鑰時，有時可自動新增額外的行。 請記得在對私密金鑰進行編碼前將其移除。

1. 從檔案複製內容 `private.key.base64`.
1. 透過SSH登入安裝Adobe Campaign執行個體的每個容器，並執行下列命令以新增Adobe Campaign中的專案憑證 `neolane` 使用者。 這會插入 **[!UICONTROL Technical Account]** 執行個體設定檔案中的憑證。

   ```sql
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. 您必須停止，然後重新啟動伺服器，才能考慮修改。 您也可以執行 `config -reload` 命令。

### 步驟3:啟用新的傳遞能力伺服器

您現在可以啟用新的傳遞能力伺服器。 若要執行此動作：

1. 開啟用戶端主控台，並以管理員身分登入Adobe Campaign。
1. 瀏覽至 **管理>平台>選項**.
1. 存取 `NewDeliverabilityServer_FeatureFlag` 選項，並將值設為 `1`. 此設定應在您的所有Campaign執行個體(MKT、MID、RT、EXEC)上執行。 身為混合型Adobe，請洽詢，在MID、RT和EXEC執行個體上設定選項。

### 步驟4:驗證您的設定

若要檢查整合是否成功，請遵循下列步驟：

1. 開啟用戶端主控台並登入Adobe Campaign。
1. 瀏覽至 **管理>生產>技術工作流程**.
1. 重新啟動 **重新整理傳遞能力** (deliverabilityUpdate)工作流程。 這應該在您的所有Campaign執行個體(MKT、MID、RT、EXEC)上執行。 身為混合型Adobe，請洽詢，讓工作流程在MID、RT和EXEC執行個體上重新啟動。
1. 檢查日誌：工作流程應會執行，而不會發生錯誤。

>[!CAUTION]
>
>更新後， **更新收件匣轉譯種子網路(updateRenderingSeeds)** 工作流程必須停止，因為它將不再套用且會失敗。

## 常見問題集 {#faq}

### 更新的時間表是什麼？

從』22年7月開始，代管客戶(Campaign Managed Services)將可開始轉換至新的傳遞能力伺服器，以增加這些改善的功能並增強安全性。 所有托管客戶將在8月底前更新。

內部部署和混合客戶必須在相同的時間範圍內進行轉換。

### 如果我未升級環境，會發生什麼情況？

任何在8月31日之前未升級的Campaign執行個體將無法再與Campaign傳遞伺服器連線。 因此， **重新整理傳遞能力** (deliverabilityUpdate)工作流程將失敗，這將影響您的傳遞能力。

如果您未升級環境，則電子郵件設定將停止同步（MX管理規則、入站電子郵件規則、網域管理規則和退信限定規則）。 這可能會隨著時間而影響您的傳遞能力。 如果這些規則發生重大變更，則必須從此點手動套用。

僅適用於MKT例項 [全局隱藏清單](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) 會受到影響。
