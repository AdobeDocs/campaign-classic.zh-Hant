---
product: campaign
title: 移轉至Adobe Managed Services(Public Cloud)常見問題集
description: Campaign Classic移轉至Public Cloud常見問題集
feature: Overview
role: User
level: Beginner
exl-id: a9cd08b0-55c2-4405-9fb8-f0c623cd4ccb
source-git-commit: 1f050ada481a7307a59ea6c81290bb0b24a3bf6c
workflow-type: tm+mt
source-wordcount: '2243'
ht-degree: 0%

---

# 移轉至公用雲端常見問題集{#dc-faq}

![](../../assets/v7-only.svg)

作為[Gold Standard計畫](../../rn/using/gold-standard.md)的一部分，Adobe將解除舊式資料中心的任務。 Campaign Classic實例必須傳輸到Public Cloud Amazon Web Services(AWS)。 [深入了解此計畫](dc-migration.md)。

以下是關於此專案的一組常見問題、對您的促銷活動環境的影響，以及其他實用資源。

若有其他問題，您可以聯絡[Adobe客戶服務](https://experienceleague.adobe.com/?support-solution=Campaign#support)。

## 基礎架構影響

![](assets/do-not-translate/database.png)

以下列出了對資料庫和基礎架構的全局影響。

* **資料庫是否會更改？新資料庫的版本是什麼？ 將使用什麼作業系統？**

   Adobe保留選擇和部署最適合的資料庫管理引擎以在最佳條件下為Adobe Campaign服務提供服務的權利。

   此外，為了保持最佳的安全級別，Adobe將不提供任何與基礎架構相關的詳細資訊。

* **是否存在資料丟失的風險？**

   資料庫將從舊式資料中心轉儲，並在Public Cloud(AWS)中恢復。 在新資料中心重新啟動後，應用程式將從移轉前的確切狀態恢復。 除了某些已排程的工作會延遲外，使用者不會看到任何差異。

* **舊式資料中心和公共雲之間的套件大小是否有任何差異？**

   我們正在Public Cloud(AWS)中根據當前資料庫大小、磁碟大小等使用新的包定義進行配置。 例如，如果客戶在舊式資料中心有一個應用程式伺服器，則他們可以根據包定義在Public Cloud(AWS)中有兩個應用程式伺服器。

* **組建編號或Campaign版本是否會變更？**

   首先，我們將保留與移轉相同的Campaign Classic組建。

   在進一步步驟中，我們將繼續升級至最新的Campaign ClassicGA版本編號。 如需詳細資訊，請參閱[建置升級常見問題集](../../platform/using/faq-build-upgrade.md)和[Campaign Gold Standard發行說明](../../rn/using/gold-standard.md)。

* **解決遷移後問題的計畫是什麼？**

   在生產系統遷移之前，將進行大量測試。 但是，若有任何問題，[Adobe客戶服務](https://experienceleague.adobe.com/?support-solution=Campaign#support)仍將是主要聯絡點。 Adobe已成立專家團隊，以視需要提供進階支援。

## 傳遞能力影響

![](assets/do-not-translate/features.png)

以下列出對IP、封鎖清單、子網域和URL的全域影響。

* **如何處理允許清單上的IP?客戶是否需要將新的IP位址新增至允許清單，以備從Campaign傳入的流量？**

   Adobe伺服器的IP位址將會變更。 因此，客戶可能需要在其系統的允許清單中新增這些新IP位址。

   [按一](#config) 下這裡，即可在允許清單中取得有關IP的詳細資訊。

* **如何處理新增至允許清單的連接埠，以供SFTP/FTP存取？**

   SFTP設定（允許清單中的公開金鑰+ IP）也將從舊版資料中心移至公開雲端(AWS)。 預期客戶不會採取任何動作。

* **我們是否在更改IP?**

   Adobe伺服器的IP位址將會變更。 因此，客戶可能需要將這些新IP位址新增至其系統中的允許清單。

   [按一](#config) 下這裡，即可在允許清單中取得有關IP的詳細資訊。

* **如何處理子網域委派？**

   現有子網域將從舊版資料中心移至Public Cloud(AWS)。 此部分將由Adobe傳遞團隊在移轉程式中處理。

   Adobe將引導客戶完成所需的測試，以確保在遷移後新的Public Cloud(AWS)伺服器上的配置正常運行。

* **移轉會產生新的URL以用於追蹤、資源和網頁應用程式嗎？**

   否，我們會保留現有的URL。

* **子網域是否會從Neolane.net變更為campaign.adobe.com?**

   移轉後，`neolane.net`和`campaign.adobe.com`都會就緒。 簡化操作：我們將將neolane.net重新導向至Public Cloud(AWS)中的新執行個體，因此不需要客戶進行任何變更。

* **IP升溫的計畫是什麼？**

   首先，Adobe傳遞能力將評估平台的傳遞能力狀態，並建議交換機至新IP的計畫

   移轉後無需熱身。 這可能是某些例外，在此情況下，[Adobe客戶服務](https://experienceleague.adobe.com/?support-solution=Campaign#support)將會聯絡客戶。

   不過，該計畫是讓這項業務透明化，這與上線期間最初的升級不同。

   移轉完成後，Campaign執行個體的傳送IP將會完全不同。 為了確保順利轉換，Adobe將逐步將流量從舊IP切換到新IP，從而實現新發送IP的升級。

* **我們是否會在允許清單上移過URL?**

   是的，這會儲存在伺服器配置檔案中，該檔案將從源複製到新實例。

* **我們使用的委派子網域對溝通方式有何影響？**

   用於行銷通訊的子網域維持不變。 不過，根據實作，用戶端上需要執行下列動作：
   * 如果子網域委派給Adobe（預設）,Adobe會處理所有變更，並確保順暢轉換。
   * 若是CNAME設定（例外），會要求用戶端與Adobe協調實施變更。

## 配置和連接影響

![](assets/do-not-translate/maintenance.png)

### 關於允許清單上IP的注意事項{#config}

遷移到公共雲將隨Adobe Campaign應用程式伺服器的新IP一起提供，這樣，更改IP可能會影響Adobe伺服器和資訊系統之間的連接。

![](assets/migration.png)

讓我們來考慮兩種情況：

* 傳入流量：從您的系統或任何其他第三方啟動到Adobe Campaign伺服器的所有網路活動。 配置將由Adobe處理，然後在移轉期間從舊版複製到公用雲端。 接著，入站流量的連線將保留為移轉後的狀態，且客戶端不會採取任何動作

* 傳出流量：由Adobe Campaign伺服器啟動到您的資訊系統或任何其他第三方的所有網路活動(例如：SMS提供者)。 根據貴組織中的安全策略，更改IP可能需要您的資訊系統或任何其他第三方執行允許清單操作

### 全球影響

以下列出對設定、與其他系統和產品的連線、 API和時區的全域影響。

* **遷移是否會影響到外部帳戶的連接？**

   是. 例如，協力廠商整合（SMS提供者）應將新的Adobe Campaign應用程式伺服器IP位址新增至允許清單。

* **移轉是否會影響使用Adobe Analytics連接器連線至Genesis?如何將促銷活動IP位址新增至Adobe Analytics端的允許清單？**

   Adobe Campaign應用程式伺服器IP位址將會變更。 此步驟將由Adobe客戶服務在移轉後處理。

* **移轉是否會影響與其他Adobe解決方案(AEM、Target等)的連線？**

   整合是在允許清單上宣告之IP位址和網站服務帳戶設定的組合。 這將由Adobe客戶服務負責並擁有。

   允許清單中會有IP位址，當應用程式伺服器IP將變更時，外部解決方案中將會需要這些位址。 將提供此資訊。 整合的其他部分是以IMS為基礎，應能如常運作。

* **為了IMS整合而未附加至組織ID的客戶呢？**

   沒有IMS的客戶將獲得以下資訊：IMS組織ID會附加至其執行個體。

* **多品牌設定是否會受移轉影響？**

   一旦子網域和所有相關設定從舊版資料中心正確移動/重新導向至Public Cloud(AWS)，我們就不會預期會有任何影響。

* **API連線是否會受移轉影響？**

   Adobe伺服器的IP位址將會變更。 因此，客戶可能需要將這些新IP位址新增至其系統中的允許清單。

   [按一](#config) 下這裡以取得允許清單上IP的詳細資訊。

* **我們是否可確保在移轉後正確設定所有JavaScript記憶體設定參數？**

   我們將將執行個體配置從舊版資料中心複製到公用雲(AWS)，因此這些值在遷移後會保留。

* **存取特定副檔名是否有風險？**

   客戶可能希望允許將字型檔案、Outlook會議檔案載入公共資源資料夾中。 此配置在當前`config-<instance>.xml`檔案中完成。 這會與設定檔一起複製。

* **新伺服器上的時區是否更改？客戶是否可以保留其當前時區？**

   它可能會根據新伺服器位置而改變。 不過，客戶將能保留其目前的時區。

   [如需](../../workflow/using/managing-time-zones.md) Adobe Campaign Classic v7時區管理的詳細資訊，請按一下這裡。


## 安全性與權限

![](assets/do-not-translate/security.png)

通過遷移到Public Cloud(AWS)，客戶環境將與所有必要的安全要求保持最新。 包括：

* 定期提供最新作業系統和安全補丁
* 每個客戶的基礎架構隔離
* 為支援雲基礎架構（如負載平衡器、網路安全規則和儲存加密）而進行的托管安全性和審核審核審核。

以下列出對權限、憑證和SFTP存取的影響。

* **我們是否將所有證書移到新伺服器？**

   是的，所有憑證會隨此移轉程式一併移動。

* **我們是否需要向客戶請求新的STP訪問密鑰？**

   否，Adobe會如同在新伺服器上複製SFTP存取金鑰。

* **如何處理SFTP權限？**

   我們會確保新的SFTP伺服器、使用者、目錄和檔案擁有完全相同的權限層級。

* **如果無法建立SFTP連線，因應措施/計畫是什麼以保持客戶運作？**

   可能出現的唯一連接問題與客戶端的允許清單有關。 客戶應在非生產環境中新增此測試，以在移至生產環境前確定其有效性。

* **是否有任何資料中心特定的允許清單配置需要轉移？**

   否，沒有要管理的資料中心特定允許清單配置。

* **我們是否確保在新環境中成功執行自訂指令碼？**

   例如，客戶實施可以在工作流中使用自定義指令碼（Perl/Shell/Python/Java指令碼）來操控檔案和資料夾。

   在托管例項上，指令碼只會透過JavaScript引擎執行。 這些特定實作可能會造成安全漏洞和升級後問題。 不支援。

* **透過IMS整合，此功能是否可如新執行個體般運作，或是否需要額外的設定更新？**

   由於我們保留相同的DNS名稱，因此遷移後應能正常運作。


## 遷移執行

![](assets/do-not-translate/upgrades.png)

以下列出移轉期間的全域影響。

* **我們是否需要規劃在移轉期間停止行銷活動？**

   Adobe建議您在舊式資料中心關閉應用程式之前，放慢速度，最好暫停所有執行：傳遞和工作流程。 這將簡化雲伺服器(AWS)上的重啟，因為流程將有時間「優雅」暫停並保存任何正在進行的執行狀態。

* **我們預期Adobe Campaign服務會停機嗎？**

   遷移過程將伴隨不可避免的平台停機。 此計畫的目的是引導最大限度地減少此停機時間。

   資料中心之間的資料傳輸處於停機的關鍵路徑。 資料的儲存方式有兩種：

   * 最重要的是，資料庫
   * 應用程式伺服器上的檔案（資料匯入和匯出）

   縮小資料庫的大小對於加快資料傳輸至關重要。 建議：

   * 縮短歷史資料（傳送記錄、追蹤記錄等）的保留期
   * 刪除其他表格（傳送、收件者、自訂表格）上無用的記錄


* **遷移實例的預計停機時間是多少？**

   停機時間完全取決於客戶的資料庫大小和SFTP檔案儲存大小。 請洽詢您的客戶服務聯絡人，以取得預估的持續時間。

* **從舊版伺服器傳送的訊息有何變化。連結是否一律可存取？**

   在移轉執行期間，只有一項服務可繼續運作：電子郵件連結重新導向。 所有收件者在電子郵件中按一下後，都將能進入登錄頁面。 不過，系統不會追蹤這些點按，因此移轉前不久開始的傳送點按率將低於往常。

* **中端音效/RT環境呢？**

   MID來源和RT的處理方式與任何其他托管基礎架構相同。

* **將在中執行什麼遷移命令？**

   環境會依下列順序移轉：

   1. 開發環境
   1. 預備環境
   1. 生產環境
   1. RT環境
   1. 中間來源環境

* **什麼是回滾計畫？**

   回滾計畫是將DNS切換回，並將源資料庫設定為從只讀中讀寫。 最終我們將實現自動化。

* **移轉後，我們仍可以存取舊執行個體嗎？**

   應用程式遷移完成後，在舊式資料中心上再運行任何流程的計畫就不存在。 我們希望，除了臨時備份目的外，舊式資料中心上的所有資料都可以被擦除，直到定時備份過程在Public Cloud(AWS)上運行。

* **移轉至Public Cloud後，每個執行個體的測試時間可允許多久？**

   根據客戶複雜性，在Stage環境和生產環境遷移之間至少需要1週的烘焙時間。

* **誰將處理將新IP新增至允許清單？**

   Adobe客戶服務團隊將負責處理，確保客戶和任何協力廠商都能借由將新IP新增至允許清單來存取新系統。

## 支援和其他有效連結{#support}

* [移轉至Adobe Managed Services(Public Cloud)](dc-migration.md)
* [Gold Standard升級](../../rn/using/gs-overview.md)
* [建置升級常見問題集](../../platform/using/faq-build-upgrade.md)