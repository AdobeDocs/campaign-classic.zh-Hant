---
product: campaign
title: 透過 LDAP 連線
description: 瞭解如何使用LDAP登入Campaign
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 2%

---

# 透過 LDAP 連線{#connecting-through-ldap}

## 設定Campaign和LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP設定僅適用於內部部署或混合式安裝。

LDAP設定會在部署精靈中執行。 此 **[!UICONTROL LDAP integration]** 選項必須在第一個組態步驟中選取。 請參閱 [部署精靈](../../installation/using/deploying-an-instance.md#deployment-wizard).

視窗可讓您透過指定的LDAP目錄設定Adobe Campaign使用者的身分識別。

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* 請在中指定LDAP伺服器的位址 **[!UICONTROL LDAP server]** 欄位。 您可以新增連線埠號碼。 依預設，使用的連線埠為389。
* 在下拉式清單中，選取使用者的驗證方法：

   * 加密的密碼(**md5**)

     預設模式。

   * 純文字密碼+ SSL (**TLS**)

     整個驗證程式（包括密碼）都會加密。 安全連線埠636不可在此模式中使用： Adobe Campaign會自動切換至安全模式。

     當您使用此驗證模式時，在Linux中，憑證會由openLDAP使用者端程式庫驗證。 建議您使用有效的SSL憑證，以便加密驗證程式。 否則，資訊將以純文字顯示。

     憑證也會在Windows中驗證。

   * Windows NT LAN管理員(**NTLM**)

     專屬Windows驗證。 此 **[!UICONTROL Unique identifier]** 僅用於網域名稱。

   * 分散式密碼驗證(**DPA**)

     專屬Windows驗證。 此 **[!UICONTROL Unique identifier]** 僅用於網域名稱(domain.com)。

   * 純文字密碼

     無加密（僅供測試階段使用）。

* 選取使用者驗證模式： **[!UICONTROL Automatically compute the unique user identifier]** （請參閱步驟） [辨別名稱計算](#distinguished-name-calculation))或 **[!UICONTROL Search the unique user identifier in the directory]** （請參閱步驟） [搜尋識別碼](#searching-for-identifiers))。

## 相容性 {#compatibility}

相容的系統取決於選取的驗證機制。 以下是作業系統與LDAP伺服器的相容性矩陣。

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> 主動式目錄<br /> </th> 
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
   <td> NTLM與DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> 純文字<br /> </td> 
   <td> Windows、Linux<br /> </td> 
   <td> Windows、Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 辨別名稱計算 {#distinguished-name-calculation}

如果您要計算「辨別名稱(DN)」識別碼，部署精靈的下一個步驟可讓您設定計算模式。

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* 在的目錄指定使用者的唯一識別碼（辨別名稱 — DN）。 **[!UICONTROL Distinguished Name]** 欄位。

  **[!UICONTROL (login)]** 將以Adobe Campaign運運算元的識別碼取代。

  >[!CAUTION]
  >
  >此 **[!UICONTROL dc]** 設定必須為小寫。

* 選取選項 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 以同步LDAP目錄中的群組和使用者關聯，以及Adobe Campaign中的群組和使用者關聯。

  選取此選項時， **[!UICONTROL Application level DN used for the search]** 和 **[!UICONTROL Password of the application login]** 已啟用。

  如果您填入這兩個欄位，Adobe Campaign將使用自己的登入和密碼連線到LDAP伺服器。 如果兩者空白，Adobe Campaign將以匿名方式連線至伺服器。

## 搜尋識別碼 {#searching-for-identifiers}

如果您選擇搜尋識別碼，部署精靈可讓您設定搜尋。

* 在 **[!UICONTROL Application level DN used for the search]** 和 **[!UICONTROL Password of the application login]** 欄位中，輸入Adobe Campaign用來連線以搜尋識別碼的識別碼和密碼。 如果兩者空白，Adobe Campaign將以匿名方式連線至伺服器。
* 指定 **[!UICONTROL Base identifier]** 和 **[!UICONTROL Search scope]** 欄位，以判斷要開始搜尋的LDAP目錄子集。

  在下拉式清單中選取所需的模式：

  ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      會從指定的層級開始完整搜尋LDAP目錄。

   1. **[!UICONTROL Limited to the base]**.

      所有屬性都包含在搜尋中。

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      對目錄的所有屬性執行搜尋，並從屬性的第一層級開始。

* 此 **[!UICONTROL Filter]** 欄位可讓您指定元素來縮小搜尋的範圍。

## 設定LDAP授權 {#configuring-ldap-authorizations}

當您選取 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 選項。

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

您必須指定數個引數，才能尋找使用者所屬的一個或多個群組及其對應的許可權，例如：

* 此 **[!UICONTROL Database identifier]** 欄位，
* 此 **[!UICONTROL Search scope]** 欄位，

  >[!NOTE]
  >
  >如果您已選擇搜尋DN，可以選取 **[!UICONTROL Reuse the DN search parameters]** 以延續先前畫面中為DN和搜尋範圍選取的值。

* 此 **[!UICONTROL Rights search filter]** 欄位，根據登入和使用者的辨別名稱，
* 此 **[!UICONTROL Attribute containing the group or authorization name]** 有關使用者的欄位，
* 此 **[!UICONTROL Association mask]** 欄位，用於在Adobe Campaign中擷取群組名稱及其相關許可權。 您可以使用規則運算式來搜尋名稱。
* 選取 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 這樣就會自動授予使用者連線的存取權。

按一下 **[!UICONTROL Save]** 以完成例項的設定。

## 管理運運算元 {#managing-operators}

確認設定後，您必須定義透過LDAP目錄管理哪些Adobe Campaign運運算元。

若要使用LDAP目錄來驗證運運算元，請編輯對應的設定檔，然後按一下 **[!UICONTROL Edit the access parameters]** 連結。 選取 **[!UICONTROL Use LDAP for authentication]** 選項： **[!UICONTROL Password]** 此運運算元的欄位會變成灰色。

![](assets/s_ncs_install_operator_in_ldap.png)

## 使用案例 {#use-cases}

本節提供幾個簡單的使用案例，協助您根據需求達成最適當的設定。

1. 已在LDAP目錄中建立使用者，但未在Adobe Campaign中建立。

   可以設定Adobe Campaign，讓使用者透過其LDAP驗證存取平台。 Adobe Campaign需要能夠控制LDAP目錄中ID/密碼組合的有效性，以便在Adobe Campaign中即時建立運運算元。 要執行此操作，請核取 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 選項。 在此情況下，也需要設定群組同步： **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 選項。

1. 使用者已在Adobe Campaign中建立，但未在LDAP目錄中建立。

   他們將無法登入Adobe Campaign。

1. LDAP目錄中的群組不存在於Adobe Campaign中。

   此群組不會在Adobe Campaign中建立。 您需要建立群組並同步群組，以透過 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 選項。

1. 群組存在於Adobe Campaign中，且LDAP目錄在事件後啟動： Adobe Campaign中的使用者群組不會自動取代為LDAP群組的內容。 同樣地，如果群組僅存在於Adobe Campaign中，則只有在群組在LDAP中建立並同步化後，才能新增LDAP使用者。

   無論透過Adobe Campaign還是LDAP，群組都不會即時建立。 兩者都需要在Adobe Campaign和LDAP目錄中個別建立。

   LDAP目錄中的群組名稱必須與Adobe Campaign群組的名稱一致。 其關聯遮罩定義於部署精靈的最後設定階段：Adobe Campaign_(。&#42;)，例如。
