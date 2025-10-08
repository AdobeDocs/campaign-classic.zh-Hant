---
product: campaign
title: 開始使用權限
description: 瞭解如何授與Campaign功能的存取權
badge: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 34f875f583dd81c2229b66f3344f23965532e802
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 8%

---

# 開始使用權限{#access-management}


>[!CAUTION]
>
>從Campaign Classic v7.3.1開始，所有操作員都應使用[Adobe Identity Management System (IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}連線至Campaign。
>
>為了強化安全性和驗證程式，Adobe Campaign強烈建議您將所有現有的操作員驗證模式從登入/密碼原生驗證移轉至Adobe Identity Management系統(IMS)。 在[此頁面](../../technotes/using/migrate-users-to-ims.md)中瞭解如何移轉您的操作員。
> 
>移轉後，請注意下一節不再適用。  在[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=zh-Hant){target="_blank"}中瞭解如何使用Adobe IMS設定許可權。


Adobe Campaign可讓您定義並管理指派給各種運運算元的許可權。 這些是一組授權或拒絕的許可權和限制：

* 存取特定功能（透過已命名的許可權），
* 存取特定記錄，
* 建立、修改及/或刪除記錄（動作、連絡人、行銷活動、群組等）。

>[!BEGINTABS]

>[!TAB 許可權檔案]

若要進一步瞭解Adobe Campaign **中的**&#x200B;許可權，請參閱&#x200B;**[Campaign v8 （主控台）檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}**。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}


>[!TAB 管理檔案夾的許可權]

若要瞭解如何定義資料夾&#x200B;**的**&#x200B;許可權，請參閱&#x200B;**[Campaign v8 （主控台）檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}**。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}


>[!TAB 原生驗證]

Campaign v7仍可使用登入/密碼的原生驗證，但為了強化安全性和驗證程式，Adobe Campaign強烈建議[將一般使用者驗證模式](../../technotes/using/ac-ims.md)從登入/密碼原生驗證移轉到Adobe Identity Management系統(IMS)。 請注意，在Campaign v8中，不允許連線使用者/密碼（亦稱為原生驗證）。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](../../technotes/using/ac-ims.md)


>[!ENDTABS]



<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](access-management-named-rights.md).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](access-management-named-rights.md)

* [Manage Campaign folder access](access-management-folders.md)

* [Access rights matrix](access-management-named-rights.md#access-rights-matrix)


See also:

* [Manage permissions for workflows](../../workflow/using/managing-rights.md)
* [Manage permissions for distributed marketing](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Manage permissions for the interaction module](../../interaction/using/operator-profiles.md)
* [Filter access to schemas](../../configuration/using/filtering-schemas.md)
* [Restricting PI view](../../configuration/using/restricting-pii-view.md)
-->