---
product: campaign
title: 調整您的設定
description: 了解如何在移轉至Campaign v7之前和之後調整您的配置
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 2%

---

# 調整您的設定{#configuring-your-platform}



Adobe Campaign v7中的某些重大變更需要特定設定。 移轉之前或之後，可能需要進行這些設定。

在移轉期間， **NmsRecipient** 表格是從結構定義中重建。 在Adobe Campaign之外對此表的SQL結構所做的任何更改都將丟失。

要檢查的元素範例：

* 如果您已將欄（或索引）新增至 **NmsRecipient** 表格，但您尚未在架構中詳細說明，則系統不會儲存此表格。
* 此 **表空間** 屬性預設會回傳其值，亦即部署精靈中定義的值。
* 如果您已將參考檢視新增至 **NmsRecipient** 表格，您必須先將其刪除，才能移轉。


## 移轉前 {#before-the-migration}

移轉至Adobe Campaign v7時，必須設定下列元素。 在開始 **postugrade**.

<!--

  * Timezones

  During a migration from a v5.11 platform, you must specify the timezone to use during the postupgrade.

  If you wish to use the "multi timezone" mode, refer to [this section](../../migration/using/general-configurations.md#time-zones).

  If you use Oracle as a database, check that the Oracle timezone files have properly been synched between the application server and the database server. [Learn more](../../migration/using/general-configurations.md#oracle)

* Security zones

  For security reasons, the Adobe Campaign platform is no longer accessible by default: you must configure the security zones, which requires collecting the user IP addresses before the migration. [Learn more](../../migration/using/general-configurations.md#security)

* Syntax

  Some Javascript code may no longer accepted in the v7 version, due to the use of a new interpreter. [Learn more](../../migration/using/general-configurations.md#javascript).

  Similarly, a new syntax is introduced in Adobe Campaign v7 to replace the SQLData based syntax. If you use code elements with this syntax, you must adapt them. [Learn more](../../migration/using/general-configurations.md#sqldata)

  -->

* 密碼

   您必須設定 **管理** 和 **內部** 密碼。 [了解更多](../../migration/using/before-starting-migration.md#user-passwords)

<!--
* Tree structure

  If migrating from a v5.11 platform, you must reorganize the tree structure folders according to Adobe Campaign v6 norms. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

-->

<!--

* Interaction

  If you are migrating from Campaign v6.02 and using the  **Interaction** module, you must delete all 6.02 schema references that no longer exist in v7. [Learn more](../../migration/using/general-configurations.md#interaction)

-->

## 移轉後 {#after-the-migration}

執行後 **postugrade**，檢查並設定下列元素：

* 鏡像頁面

   鏡像頁面個人化區塊已隨v6.x變更。這個新版本可改善存取這些頁面時的安全性。

   如果您在訊息中使用v5個人化區塊，鏡像頁面顯示將會失敗。 Adobe強烈建議在訊息中插入鏡像頁面時，使用新的個人化區塊。

   不過，作為暫時的因應措施（且鏡像頁面仍為即時頁面），您可以回到舊的個人化區塊，透過變更選項來避免此問題 **[!UICONTROL XtkAcceptOldPasswords]** 並將其設定為 **[!UICONTROL 1]**. 這不會影響新v6.x個人化區塊的使用。

* 語法

   如果您遇到任何與語法相關的錯誤，在升級後期間，您必須暫時啟用 **allowSQLInjents** 選項 **serverConf.xml** 檔案，因為這能讓您有時間重寫程式碼。 調整程式碼後，請務必重新啟用安全性。

* 衝突

   移轉是透過升級後執行，而報表、表單或網頁應用程式中可能會出現衝突。 這些衝突可從主控台解決。

* Tomcat

   如果您自訂了安裝資料夾，請務必確認移轉後資料夾已正確更新。

* 報告

   現成可用的所有報表目前都使用v6.x轉譯引擎。 若您已將JavaScript程式碼新增至報表中，則某些元素可能會受到影響。

* Web應用程式

   升級後，如果您在連接到已識別的Web應用程式時遇到任何問題，則必須激活 **allowUserPassword** 和 **sessionTokenOnly** 選項 **serverConf.xml** 檔案。 為避免出現任何安全問題，在問題解決後，必須重新激活這兩個選項。

   您必鬚根據Web應用程式的類型及其配置執行其他操作，以確保它們正常工作。

<!--
  If migrating from a v5.11 platform, additional configurations must be carried out. [Learn more](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Security zones

  Before starting the server, you must configure the security zones. [Learn more](../../installation/using/security-zones.md) and [see here](../../migration/using/general-configurations.md#security)

-->

<!--

* Workflows

  If migrating from a v5.11 platform, you must check the workflows folder. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

-->

<!--

* Tracking

  If migrating from a v5.11 platform, you must configure the tracking mode. [Learn more](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

-->

* 互動

   如果您使用 **互動**，您必須在移轉後調整任何參數。

<!--

* Dashboards

  If a client error appears, you have to either update your dashboards with the new Adobe Campaign v7 code, or manually copy the following files from the v6.02 instance to the v7 instance:

  ```
  v6.02 files and spaces:
  /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
  /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
  v6.1 files and spaces:
  /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
  /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
  ```

-->

<!--

## Specific configurations from a v5.11 to v7{#specific-configurations-in-v5-11}



This section details the additional configuration required when migrating from v5.11. You should also configure the settings detailed in the [General configurations](../../migration/using/general-configurations.md) section.

### Web applications {#web-applications-v5}

The following warning will be displayed automatically during migration:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Some components of web applications, for instance the various formula fields, have @id attributes. These are used in the XML code of web applications and are no longer generated in the same way. They are not visible in the interface and you must not normally use them. However, in some cases, @id attributes may have been used to personalize the rendering of web applications, for instance via a stylesheet or using JavaScript code.

During migration, you **must** check the log file path specified in the warning:

* **The file is not empty**: it contains warnings which concern inconsistencies recorded before migration and which still exist. This can be JavaScript code in a web application which references a non-existent ID. Each error must be checked and corrected.
* **The file is empty**: this means that Adobe Campaign has not detected any issues.

Whether the file is empty or not, you must check that these IDs are not used for configuration elsewhere (and adapt configuration if this is the case).

### Workflows {#workflows}

Since the name of the Adobe Campaign installation directory has changed, some workflows may not work after the migration. If a workflow references the nl5 directory in one of its activities, this will raise an error. Replace this reference with **build**. You can run an SQL query to identify these workflows (PostgreSQL example):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL is only supported in v7 as the main database engine when migrating from version 6.02 or 5.11 using this engine.

MySQL does not manage timezones by default. To enable timezone management, run the following command:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>For more information, refer to the [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) page.

If modifications have been made to the database structure, during configuration for example (creating specific indexes, creating SQL views, etc.), certain precautions should be taken when migrating. Indeed, certain modifications can be generated from incompatibilities with the migration procedure. For example, creating SQL views containing **Timestamp** fields are not compatible with the **usetimestamptz** option. We therefore advise you to follow the recommendations below:

1. Before starting the migration, back up the database.
1. Delete SQL changes.
1. Perform the postupgrade
    >[!NOTE]
    >
    >You must follow the migration steps presented in [this section](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. Reintegrate SQL changes.

In this example, a **NmcTrackingLogMessages** view had been created and this has a **Timestamp** field named **tslog**. In this case, the migration procedure fails and the following error message appears:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

To make sure the postupgrade works, you must delete the view before the migration and re-create it after the migration while adapting it to the TIMESTAMP WITH TIMEZONE mode.

### Tracking {#tracking}

The tracking formula has been modified. When migrating, the old formula (v5) is replaced by the new one (v7). If you use a personalized formula in Adobe Campaign v5, this configuration has to be adapted in Adobe Campaign v7 (**NmsTracking_ClickFormula** and **NmsTracking_OpenFormula** options).

Web tracking management has also been modified. Once migration to v7 has been carried out, you must start the deployment wizard to finish configuring the web tracking.

  ![](assets/migration_web_tracking.png)

Three modes are available:

* **Session web tracking**: If the **[!UICONTROL Leads]** package has not been installed, this option is selected by default. This option is the most ideal in terms of performance and it allows you to limit the size of the tracking logs.
* **Permanent Web tracking**
* **Anonymous Web Tracking**: If the **[!UICONTROL Leads]** package is installed, this option is selected by default. It is the most resource-consuming option. As above, the **sSourceId** column must be indexed (in the tracking table and the **CrmIncomingLead** table).

>[!NOTE]
>
>For more information on these three modes, refer to [this section](../../configuration/using/about-web-tracking.md).

### Adobe Campaign v7 tree structure {#campaign-vseven-tree-structure}

During migration, the tree structure is automatically reorganized based on the v7 standards. The new folders are added, the obsolete folders are deleted, and their content is placed in the "To move" folder. All items in this folder must be checked after the migration, and the consultant has to decide to either keep it or delete each one. Items to be kept then have to be moved to the right place.

An option has been added for disabling the automatic migration of the navigation tree. This operation is now manual. Obsolete folders are not deleted and new folders are not added. This option should only be used if the out-of-the-box v5 navigation tree has undergone too many changes. Add the option to the console, before migrating, in the **[!UICONTROL Administration > Options]** node:

* Internal name: NlMigration_KeepFolderStructure
* Data type: Integer
* Value (text): 1

If you use this option, after migration you will have to delete obsolete folders, add the new folders and run all necessary checks.

**List of new folders**:

The following folders need to be added after the migration:

| Internal name | Label | Condition |
|---|---|---|
| nmsAutoObjects | Objects created automatically | - |
| nmsCampaignAdmin | Campaign management | - |
| nmsCampaignMgt | Campaign management | - |
| nmsCampaignRes | Campaign management | - |
| nmsModels | Templates | - |
| nmsOnlineRes | Online | - |
| nmsProduction | Production | - |
| nmsProfilProcess | Processes | - |
| xtkDashboard | Dashboards | - |
| xtkPlatformAdmin | Platform | - |
| nmsLocalOrgUnit | Organizational units | - |
| nmsMRM | MRM | MRM installed |
| nmsOperations | Campaigns | Campaign installed |

**List of obsolete folders**:

The obsolete folders to be deleted after the migration are as follows:

>[!NOTE]
>
>The entire content of the obsolete folders must be checked, and for each item the consultant decides whether to keep or delete it. The items to be kept must be moved to the appropriate place.

| Internal name | Label | Condition |
|---|---|---|
| nmsAdministration | Administration | - |
| nmsDeliveryMgt | Campaign execution | - |
| ncmContent | Content management | Content Manager installed |
| ncmForm | Input form | Content Manager installed |
| ncmImage | Images | Content Manager installed |
| ncmJavascript | JavaScript codes | Content Manager installed |
| ncmJst | JavaScript templates | Content Manager installed |
| ncmParameters | Configuration | Content Manager installed |
| ncmSrcSchema | Data schemas | Content Manager installed |
| ncmStylesheet | XSL style files | Content Manager installed |
| nmsAdminPlan | Administration | Campaign installed |
| nmsResourcePlan | Resources | Campaign installed |
| nmsResourcesModels | Templates | Campaign installed |
| nmsRootPlan | Campaign management | Campaign installed |
| nmsOperator | Marketing operators | MRM installed |


## Specific configurations from v6.02 to v7{#specific-configurations-in-v6-02}



The following section details the additional configuration required when migrating from v6.02. You should also configure the settings detailed in [this page](../../migration/using/general-configurations.md).

### Web applications {#web-applications-v6}

If you are migrating from v6.02, error logs regarding overview-type web applications may appear. Error message examples:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

These web applications used SQLData and are not compatible with v7, due to heightened security. These errors will lead to a migration failure.

If you didn't use these web applications, run the following cleanup script and rerun the postupgrade:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

If you have modified these web applications and would like to continue using them in v7, you must activate the **allowSQLInjection** option in your different security zones and re-start the postupgrade. Refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section for more on this.

### Message Center {#message-center}

After a Message Center control instance migration, you must republish the transactional message templates for them to work.

In v7, the names of transactional message templates on execution instances have changed. They are currently prefixed by the operator name that corresponds to the control instance on which they are created, for example **control1_template1_rt** (where **control1** is the name of the operator). If you have a significant volume of templates, we recommend deleting old templates on control instances.

-->