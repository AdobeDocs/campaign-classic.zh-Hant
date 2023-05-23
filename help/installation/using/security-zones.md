---
product: campaign
title: 配置安全區域
description: 瞭解如何配置安全區域
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1464'
ht-degree: 1%

---

# 定義安全區域（內部）{#defining-security-zones}



每個操作員需要連結到區域才能登錄到實例，並且必須將操作員IP包括在安全區域中定義的地址或地址集中。 安全區域配置在Adobe Campaign伺服器的配置檔案中執行。

操作員從控制台中的配置檔案連結到安全區域，可在 **[!UICONTROL Administration > Access management > Operators]** 的下界。 [了解更多](#linking-a-security-zone-to-an-operator)。

>[!NOTE]
>
>此過程僅限於 **現場** 部署。
>
>作為 **托管** 客戶，如果您 [市場活動控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)，可以使用安全區域自助服務介面。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hant)
>
>其他 **混合/托管** 客戶需要聯繫Adobe支援團隊以將IP添加到允許清單中。

## 建立安全區域 {#creating-security-zones}

區域由以下定義：

* 一個或多個IP地址範圍（IPv4和IPv6）
* 與每個IP地址範圍關聯的技術名稱

安全區域是互鎖的，這意味著在另一個區域中定義新區域可以減少可以登錄到該區域的操作員數量，同時增加分配給每個操作員的權限。

必須在伺服器配置期間定義區域， **serverConf.xml** 的子菜單。 中的所有可用參數 **serverConf.xml** 列於 [此部分](../../installation/using/the-server-configuration-file.md)。

每個區域都定義權限，例如：

* HTTP連接而不是HTTPS
* 錯誤顯示（Java錯誤、JavaScript、C++等）
* 報表和WebApp預覽
* 通過登錄/密碼進行身份驗證
* 非安全連接模式

>[!NOTE]
>
>**每個運算子必須連結到區域**。 如果操作員的IP地址屬於區域定義的範圍，則操作員可以登錄到實例。\
>操作員的IP地址可以在多個區域中定義。 在這種情況下，操作員接收 **集** 每個區域的可用權限。

開箱即用 **serverConf.xml** 檔案包括三個區域： **公共、VPN和LAN**。

>[!NOTE]
>
>**出廠配置是安全的**。 但是，在從較早版本的Adobe Campaign遷移之前，可能需要暫時降低安全性，以便遷移和批准新規則。

如何在 **serverConf.xml** 檔案：

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

定義區域的所有權限如下：

* **允許調試**:使webApp能夠在「調試」模式下執行
* **allowEmptyPassword**:授權與無密碼實例的連接
* **允許HTTP**:可以建立會話，而不使用HTTPS協定
* **allowUserPassword**:會話令牌可以具有以下格式&quot;`<login>/<password>`&quot;
* **會話TokenOnly**:連接URL中不需要安全令牌
* **showErrors**:伺服器端的錯誤將被轉發並顯示

>[!IMPORTANT]
>
>在區域定義中，每個屬性 **真** 價值降低了安全性。

使用消息中心時，如果有多個執行實例，則需要使用 **會話TokenOnly** 定義的屬性 **真**&#x200B;只添加必要的IP地址。 有關配置實例的詳細資訊，請參閱 [此文檔](../../message-center/using/configuring-instances.md)。

## 安全區的最佳做法 {#best-practices-for-security-zones}

在定義中 **區域網路** 安全區域，可以添加定義技術訪問的IP地址掩碼。 此添加將啟用對伺服器上承載的所有實例的訪問。

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

我們建議直接在專用於實例的配置檔案中為只訪問特定實例的操作員定義IP地址範圍。

在 **`config-<instance>.xml`** 檔案：

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## 安全區域中的子網路和代理 {#sub-networks-and-proxies-in-a-security-zone}

的 **代理** 參數可用於 **子網路** 元素，以指定安全區域中的代理使用。

當引用代理並通過此代理進入連接時（通過HTTP X-Forwarded-For標頭可見），驗證區域是代理客戶端的區域，而不是代理客戶端的區域。

>[!IMPORTANT]
>
>如果配置了代理，並且可以覆蓋它（或者如果不存在），則將測試的IP地址將被偽造。
>
>此外，中繼現在與代理類似地生成。 因此，您可以將IP地址127.0.0.1添加到安全區域配置中的代理清單中。
>
>例如：&quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`。

可能會發生各種情況：

* 子網路在安全區域中直接引用，且未配置代理：子網用戶可以直接連接到Adobe Campaign伺服器。

   ![](assets/8101_proxy1.png)

* 為安全區域中的子網路指定代理：來自此子網的用戶可以通過此代理訪問Adobe Campaign伺服器。

   ![](assets/8101_proxy2.png)

* 代理包括在安全區域子網中：通過此代理訪問的用戶，無論其來源如何，都可以訪問Adobe Campaign伺服器。

   ![](assets/8101_proxy3.png)

必須在以下兩個中輸入可能訪問Adobe Campaign伺服器的代理的IP地址： **`<subnetwork>`** 和一級子網 **`<subnetwork name="all"/>`**。 例如，對於IP地址為10.131.146.102的代理，請在此處：

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

## 將安全區域連結到操作員 {#linking-a-security-zone-to-an-operator}

定義區域後，必須將每個操作員連結到其中一個操作員才能登錄到實例，並且該操作員的IP地址必須包含在區域中引用的地址或地址範圍中。

區域的技術配置在市場活動伺服器的配置檔案中執行： **serverConf.xml**。

在此之前，必須首先配置開箱即用 **[!UICONTROL Security zone]** 將標籤連結到在 **serverConf.xml** 的子菜單。

此配置在市場活動瀏覽器中完成：

1. 按一下 **[!UICONTROL Administration > Platform > Enumerations]** 的下界。
1. 選擇 **[!UICONTROL Security zone (securityZone)]** 系統枚舉。

   ![](assets/enum_securityzone.png)

1. 對於伺服器配置檔案中定義的每個安全區域，按一下 **[!UICONTROL Add]** 按鈕
1. 在 **[!UICONTROL Internal name]** 欄位，輸入在 **serverConf.xml** 的子菜單。 它與 **@name** 屬性 `<securityzone>`  的子菜單。 在中輸入連結到內部名稱的標籤  **標籤**&#x200B;的子菜單。

   ![](assets/enum_addsecurityvalue.png)

1. 按一下「確定」(OK)並保存修改。

定義區域並 **[!UICONTROL Security zone]** 配置了枚舉，您需要將每個運算子連結到安全區域：

1. 按一下 **[!UICONTROL Administration > Access management > Operators]** 的下界。
1. 選擇要將安全區域連結到的操作員，然後按一下 **[!UICONTROL Edit]** 頁籤。
1. 轉到 **[!UICONTROL Access rights]** ，然後按一下 **[!UICONTROL Edit access parameters...]** 的子菜單。

   ![](assets/zone_operator.png)

1. 從 **[!UICONTROL Authorized connection zone]** 下拉清單

   ![](assets/zone_operator_selection.png)

1. 按一下 **[!UICONTROL OK]** 並保存修改以應用這些更改。



## 建議

* 確保子網路中不允許使用反向代理。 如果是這樣， **全部** 將檢測到來自此本地IP的通信，因此將受信任。

* 將sessionTokenOnly=&quot;true&quot;的使用降至最低：

   * 警告：如果此屬性設定為true，則運算子可以暴露在 **CRSF攻擊**。
   * 此外，sessionTokencookie未使用httpOnly標誌設定，因此某些客戶端JavaScript代碼可以讀取它。
   * 但是，多個執行單元格上的消息中心需要sessionTokenOnly:建立會話TokenOnly設定為&quot;true&quot;的新安全區域並添加 **僅需要的IP** 在這個區域。

* 如果可能，將alllowHTTP、showErrors設定為false（不是本地主機）並檢查它們。

   * allowHTTP = &quot;false&quot;:強制運算子使用HTTPS
   * showErrors = &quot;false&quot;:隱藏技術錯誤（包括SQL錯誤）。 它可防止顯示太多資訊，但會降低營銷人員解決錯誤的能力（無需向管理員要求更多資訊）

* 僅在需要建立（實際上是預覽）調查、WebApps和報告的市場營銷用戶/管理員使用的IP上，將allowDebug設定為true。 此標誌允許這些IP獲取顯示的中繼規則並調試它們。

   * 如果allowDebug設定為false，則輸出為：

      ```
      <redir status='OK' date='...' sourceIP='...'/>
      ```

   * 如果allowDebug設定為true，則輸出為：

      ```
      <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
      ```

* 從不將allowEmptyPassword、allowUserPassword和allowSQLInjent設定為true。 這些屬性僅用於允許從v5和v6.0順利遷移：

   * **allowEmptyPassword** 允許運算子具有空密碼。 如果是這種情況，請通知所有操作員在最後期限前要求他們設定密碼。 在此截止期限過後，將此屬性更改為false。

   * **allowUserPassword** 允許操作員將其憑據作為參數發送（以便它們將由apache/IIS/proxy記錄）。 此功能過去曾用於簡化API使用。 您可以簽入您的烹飪書（或在規範中），以確定某些第三方應用程式是否使用此功能。 如果是，您必須通知他們更改他們使用我們API的方式，並盡快刪除此功能。

   * **allowSQLInjent** 允許用戶使用舊語法執行SQL注入。 此屬性應設定為false。 可以使用/nl/jsp/ping.jsp?zones=true檢查安全區域配置。 此頁顯示當前IP的安全措施（使用這些安全標誌計算）的活動狀態。

* HttpOnly cookie/useSecurityToken:參考 **會話TokenOnly** 。

* 最小化添加到允許清單的IP:現在，在安全區中，我們為專用網路添加了3個範圍。 您不太可能使用所有這些IP地址。 所以只保留你需要的。

* 將WebApp/內部運算子更新為僅可在localhost中訪問。
