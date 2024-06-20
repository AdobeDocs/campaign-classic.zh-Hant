---
title: IMS移轉後更新Campaign介面
description: 瞭解如何啟用AdobeIdentity Management系統移轉介面影響
source-git-commit: ab1bb91bdbc9961b4f3f0feba7cfd354b02b6511
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 1%

---

# IMS移轉後更新Campaign介面 {#impact-ims-migration}

一旦您擁有 [已將Campaign技術運運算元移轉至開發人員主控台](ims-migration.md) 和 [已轉換為IMS以進行一般使用者驗證](migrate-users-to-ims.md)，最後一個步驟是啟用使用者介面和API限制，移除原生驗證特有的選項和功能。 此更新自Campaign v7.4.1起可用。

## 啟用IMS限制 {#ims-restrictions}

若要完成移轉至Adobe識別管理系統(IMS)，您必須封鎖新的原生使用者建立、原生使用者登入及原生操作員的API存取。 接著您的環境就會受到保護並標準化。

請以「受管理的Cloud Service/託管」使用者身分聯絡Adobe以啟用此限制，並更新產品使用者介面中的相關更新。

作為內部部署/混合部署使用者，請遵循下列步驟：

1. 瀏覽至 `<imsConfig>` 區段來識別您的執行個體設定檔案。
1. 若要啟用UI限制，請更新 `nonIMSOperatorMgmtInClientConsoleRestricted` 選項，在內 `nonIMSOperatorMgmtInClientConsole` 元素，至 `true`，如下所示：


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. 若要啟用API限制，請更新 `disableAPI` 選項，在內 `nonIMSAuthnAPI` 元素，至 `true`，如下所示：

   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSAuthnAPI disableAPI="true">
               ...
           </nonIMSAuthnAPI>
       </imsConfig>
   </shared>
   </serverConf>
   ```

請注意，允許一些運運算元使用原生驗證連線至Adobe Campaign。 這些技術運運算元預設為啟用，且不得修改。 為了允許此例外，這些技術運運算元預設會新增到允許清單。 您可以在 `<imsConfig>` 區段中的執行個體設定檔案，在 `allowOperator` 內的選項 `nonIMSAuthnAPI` 元素。

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

如果您需要新增運運算元至允許清單，請新增 `allowOperator` 元素與運運算元名稱。 例如，如果您想以名稱新增運運算元 `test`，請更新此區段，如下所示：

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## 使用者介面中的影響 {#ims-impacts}

完成移轉並按如下所述套用限制後，下列變更將套用至產品及其使用者介面。

### 操作員管理 {#manage-admin}

您無法再從使用者端主控台以原生驗證來建立、編輯、更新或刪除運運算元。

因此，使用者端主控台中已停用這些動作。

操作員的管理集中於Adobe Admin Console，而下列工作現在只能透過此主控台管理。 瞭解如何在中建立使用者並指派許可權 [Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### 無法使用的選項 {#unavailable-migration}

移轉後，使用者端主控台中將不再提供下列工作：

* 使用 [合併所選行選項](../../platform/using/updating-data.md#merge-data) 以合併運運算元。

* 更新運運算元的下列欄位：
   * 名稱
   * 密碼
   * 標籤
   * 電子郵件

* [重設您的Campaign密碼](../../production/using/lost-password.md)

* 編輯運運算元的XML來源

* 重複的運運算元。


>[!MORELIKETHIS]
>
>* [終端使用者移轉至IMS](migrate-users-to-ims.md)
>* [技術運運算元移轉至Adobe Developer主控台](ims-migration.md)
>* [Adobe Campaign Classic v7最新發行說明](../../rn/using/latest-release.md)
>* [什麼是AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}

