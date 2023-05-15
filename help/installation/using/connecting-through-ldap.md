---
product: campaign
title: 透過 LDAP 連線
description: 了解如何使用LDAP登入Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: e011333411af79b985166a4e73592a1860749cf1
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---

# 透過 LDAP 連線{#connecting-through-ldap}

## 設定促銷活動和LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP設定僅可用於內部部署或混合安裝。

LDAP配置在部署嚮導中執行。 此 **[!UICONTROL LDAP integration]** 選項。 請參閱 [部署嚮導](../../installation/using/deploying-an-instance.md#deployment-wizard).

此視窗可讓您透過指定的LDAP目錄來設定Adobe Campaign使用者的身分識別。

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* 在 **[!UICONTROL LDAP server]** 欄位。 可以添加埠號。 預設情況下，使用的埠為389。
* 在下拉式清單中，選取使用者的驗證方法：

   * 加密密碼(**md5**)

      預設模式。

   * 純文字密碼+ SSL(**TLS**)

      對整個驗證過程（包括密碼）進行加密。 安全埠636不得在此模式下使用：Adobe Campaign會自動切換至安全模式。

      使用此身份驗證模式時，在Linux中，證書由openLDAP客戶端庫驗證。 建議您使用有效的SSL憑證，以加密驗證程式。 否則，資訊將以純文字檔案形式顯示。

      憑證也會在Windows中驗證。

   * Windows NT LAN管理器(**NTLM**)

      專有的Windows身份驗證。 此 **[!UICONTROL Unique identifier]** 僅用於網域名稱。

   * 分佈式密碼驗證(**DPA**)

      專有的Windows身份驗證。 此 **[!UICONTROL Unique identifier]** 僅用於域名(domain.com)。

   * 純文字密碼

      無加密（僅用於測試階段）。

* 選擇用戶身份驗證模式： **[!UICONTROL Automatically compute the unique user identifier]** （請參閱步驟） [可分辨名稱計算](#distinguished-name-calculation))或 **[!UICONTROL Search the unique user identifier in the directory]** （請參閱步驟） [搜尋識別碼](#searching-for-identifiers))。

## 相容性 {#compatibility}

相容的系統取決於所選的驗證機制。 以下是作業系統和LDAP伺服器的相容性矩陣。

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
   <td> 純文字<br /> </td> 
   <td> Windows、Linux<br /> </td> 
   <td> Windows、Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 可分辨名稱計算 {#distinguished-name-calculation}

如果要計算可分辨名稱(DN)標識符，則部署嚮導的下一步允許您配置計算模式。

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* 在 **[!UICONTROL Distinguished Name]** 欄位。

   **[!UICONTROL (login)]** 將會取代為Adobe Campaign運算子的識別碼。

   >[!CAUTION]
   >
   >此 **[!UICONTROL dc]** 設定必須為小寫。

* 選取選項 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 以便同步LDAP目錄中的組和用戶關聯，以及Adobe Campaign中的組和用戶關聯。

   選取此選項時， **[!UICONTROL Application level DN used for the search]** 和 **[!UICONTROL Password of the application login]** 的URL區段。

   如果填入這兩個欄位，Adobe Campaign會使用自己的登入和密碼連線至LDAP伺服器。 如果空白，Adobe Campaign會以匿名方式連線至伺服器。

## 搜尋識別碼 {#searching-for-identifiers}

如果您選擇搜尋識別碼，部署精靈可讓您設定搜尋。

* 在 **[!UICONTROL Application level DN used for the search]** 和 **[!UICONTROL Password of the application login]** 欄位，提供Adobe Campaign將用來搜尋識別碼的識別碼和密碼。 如果空白，Adobe Campaign會以匿名方式連線至伺服器。
* 指定 **[!UICONTROL Base identifier]** 和 **[!UICONTROL Search scope]** 欄位，以確定要從中開始搜索的LDAP目錄的子集。

   在下拉式清單中選取所需模式：

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      從給定級別開始，將以完整方式搜索LDAP目錄。

   1. **[!UICONTROL Limited to the base]**.

      所有屬性都包含在搜尋中。

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      從屬性的第一級開始，對目錄的所有屬性執行搜索。

* 此 **[!UICONTROL Filter]** 欄位可讓您指定元素以縮小搜尋範圍。

## 配置LDAP授權 {#configuring-ldap-authorizations}

選取 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 選項。

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

您必須指定數個參數，才能尋找使用者所屬的群組或群組及其對應權限，例如：

* the **[!UICONTROL Database identifier]** 欄位，
* the **[!UICONTROL Search scope]** 欄位，

   >[!NOTE]
   >
   >如果已選擇搜索DN，則可以選擇 **[!UICONTROL Reuse the DN search parameters]** 以便從上一個螢幕中繼續為DN和搜索範圍選擇的值。

* the **[!UICONTROL Rights search filter]** 欄位，根據登錄名和用戶的可分辨名稱，
* the **[!UICONTROL Attribute containing the group or authorization name]** 欄位，
* the **[!UICONTROL Association mask]** 欄位，以在Adobe Campaign中擷取群組名稱及其相關權限。 您可以使用規則運算式來搜尋名稱。
* 選擇 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 以便自動授予用戶連接的訪問權限。

按一下 **[!UICONTROL Save]** 完成執行個體的設定。

## 管理運算子 {#managing-operators}

確認配置後，必須定義哪些Adobe Campaign運算子是通過LDAP目錄管理的。

要使用LDAP目錄驗證運算子，請編輯相應的配置檔案，然後按一下 **[!UICONTROL Edit the access parameters]** 連結。 選取 **[!UICONTROL Use LDAP for authentication]** 選項：此 **[!UICONTROL Password]** 欄位對此運算子呈灰色。

![](assets/s_ncs_install_operator_in_ldap.png)

## 使用案例 {#use-cases}

本節提供一些簡單的使用案例，協助您根據需求完成最適當的設定。

1. 已在LDAP目錄中建立用戶，但未在Adobe Campaign中建立。

   可設定Adobe Campaign，讓使用者透過其LDAP驗證存取平台。 Adobe Campaign必須能夠控制LDAP目錄中ID/密碼組合的有效性，以便在Adobe Campaign中即時建立運算子。 若要這麼做，請檢查 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 選項。 在這種情況下，還需要配置組同步：the **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 選項。

1. 使用者已在Adobe Campaign中建立，但未在LDAP目錄中建立。

   他們無法登入Adobe Campaign。

1. LDAP目錄中有一個組，該組在Adobe Campaign中不存在。

   此群組不會在Adobe Campaign中建立。 您需要建立群組並同步群組，才能透過 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 選項。

1. 群組存在於Adobe Campaign中，且LDAP目錄會在事件後啟動：Adobe Campaign中的使用者群組不會自動取代為LDAP群組的內容。 同樣，如果組僅存在於Adobe Campaign中，則不可向其添加LDAP用戶，直到在LDAP中建立並同步該組。

   不論是由Adobe Campaign或LDAP即時建立群組。 這些檔案需要分別在Adobe Campaign和LDAP目錄中建立。

   LDAP目錄中的群組名稱必須與Adobe Campaign群組的名稱一致。 其關聯掩碼在部署嚮導的最後一個配置階段中定義：Adobe Campaign_(.&#42;)，例如。
