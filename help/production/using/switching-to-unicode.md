---
product: campaign
title: 切換至Unicode
description: 切換至Unicode
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 切換至Unicode{#switching-to-unicode}



針對現有 **prod** 在Linux/PostgreSQL的執行個體中，切換至Unicode的步驟如下：

1. 停止將處理作業寫入資料庫：

   ```
   su - neolane
   nlserver shutdown
   ```

1. 傾印資料庫：

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

   新增 **u** 與資料庫識別碼相關的值前面的字元(**databaseid**)：

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. 在呼叫資料庫的伺服器上：

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

1. 確認開關。 若要這麼做，請透過Adobe Campaign主控台連線並：

   * 檢查資料是否正確顯示，尤其是重音字元：
   * 啟動傳遞，然後檢查追蹤擷取是否有效。
