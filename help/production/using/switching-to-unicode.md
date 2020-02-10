---
title: 切換為Unicode
seo-title: 切換為Unicode
description: 切換為Unicode
seo-description: null
page-status-flag: never-activated
uuid: 5f15b285-7377-453a-aa98-ca4cf14a4c80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 0f5399a8-860d-4a1b-86a9-9011b973346b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 切換為Unicode{#switching-to-unicode}

對於Linux/ **PostgreSQL中的現有** prod實例，切換到unicode的步驟如下：

1. 停止向資料庫寫入的進程：

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

1. 更新指示資料庫為Unicode的選項：

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

   在與數 **據庫標識符** (databaseId)相關的值前面添加&#x200B;**u字元**:

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

   修改資料庫參考：

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

1. 確認交換機。 若要這麼做，請透過Adobe Campaign主控台連線，並：

   * 檢查資料是否正確顯示，尤其是強調字元：
   * 啟動傳送並檢查追蹤擷取是否有效。

