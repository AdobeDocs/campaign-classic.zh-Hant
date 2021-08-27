---
product: campaign
title: Campaign 18.6發行說明
description: Campaign 18.6發行說明
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Overview
role: User
level: Beginner
exl-id: a849ce10-0972-4c42-b10e-67a81c79bc65
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 7%

---

# 第 18.6 發行版本{#release-18-6}

![](../../assets/v7-only.svg)

## 發行版本 18.6.2 - 版本編號 8949{#release-18-6-3-build-8949}

2018年8月22日

>[!CAUTION]
>
>這棟建築已召回。 請[升級至最新的組建版本](../../production/using/build-upgrade.md)或聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

**有哪些新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 說明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 查詢段落<br /> </td> 
   <td> <p>當多個Campaign使用者連線至相同的FDATeradata外部帳戶時，您現在可以傳遞每個使用者專屬的查詢範圍（索引鍵/值組）。 每次Campaign使用者在Teradata資料庫上執行查詢時，Adobe Campaign現在都能傳送與使用者相關聯的中繼資料。 這些資料包含在索引鍵和值清單中，然後可供Teradata管理員用於稽核或管理存取權限。</p><p>如需詳細資訊，請參閱<a href="../../installation/using/external-accounts.md">詳細文件</a>，以瞭解詳情。</p> </td>
  </tr> 
 </tbody> 
</table>

**功能改善**

* 電子郵件封存記錄已增強，讓您更輕鬆更清楚地檢查哪些電子郵件已成功傳送或透過密件副本封存失敗。 (NEO-10675)
* 修正了導致在追蹤廣播中顯示負載平衡器IP而非客戶IP的問題。 (NEO-11295)
* 修正傳遞屬性遭錯誤覆寫的隨機問題。 (NEO-11015)
* 修正排序擴充活動結果時的語法錯誤。 (NEO-11394)
* 修正在&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流程活動中使用計算欄位時的問題。 (NEO-11382)
* 已更新Tomcat以防止漏洞利用。 (NEO-11503)
* 修正使用FDA連線至PostgreSQL資料庫時，LATIN1編碼的錯誤。 (NEO-11299)
* 修正使用&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;傳送選項時發生的問題。 (NEO-11047)
* 修正了使用延伸連接器時無法傳送SMS的升級後問題。
* 改善套件匯入/匯出（介面中新增了記錄檔和地區）。
* 修正了當&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流程活動未完全設定時，在升級後記錄中顯示無用錯誤的問題。

**技術演變**

查詢區

特定索引鍵（PROXYUSER或PROXYROLE）可用來將Teradata使用者或角色與促銷活動使用者建立關聯。 已新增使用此代理使用者/角色的新權限。 您需要將GRANTCONNECTTHROUGH訪問權限添加到資料庫帳戶(在Teradata外部帳戶中定義的帳戶)。

已在Teradata外部帳戶中新增索引標籤。 **[!UICONTROL Query banding]**&#x200B;標籤包含下列選項：

* **[!UICONTROL Active]**:勾選此方塊以啟用功能。
* **[!UICONTROL Default]**:輸入預設的查詢段，如果用戶沒有關聯的查詢段，則將使用該段。如果沒有定義預設的查詢段落，則沒有關聯的查詢段落的用戶將無法使用Teradata。
* **[!UICONTROL Users]**:為每個使用者指定查詢區段。您可以視需要新增任意數量的索引鍵/值組。 例如：&#39;priority=1;workload=high;&#39;

如需查詢區隔的詳細資訊，請參閱下列文章：

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## 發行版本 18.6 - 版本編號 8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>這棟建築已召回。 請[升級至最新版本編號](../../production/using/build-upgrade.md)或聯繫[技術支援](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

**有哪些新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 說明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 安全性改善<br /> </td> 
   <td> 已新增一系列安全性改善項目至Campaign Classic。 以下列出改善項目和修正項目。<br /> </td> 
  </tr> 
  <tr> 
   <td> 支援Windows Server 2016<br /> </td> 
   <td> Adobe Campaign現在與Windows Server 2016相容。 請參閱<a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic相容性矩陣</a>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

decryptString

已棄用&#x200B;**decryptString**&#x200B;函式。 請參閱[已棄用和已移除的功能](https://helpx.adobe.com/tw/campaign/kb/deprecated-and-removed-features.html)文章。

若為新客戶，此函式現在僅用於解密登錄頁面中收件者的加密ID。 要解密儲存在外部帳戶中的密碼，請使用新的&#x200B;**decryptPassword**&#x200B;函式。

對於現有客戶，此函式的行為不會變更，但建議您使用&#x200B;**decryptPassword**，而非&#x200B;**decryptString**。 **XtkSecurity_Unsafe_DecryptString**&#x200B;相容性選項由升級後添加並預設激活，允許您繼續使用函式。 如果要停用&#x200B;**decryptString**，請停用選項。

decryptPassword

已添加&#x200B;**decryptPassword**&#x200B;函式。 它可讓您解密儲存在外部帳戶中的密碼。 如需詳細資訊，請參閱[JSAPI](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)檔案。

檔案API

若為新安裝，透過檔案API存取資料夾的權限會限制為&#x200B;**var**、**sftp**&#x200B;以及Adobe Campaign的臨時資料夾。

若為現有客戶，檔案API無法再存取Adobe Campaign的&#x200B;**conf**&#x200B;資料夾。 **XtkSecurity_Disable_JSFileSandboxing**&#x200B;相容性選項由升級後添加並預設激活，允許您繼續訪問其他資料夾。 如果您想要限制對Adobe Campaign的&#x200B;**var**、**sftp**&#x200B;和臨時資料夾的存取，請停用選項。

**修補程式**

* 修正可能影響SMS交易式訊息效能的問題。 (NEO-9812)
