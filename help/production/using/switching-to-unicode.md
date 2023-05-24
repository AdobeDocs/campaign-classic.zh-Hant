---
product: campaign
title: 切換為 Unicode
description: 切換為 Unicode
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 7%

---

# 切換為 Unicode{#switching-to-unicode}



針對現有 **prod** Linux/PostgreSQL中的執行個體，切換至Unicode的步驟如下：

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

   新增 **u** 與資料庫識別碼相關的值前面的字元(**資料庫識別碼**)：

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

1. 確認交換器。 若要這麼做，請透過Adobe Campaign主控台連線，並：

   * 檢查資料是否正確顯示，尤其是重音字元：
   * 啟動傳遞，並檢查追蹤擷取是否有效。
