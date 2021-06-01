---
product: campaign
title: 切換為 Unicode
description: 切換為 Unicode
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 7%

---

# 切換為 Unicode{#switching-to-unicode}

對於Linux/PostgreSQL中的現有&#x200B;**prod**&#x200B;實例，切換為unicode的步驟如下：

1. 停止寫入資料庫的進程：

   ```
   su - neolane
   nlserver shutdown
   ```

1. 轉儲資料庫：

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. 建立Unicode資料庫：

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. 還原資料庫：

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. 更新表示資料庫為Unicode的選項：

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. 在追蹤伺服器上：

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   在與資料庫標識符(**databaseId**)相關的值前面添加&#x200B;**u**&#x200B;字元：

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. 在調用資料庫的伺服器上：

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   修改資料庫引用：

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. 重新啟動所有電腦：

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. 確認開關。 若要這麼做，請透過Adobe Campaign主控台連線，並：

   * 檢查資料是否正確顯示，尤其是強調字元：
   * 啟動傳送並檢查追蹤擷取是否有效。
