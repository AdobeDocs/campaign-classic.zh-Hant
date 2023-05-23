---
product: campaign
title: 透過 LDAP 連線
description: 瞭解如何使用LDAP登錄市場活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---

# 透過 LDAP 連線{#connecting-through-ldap}

## 配置市場活動和LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP配置僅可用於內部安裝或混合安裝。

LDAP配置在部署嚮導中執行。 的 **[!UICONTROL LDAP integration]** 選項。 請參閱 [部署嚮導](../../installation/using/deploying-an-instance.md#deployment-wizard)。

該窗口允許您通過指定的LDAP目錄配置Adobe Campaign用戶的標識。

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* 指定LDAP伺服器的地址 **[!UICONTROL LDAP server]** 的子菜單。 可以添加埠號。 預設情況下，使用的埠為389。
* 在下拉清單中，為用戶選擇身份驗證方法：

   * 加密密碼(**md5**)

      預設模式。

   * 純文字檔案密碼+ SSL(**TLS**)

      整個驗證過程（包括密碼）被加密。 安全埠636不能在此模式下使用：Adobe Campaign自動切換到安全模式。

      使用此身份驗證模式時，在Linux中，證書由openLDAP客戶端庫驗證。 我們建議使用有效的SSL證書，以便對身份驗證過程進行加密。 否則，資訊將以純文字檔案形式顯示。

      證書也在Windows中驗證。

   * Windows NT LAN管理器(**NTLM**)

      專有的Windows身份驗證。 的 **[!UICONTROL Unique identifier]** 僅用於域名。

   * 分佈式密碼驗證(**德新**)

      專有的Windows身份驗證。 的 **[!UICONTROL Unique identifier]** 僅用於域名(domain.com)。

   * 純文字密碼

      無加密(僅用於test階段)。

* 選擇用戶身份驗證模式： **[!UICONTROL Automatically compute the unique user identifier]** （請參閱步驟） [可分辨名稱計算](#distinguished-name-calculation))或 **[!UICONTROL Search the unique user identifier in the directory]** （請參閱步驟） [搜索標識符](#searching-for-identifiers))。

## 相容性 {#compatibility}

相容的系統取決於選定的身份驗證機制。 以下是作業系統和LDAP伺服器的相容性矩陣。

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

## 可分辨名稱計算 {#distinguished-name-calculation}

如果要計算可分辨名稱(DN)標識符，則部署嚮導的下一步允許您配置計算模式。

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* 在中的目錄（可分辨名稱 — DN）中指定用戶的唯一標識符 **[!UICONTROL Distinguished Name]** 的子菜單。

   **[!UICONTROL (login)]** 將替換為Adobe Campaign運算子的標識符。

   >[!CAUTION]
   >
   >的 **[!UICONTROL dc]** 設定必須為小寫。

* 選擇選項 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 以便同步LDAP目錄中的組和用戶關聯以及Adobe Campaign的組和用戶關聯。

   選擇此選項時， **[!UICONTROL Application level DN used for the search]** 和 **[!UICONTROL Password of the application login]** 的子菜單。

   如果填充這兩個欄位，Adobe Campaign將使用其自己的登錄名和密碼連接到LDAP伺服器。 如果它們為空，Adobe Campaign將匿名連接到伺服器。

## 搜索標識符 {#searching-for-identifiers}

如果選擇搜索標識符，則部署嚮導允許您配置搜索。

* 在 **[!UICONTROL Application level DN used for the search]** 和 **[!UICONTROL Password of the application login]** 欄位中，提供標識符和密碼，Adobe Campaign將連接這些標識符以搜索該標識符。 如果它們為空，Adobe Campaign將匿名連接到伺服器。
* 指定 **[!UICONTROL Base identifier]** 和 **[!UICONTROL Search scope]** 以確定要從中開始搜索的LDAP目錄的子集。

   在下拉清單中選擇所需模式：

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**。

      從給定級別開始，將完整搜索LDAP目錄。

   1. **[!UICONTROL Limited to the base]**.

      搜索中包含所有屬性。

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      搜索從該屬性的第一級開始，對該目錄的所有屬性執行。

* 的 **[!UICONTROL Filter]** 欄位中，您可以指定元素來細化搜索範圍。

## 配置LDAP授權 {#configuring-ldap-authorizations}

當您選擇 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 的雙曲餘切值。

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

必須指定多個參數才能查找用戶所屬的組及其相應權限，即：

* 這樣 **[!UICONTROL Database identifier]** 欄位，
* 這樣 **[!UICONTROL Search scope]** 欄位，

   >[!NOTE]
   >
   >如果已選擇搜索DN，則可以選擇 **[!UICONTROL Reuse the DN search parameters]** 以便從上一個螢幕中繼承DN和搜索範圍的選定值。

* 這樣 **[!UICONTROL Rights search filter]** 欄位，根據登錄名和用戶的可分辨名稱，
* 這樣 **[!UICONTROL Attribute containing the group or authorization name]** 欄位，
* 這樣 **[!UICONTROL Association mask]** 啟用在Adobe Campaign中提取組名稱及其相關權限的欄位。 可以使用規則運算式搜索名稱。
* 選擇 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 以便用戶自動被授予連接訪問權限。

按一下 **[!UICONTROL Save]** 完成實例的配置。

## 管理運算子 {#managing-operators}

確認配置後，必須定義通過LDAP目錄管理哪些Adobe Campaign運算子。

要使用LDAP目錄驗證操作員，請編輯相應的配置檔案，然後按一下 **[!UICONTROL Edit the access parameters]** 的子菜單。 選擇 **[!UICONTROL Use LDAP for authentication]** 選項：的 **[!UICONTROL Password]** 欄位對此運算子呈灰色。

![](assets/s_ncs_install_operator_in_ldap.png)

## 使用案例 {#use-cases}

本節提供了一些簡單的使用案例，幫助您根據需要實現最合適的配置。

1. 已在LDAP目錄中建立用戶，但未在Adobe Campaign。

   可以配置Adobe Campaign，以便用戶通過其LDAP驗證訪問平台。 Adobe Campaign需要能夠控制LDAP目錄中ID/密碼組合的有效性，以便在Adobe Campaign即時建立操作員。 要執行此操作，請檢查 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 的雙曲餘切值。 在這種情況下，還需要配置組同步：這樣 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 選項。

1. 用戶已在Adobe Campaign建立，但未在LDAP目錄中建立。

   他們無法登錄Adobe Campaign。

1. LDAP目錄中有一個組在Adobe Campaign中不存在。

   此組不會在Adobe Campaign建立。 您需要建立組並同步組，以通過 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 的雙曲餘切值。

1. 組存在於Adobe Campaign，事件發生後將激活LDAP目錄：Adobe Campaign的用戶組不會自動替換為LDAP組的內容。 同樣，如果組僅存在於Adobe Campaign，則在LDAP中建立並同步組之前，不能將LDAP用戶添加到該組。

   組從不是通過Adobe Campaign或LDAP動態建立的。 需要在Adobe Campaign和LDAP目錄中分別建立它們。

   LDAP目錄中的組名稱需要與Adobe Campaign組的名稱一致。 它們的關聯掩碼是在部署嚮導的最後配置階段定義的：Adobe Campaign_()&#42;)，例如。
