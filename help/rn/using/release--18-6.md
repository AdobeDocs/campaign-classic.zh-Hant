---
solution: Campaign Classic
product: campaign
title: Campaign 18.6發行說明
description: Campaign 18.6的發行說明
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Overview
role: Business Practitioner
level: Beginner
translation-type: tm+mt
source-git-commit: ce60b2bd0a9d75ca429af2f740832b408ce3c48b
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 6%

---


# 18.6 發行版本{#release-18-6}

## 發行版本 18.6.2 - Build 8949{#release-18-6-3-build-8949}

2018年8月22日

>[!CAUTION]
>
>這個建築已經召回。 請[升級至最新版本](../../production/using/build-upgrade.md)或與[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)聯絡。

**新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 說明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 查詢條帶<br /> </td> 
   <td> <p>當多個促銷活動使用者連線至相同的FDATeradata外部帳戶時，您現在可以傳遞每個使用者專屬的查詢頻段（金鑰／值配對）。 每當促銷活動使用者在Teradata資料庫上執行查詢時，Adobe Campaign現在可以傳送與使用者相關的中繼資料。 例如，這些包含在索引鍵和值清單中的資料，便可供Teradata管理員用於稽核或管理存取權限。</p><p>如需詳細資訊，請參閱<a href="../../installation/using/external-accounts.md">相關的文件</a>，以瞭解詳情。</p> </td>
  </tr> 
 </tbody> 
</table>

**功能改善**

* 電子郵件封存記錄已增強，因此檢查哪些電子郵件已透過密件副本封存成功傳送或失敗，變得更輕鬆更清楚。 (NEO-10675)
* 修正導致在追蹤廣播中顯示負載平衡器IP而非客戶IP的問題。 (NEO-11295)
* 修正導致傳送屬性覆寫錯誤的隨機問題。 (NEO-11015)
* 修正排序擴充活動結果時的語法錯誤。 (NEO-11394)
* 修正在&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流程活動中使用計算欄位的問題。 (NEO-11382)
* Tomcat已更新，以防止漏洞利用。 (NEO-11503)
* 修正使用FDA連線至PostgreSQL資料庫時，LATIN1編碼的錯誤。 (NEO-11299)
* 修正使用&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;傳送選項時發生的問題。 (NEO-11047)
* 修正當使用延伸連接器時，無法傳送SMS的錯誤等級問題。
* 已改善封裝匯入／匯出（在介面中新增記錄檔和地區）。
* 修正當&#x200B;**[!UICONTROL Survey answers]**&#x200B;工作流程活動未完整設定時，在設定檔記錄檔中顯示無用錯誤的問題。

**技術演變**

查詢色帶

特定金鑰（PROXYUSER或PROXYROLE）可用來將Teradata使用者或角色與促銷活動使用者建立關聯。 已新增使用此代理用戶／角色的權限。 您需要通過對資料庫帳戶(在Teradata外部帳戶中定義的帳戶)的訪問權限添加GRANTCONNECT。

已在Teradata外部帳戶中新增標籤。 **[!UICONTROL Query banding]**&#x200B;標籤包含下列選項：

* **[!UICONTROL Active]**:選中此框以激活特徵。
* **[!UICONTROL Default]**:輸入預設查詢帶條，如果用戶沒有關聯的查詢帶條，則將使用該帶條。如果沒有定義預設查詢帶，則沒有關聯查詢帶的用戶將無法使用Teradata。
* **[!UICONTROL Users]**:請為每位使用者指定查詢色帶。您可以視需要新增任意數量的金鑰／值配對。 例如：『priority=1;workload=high;&#39;

如需查詢色帶的詳細資訊，請參閱下列文章：

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## 發行版本 18.6 - Build 8947{#release-18-6-build-8947}

2018年6月25日

>[!CAUTION]
>
>這個建築已經召回。 請[升級至最新版本](../../production/using/build-upgrade.md)或與[技術支援](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)聯絡。

**新增功能？**

<table> 
 <thead> 
  <tr> 
   <th> 功能<br /> </th> 
   <th> 說明<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 安全性改進<br /> </td> 
   <td> Campaign Classic已新增一系列安全性改進。 改進和修正列於下方。<br /> </td> 
  </tr> 
  <tr> 
   <td> 支援Windows Server 2016<br /> </td> 
   <td> Adobe Campaign現在與Windows Server 2016相容。 請參閱<a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Campaign Classic相容性表</a>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

**安全性增強功能**

decryptString

**decryptString**&#x200B;函式已過時。 請參閱[已過時和已移除的功能](https://helpx.adobe.com/tw/campaign/kb/deprecated-and-removed-features.html)文章。

對於新客戶，此函式現在僅用於解密登陸頁面中收件者的加密ID。 要解密儲存在外部帳戶中的密碼，請使用新的&#x200B;**decryptPassword**&#x200B;函式。

對於現有客戶，此函式的行為不會變更，但建議您使用&#x200B;**decryptPassword**，而非&#x200B;**decryptString**。 **XtkSecurity_Unsafe_DecryptString**&#x200B;相容性選項由postupgrade新增並依預設啟用，讓您可繼續使用函式。 如果要停用&#x200B;**decryptString**，請停用選項。

decryptPassword

已添加&#x200B;**decryptPassword**&#x200B;函式。 它允許您解密儲存在外部帳戶中的密碼。 如需詳細資訊，請參閱[JSAPI](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)檔案。

檔案API

對於新安裝，通過檔案API訪問資料夾的限制為&#x200B;**var**、**sftp**&#x200B;和Adobe Campaign的臨時資料夾。

對於現有客戶，檔案API無法再訪問Adobe Campaign的&#x200B;**conf**&#x200B;資料夾。 **XtkSecurity_Disable_JSFileSandboxing**&#x200B;相容性選項由配置添加，預設情況下激活，允許您繼續訪問其他資料夾。 如果您想要限制對&#x200B;**var**、**sftp**&#x200B;和Adobe Campaign的臨時資料夾的存取，請停用選項。

**修補程式**

* 修正可能影響SMS交易訊息效能的問題。 (NEO-9812)
