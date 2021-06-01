---
product: campaign
title: 透過 LDAP 連線
description: '了解如何使用LDAP登入Campaign '
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 0%

---

# 透過 LDAP 連線{#connecting-through-ldap}

## 配置促銷活動和LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP設定僅可用於內部部署或混合安裝。

LDAP配置在部署嚮導中執行。 在第一個配置步驟中必須選擇&#x200B;**[!UICONTROL LDAP integration]**&#x200B;選項。 請參閱[部署嚮導](../../installation/using/deploying-an-instance.md#deployment-wizard)。

此視窗可讓您透過指定的LDAP目錄來設定Adobe Campaign使用者的身分識別。

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* 在&#x200B;**[!UICONTROL LDAP server]**&#x200B;欄位中指定LDAP伺服器的地址。 可以添加埠號。 預設情況下，使用的埠為389。
* 在下拉式清單中，選取使用者的驗證方法：

   * 加密密碼(**md5**)

      預設模式。

   * 純文字密碼+ SSL(**TLS**)

      對整個驗證過程（包括密碼）進行加密。 安全埠636不得在此模式下使用：Adobe Campaign會自動切換至安全模式。

      使用此身份驗證模式時，在Linux中，證書由openLDAP客戶端庫驗證。 建議您使用有效的SSL憑證，以加密驗證程式。 否則，資訊將以純文字檔案形式顯示。

      憑證也會在Windows中驗證。

   * Windows NT LAN管理器(**NTLM**)

      專有的Windows身份驗證。 **[!UICONTROL Unique identifier]**&#x200B;僅用於域名。

   * 分佈式密碼驗證(**DPA**)

      專有的Windows身份驗證。 **[!UICONTROL Unique identifier]**&#x200B;僅用於域名(domain.com)。

   * 純文字密碼

      無加密（僅用於測試階段）。

* 選擇用戶身份驗證模式：**[!UICONTROL Automatically compute the unique user identifier]**（請參閱步驟[可分辨名稱計算](#distinguished-name-calculation)）或&#x200B;**[!UICONTROL Search the unique user identifier in the directory]**（請參閱步驟[搜索標識符](#searching-for-identifiers)）。

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
   <td> Windows, Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM和DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> 純文字<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 可分辨名稱計算{#distinguished-name-calculation}

如果要計算可分辨名稱(DN)標識符，則部署嚮導的下一步允許您配置計算模式。

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* 在&#x200B;**[!UICONTROL Distinguished Name]**&#x200B;欄位的目錄（可分辨名稱 — DN）中指定用戶的唯一標識符。

   **[!UICONTROL (login)]** 將會取代為Adobe Campaign運算子的識別碼。

   >[!CAUTION]
   >
   >**[!UICONTROL dc]**&#x200B;設定必須為小寫。

* 選擇&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;選項，以便同步LDAP目錄中的組和用戶關聯以及Adobe Campaign中的組和用戶關聯。

   選擇此選項時，將啟用&#x200B;**[!UICONTROL Application level DN used for the search]**&#x200B;和&#x200B;**[!UICONTROL Password of the application login]**。

   如果填入這兩個欄位，Adobe Campaign會使用自己的登入和密碼連線至LDAP伺服器。 如果空白，Adobe Campaign會以匿名方式連線至伺服器。

## 搜索標識符{#searching-for-identifiers}

如果您選擇搜尋識別碼，部署精靈可讓您設定搜尋。

* 在&#x200B;**[!UICONTROL Application level DN used for the search]**&#x200B;和&#x200B;**[!UICONTROL Password of the application login]**&#x200B;欄位中，提供Adobe Campaign將連線以搜尋識別碼的識別碼和密碼。 如果空白，Adobe Campaign會以匿名方式連線至伺服器。
* 指定&#x200B;**[!UICONTROL Base identifier]**&#x200B;和&#x200B;**[!UICONTROL Search scope]**&#x200B;欄位，以確定要開始搜索的LDAP目錄的子集。

   在下拉式清單中選取所需模式：

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      從給定級別開始，將以完整方式搜索LDAP目錄。

   1. **[!UICONTROL Limited to the base]**.

      所有屬性都包含在搜尋中。

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      從屬性的第一級開始，對目錄的所有屬性執行搜索。

* **[!UICONTROL Filter]**&#x200B;欄位可讓您指定元素以縮小搜尋範圍。

## 配置LDAP授權{#configuring-ldap-authorizations}

選擇&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;選項時，將顯示此窗口。

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

您必須指定數個參數，才能尋找使用者所屬的群組或群組及其對應權限，例如：

* **[!UICONTROL Database identifier]**&#x200B;欄位，
* **[!UICONTROL Search scope]**&#x200B;欄位，

   >[!NOTE]
   >
   >如果已選擇搜索DN，則可以選擇&#x200B;**[!UICONTROL Reuse the DN search parameters]**&#x200B;以從上一螢幕中繼承所選的DN值和搜索範圍。

* **[!UICONTROL Rights search filter]**&#x200B;欄位，根據登錄名和用戶的可分辨名稱，
* 關於用戶的&#x200B;**[!UICONTROL Attribute containing the group or authorization name]**&#x200B;欄位，
* **[!UICONTROL Association mask]**&#x200B;欄位，啟用提取Adobe Campaign中的群組名稱及其相關權限。 您可以使用規則運算式來搜尋名稱。
* 選擇&#x200B;**[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**&#x200B;以便在連接時自動授予用戶訪問權限。

按一下&#x200B;**[!UICONTROL Save]**&#x200B;以完成執行個體的設定。

## 管理運算子{#managing-operators}

確認配置後，必須定義哪些Adobe Campaign運算子是通過LDAP目錄管理的。

要使用LDAP目錄驗證運算子，請編輯相應的配置檔案，然後按一下&#x200B;**[!UICONTROL Edit the access parameters]**&#x200B;連結。 選擇&#x200B;**[!UICONTROL Use LDAP for authentication]**&#x200B;選項：此運算子的&#x200B;**[!UICONTROL Password]**&#x200B;欄位會變灰。

![](assets/s_ncs_install_operator_in_ldap.png)

## 使用實例 {#use-cases}

本節提供一些簡單的使用案例，協助您根據需求完成最適當的設定。

1. 已在LDAP目錄中建立用戶，但未在Adobe Campaign中建立。

   可設定Adobe Campaign，讓使用者透過其LDAP驗證存取平台。 Adobe Campaign必須能夠控制LDAP目錄中ID/密碼組合的有效性，以便在Adobe Campaign中即時建立運算子。 要執行此操作，請核取&#x200B;**[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**&#x200B;選項。 在這種情況下，還需要配置組同步：需要選擇&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;選項。

1. 使用者已在Adobe Campaign中建立，但未在LDAP目錄中建立。

   他們無法登入Adobe Campaign。

1. LDAP目錄中有一個組，該組在Adobe Campaign中不存在。

   此群組不會在Adobe Campaign中建立。 您需要建立群組並同步群組，才能透過&#x200B;**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**&#x200B;選項啟用比對。

1. 群組存在於Adobe Campaign中，且LDAP目錄會在事件後啟動：Adobe Campaign中的使用者群組不會自動取代為LDAP群組的內容。 同樣，如果組僅存在於Adobe Campaign中，則不能向該組添加LDAP用戶，直到在LDAP中建立並同步該組。

   不論是由Adobe Campaign或LDAP即時建立群組。 這些檔案需要分別在Adobe Campaign和LDAP目錄中建立。

   LDAP目錄中的群組名稱必須與Adobe Campaign群組的名稱一致。 其關聯掩碼在部署嚮導的最後一個配置階段中定義：Adobe Campaign_(.*)，例如。
