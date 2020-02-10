---
title: 通過LDAP連接
seo-title: 通過LDAP連接
description: 通過LDAP連接
seo-description: null
page-status-flag: never-activated
uuid: 13a426bc-7c34-49e5-ac8e-26d830845f28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1563db7c-ccb6-46b3-9299-67ec0aedaca0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 通過LDAP連接{#connecting-through-ldap}

## 設定促銷活動和LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP配置僅可用於內部部署或混合安裝。

LDAP配置在部署嚮導中執行。 在第 **[!UICONTROL LDAP integration]** 一個配置步驟中必須選擇該選項。 請參閱部 [署精靈](../../installation/using/deploying-an-instance.md#deployment-wizard)。

此視窗可讓您透過指定的LDAP目錄來設定Adobe Campaign使用者的識別碼。

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Specify the address of the LDAP server in the **[!UICONTROL LDAP server]** field. 您可以添加埠號。 預設情況下，使用的埠為389。
* 在下拉式清單中，選取使用者的驗證方法：

   * 加密密碼(**md5**)

      預設模式。

   * 純文字密碼+ SSL(**TLS**)

      整個驗證過程（包括密碼）都經過加密。 安全埠636不能在此模式下使用：Adobe Campaign會自動切換至安全模式。

      使用此驗證模式時，在Linux中，證書由openLDAP客戶端庫驗證。 我們建議使用有效的SSL憑證，以便加密驗證程式。 否則，資訊將會以純文字顯示。

      此憑證也會在Windows中驗證。

   * Windows NT LAN Manager(**NTLM**)

      專有的Windows驗證。 僅 **[!UICONTROL Unique identifier]** 用於域名。

   * 分佈式密碼驗&#x200B;**證(DPA**)

      專有的Windows驗證。 僅 **[!UICONTROL Unique identifier]** 用於域名(domain.com)。

   * 純文字密碼

      無加密（僅用於測試階段）。

* 選擇用戶驗證模式： **[!UICONTROL Automatically compute the unique user identifier]** (請參 [閱步驟Distinguished Name calculation](#distinguished-name-calculation))或 **[!UICONTROL Search the unique user identifier in the directory]** (請參閱 [步驟Searching for identifiers](#searching-for-identifiers))。

## 相容性 {#compatibility}

相容的系統取決於所選的身份驗證機制。 以下是作業系統和LDAP伺服器的相容性清單。

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> Active Directory<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows、Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows、Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM和DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> 純文字檔案<br /> </td> 
   <td> Windows、Linux<br /> </td> 
   <td> Windows、Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 唯一判別名計算 {#distinguished-name-calculation}

如果要計算唯一判別名(DN)標識符，則部署嚮導的下一步將允許您配置計算模式。

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* 在欄位的目錄中指定用戶的唯一標識符（標識名- DN）。 **[!UICONTROL Distinguished Name]**

   **[!UICONTROL (login)]** 將會以Adobe Campaign運算子的識別碼取代。

   >[!CAUTION]
   >
   >設 **[!UICONTROL dc]** 定必須為小寫。

* 選取此選 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 項，以同步LDAP目錄中的群組和使用者關聯，以及Adobe Campaign中的群組和使用者關聯。

   當您選取此選項時， **[!UICONTROL Application level DN used for the search]** 和 **[!UICONTROL Password of the application login]** 會啟用。

   如果您填入這兩個欄位，Adobe Campaign將會使用其登入名稱和密碼連線至LDAP伺服器。 如果是空的，Adobe Campaign會匿名連線至伺服器。

## 搜索標識符 {#searching-for-identifiers}

如果您選擇搜尋識別碼，部署精靈可讓您設定搜尋。

* 在和欄 **[!UICONTROL Application level DN used for the search]** 位 **[!UICONTROL Password of the application login]** 中，提供Adobe Campaign用來搜尋識別碼的識別碼和密碼。 如果是空的，Adobe Campaign會匿名連線至伺服器。
* 指定 **[!UICONTROL Base identifier]** 和字 **[!UICONTROL Search scope]** 段，以確定要開始搜索的LDAP目錄子集。

   在下拉式清單中選取所需模式：

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      從給定級別開始，將完整搜索LDAP目錄。

   1. **[!UICONTROL Limited to the base]**.

      所有屬性都包含在搜尋中。

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      搜索從屬性的第一級開始對目錄的所有屬性執行。

* 欄位 **[!UICONTROL Filter]** 可讓您指定元素以調整搜尋範圍。

## 配置LDAP授權 {#configuring-ldap-authorizations}

當您選取選項時，會顯示此 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 視窗。

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

您必須指定數個參數，才能查找用戶所屬的組或組及其相應權限，即：

* 欄 **[!UICONTROL Database identifier]** 位，
* 欄 **[!UICONTROL Search scope]** 位，

   >[!NOTE]
   >
   >如果您選擇搜索DN，則可以選 **[!UICONTROL Reuse the DN search parameters]** 擇，以便從上一個螢幕中保留選定的DN值和搜索範圍。

* 根據 **[!UICONTROL Rights search filter]** 登錄名和用戶的標識名，
* 關於 **[!UICONTROL Attribute containing the group or authorization name]** 用戶的欄位，
* 此欄 **[!UICONTROL Association mask]** 位可在Adobe Campaign中擷取群組名稱及其相關權限。 您可以使用規則運算式來搜尋名稱。
* 選擇 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 此選項，以便用戶在連接時自動獲得訪問權限。

按一 **[!UICONTROL Save]** 下以完成執行個體的設定。

## 管理營運商 {#managing-operators}

確認設定後，您必須定義哪些Adobe Campaign運算子是透過LDAP目錄管理的。

要使用LDAP目錄來驗證操作員，請編輯相應的配置檔案並按一下該 **[!UICONTROL Edit the access parameters]** 連結。 選擇選 **[!UICONTROL Use LDAP for authentication]** 項：此運 **[!UICONTROL Password]** 算子的欄位會變灰。

![](assets/s_ncs_install_operator_in_ldap.png)

## 使用案例 {#use-cases}

本節提供一些簡單的使用案例，幫助您根據需要實現最合適的配置。

1. 已在LDAP目錄中建立使用者，但未在Adobe Campaign中建立。

   Adobe Campaign可以設定，讓使用者透過其LDAP驗證存取平台。 Adobe Campaign必須能夠控制LDAP目錄中ID/密碼組合的有效性，以便在Adobe Campaign中即時建立運算元。 若要這麼做，請勾選 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 選項。 在這種情況下，還需要配置組同步：需 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 要選取選項。

1. 使用者已在Adobe Campaign中建立，但未在LDAP目錄中建立。

   他們將無法登入Adobe Campaign。

1. LDAP目錄中有一個Adobe Campaign中不存在的群組。

   此群組不會在Adobe Campaign中建立。 您需要建立群組並同步這些群組，才能透過選項啟用比 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 對。

1. 群組存在於Adobe Campaign中，且LDAP目錄會在事件發生後啟動：Adobe Campaign中的使用者群組不會自動取代為LDAP群組的內容。 同樣地，如果群組僅存在於Adobe Campaign中，則在LDAP中建立並同步群組之前，不得將LDAP使用者新增至該群組。

   不論是透過Adobe Campaign或LDAP，都不會即時建立群組。 這些項目必須在Adobe Campaign和LDAP目錄中個別建立。

   LDAP目錄中的群組名稱必須與Adobe Campaign群組的名稱一致。 其關聯掩碼在部署嚮導的最後一個配置階段中定義：Adobe Campaign_(.*)。

