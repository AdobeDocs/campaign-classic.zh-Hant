---
product: campaign
title: 配置安全區域
description: 了解如何配置安全區域
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '1464'
ht-degree: 1%

---

# 定義安全區域（內部部署）{#defining-security-zones}



每個運算子都需要連結到區域才能登錄到實例，並且運算子IP必須包含在安全區域中定義的地址或地址集中。 安全區配置在Adobe Campaign伺服器的配置檔案中執行。

運算子會從主控台的設定檔連結至安全區域，可在 **[!UICONTROL Administration > Access management > Operators]** 節點。 [了解更多](#linking-a-security-zone-to-an-operator)。

>[!NOTE]
>
>此程式僅限於 **內部部署** 部署。
>
>As a **托管** 客戶，如果您可以 [Campaign控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)，您可以使用安全區域自助服務介面。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hant)
>
>其他 **混合/托管** 客戶需要聯絡Adobe支援團隊，將IP新增至允許清單。

## 建立安全區域 {#creating-security-zones}

區域由以下項定義：

* 一個或多個IP地址範圍（IPv4和IPv6）
* 與每個IP位址範圍相關聯的技術名稱

安全區域是互鎖的，這意味著在另一個區域內定義新區域可以減少可以登錄到該區域的操作員數量，同時增加分配給每個操作員的權限。

必須在伺服器配置期間定義區域，位於 **serverConf.xml** 檔案。 中所有可用的參數 **serverConf.xml** 列於 [本節](../../installation/using/the-server-configuration-file.md).

每個區域都定義權利，例如：

* HTTP連線而非HTTPS
* 錯誤顯示(Java錯誤、JavaScript、C++等)
* 報表和WebApp預覽
* 通過登錄/密碼進行身份驗證
* 非安全連接模式

>[!NOTE]
>
>**每個運算子都必須連結至區域**. 如果運算子的IP位址屬於區域所定義的範圍，運算子可登入執行個體。\
>運算子的IP位址可在數個區域中定義。 在此情況下，運算子會接收 **set** 每個區域的可用權限。

現成可用 **serverConf.xml** 檔案包含三個區域： **公共、VPN和LAN**.

>[!NOTE]
>
>**現成可用的設定是安全的**. 不過，在從舊版Adobe Campaign移轉之前，可能需要暫時降低安全性，才能移轉並核准新規則。

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

* **allowDebug**:讓webApp可在「除錯」模式中執行
* **allowEmptyPassword**:授權不使用密碼連線至執行個體
* **allowHTTP**:不使用HTTPS通訊協定即可建立工作階段
* **allowUserPassword**:工作階段代號可具有下列格式：`<login>/<password>`&quot;
* **sessionTokenOnly**:連線URL中不需要安全權杖
* **showErrors**:會轉送並顯示伺服器端的錯誤

>[!IMPORTANT]
>
>在區域定義中，每個屬性 **true** 值降低了安全性。

使用訊息中心時，如果有數個執行例項，您需要使用 **sessionTokenOnly** 屬性定義為 **true**，其中只需新增必要的IP位址。 如需設定例項的詳細資訊，請參閱 [此文檔](../../message-center/using/configuring-instances.md).

## 安全區域最佳實務 {#best-practices-for-security-zones}

在 **lan** 安全區域，可新增定義技術存取的IP位址遮罩。 此新增功能將啟用對伺服器上托管的所有執行個體的存取。

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

建議僅存取特定例項的運算子，直接在該例項專用的設定檔案中定義IP位址範圍。

在 **`config-<instance>.xml`** 檔案：

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## 安全區域中的子網和代理 {#sub-networks-and-proxies-in-a-security-zone}

此 **代理** 參數可用於 **subNetwork** 要指定在安全區域中使用代理的元素。

當引用代理且連線透過此代理進入時（透過HTTP X-Forwarded-For標頭可見），驗證的區域是代理的用戶端，而非代理的用戶端。

>[!IMPORTANT]
>
>如果已設定代理，且可以覆寫代理（或若不存在），則將測試的IP位址將能夠偽造。
>
>此外，中繼現在會像Proxy一樣產生。 因此，您可以將IP地址127.0.0.1添加到安全區域配置中的Proxy清單中。
>
>例如：&quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`」。

可能會發生各種情況：

* 在安全區域中直接引用子網路，並且未配置代理：子網路的使用者可直接連線至Adobe Campaign伺服器。

   ![](assets/8101_proxy1.png)

* 為安全區域中的子網路指定代理：來自此子網路的使用者可透過此代理存取Adobe Campaign伺服器。

   ![](assets/8101_proxy2.png)

* 代理包含在安全區域子網路中：透過此代理存取的使用者（不論其來源為何）可存取Adobe Campaign伺服器。

   ![](assets/8101_proxy3.png)

必須在 **`<subnetwork>`** 第一級子網 **`<subnetwork name="all"/>`**. 例如，若IP位址為10.131.146.102的Proxy，請前往下列位置：

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

定義區域後，每個運算子必須連結到其中一個運算子才能登錄到實例，並且運算子的IP地址必須包含在區域中引用的地址或地址範圍中。

區域的技術設定會在Campaign伺服器的設定檔案中執行： **serverConf.xml**.

在此之前，您必須先設定現成可用的 **[!UICONTROL Security zone]** 枚舉以將標籤連結到中定義的區域的內部名稱 **serverConf.xml** 檔案。

此設定是在Campaign檔案總管中完成：

1. 按一下 **[!UICONTROL Administration > Platform > Enumerations]** 節點。
1. 選取 **[!UICONTROL Security zone (securityZone)]** 系統枚舉。

   ![](assets/enum_securityzone.png)

1. 對於伺服器配置檔案中定義的每個安全區域，按一下 **[!UICONTROL Add]** 按鈕。
1. 在 **[!UICONTROL Internal name]** 欄位中，輸入 **serverConf.xml** 檔案。 它對應至 **@name** 屬性 `<securityzone>`  元素。 在  **標籤**&#x200B;欄位。

   ![](assets/enum_addsecurityvalue.png)

1. 按一下「確定」並儲存修改。

定義區域後， **[!UICONTROL Security zone]** 枚舉已配置，您需要將每個運算子連結到安全區域：

1. 按一下 **[!UICONTROL Administration > Access management > Operators]** 節點。
1. 選擇要將安全區域連結到的運算子，然後按一下 **[!UICONTROL Edit]** 標籤。
1. 前往 **[!UICONTROL Access rights]** ，然後按一下 **[!UICONTROL Edit access parameters...]** 連結。

   ![](assets/zone_operator.png)

1. 從 **[!UICONTROL Authorized connection zone]** 下拉式清單

   ![](assets/zone_operator_selection.png)

1. 按一下 **[!UICONTROL OK]** 並儲存修改以套用這些變更。



## 建議

* 請確定子網路中不允許您的反向代理。 如果是這樣， **all** 會偵測到來自此本機IP的流量，因此將會受信任。

* 盡量不使用sessionTokenOnly=&quot;true&quot;:

   * 警告：如果此屬性設為true，運算子可公開給 **CRSF攻擊**.
   * 此外，sessionToken Cookie未以httpOnly標幟設定，因此有些用戶端JavaScript程式碼可以讀取。
   * 但多個執行儲存格上的訊息中心需要sessionTokenOnly:使用sessionTokenOnly設為&quot;true&quot;建立新的安全區域並新增 **只有所需的IP** 在這個區。

* 如果可能，請將所有allowHTTP、showErrors設定為false（而非localhost）並加以檢查。

   * allowHTTP = &quot;false&quot;:強制運算子使用HTTPS
   * showErrors = &quot;false&quot;:隱藏技術錯誤（包括SQL錯誤）。 它可防止顯示太多資訊，但會降低行銷人員解決錯誤的能力（而無須向管理員要求更多資訊）

* 只有在需要建立調查、webApps和報表的行銷使用者/管理員所使用的IP上，才將allowDebug設為true。 此標幟可讓這些IP取得顯示的中繼規則，並對其進行除錯。

   * 若allowDebug設為false，則輸出為：

      ```
      <redir status='OK' date='...' sourceIP='...'/>
      ```

   * 若allowDebug設為true，則輸出為：

      ```
      <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
      ```

* 從不將allowEmptyPassword、allowUserPassword、allowSQLInjection設定為true。 這些屬性僅用於允許從v5和v6.0順利遷移：

   * **allowEmptyPassword** 讓運算子具有空密碼。 如果是這種情況，請通知所有操作員，要求他們在最後期限內設定密碼。 一旦此截止日期過後，請將此屬性變更為false。

   * **allowUserPassword** 可讓運算子以參數形式傳送其憑證（以便由apache/IIS/proxy記錄）。 此功能過去曾用來簡化API的使用。 您可以在逐步指南中（或在規格中）查看某些第三方應用程式是否使用此功能。 若是如此，您必須通知他們變更使用API的方式，並盡快移除此功能。

   * **allowSQLInjents** 可讓使用者使用舊語法執行SQL插入。 此屬性應設為false。 您可以使用/nl/jsp/ping.jsp?zones=true來檢查您的安全區域配置。 此頁顯示當前IP的安全措施的活動狀態（使用這些安全標誌計算）。

* HttpOnly cookie/useSecurityToken:請參閱 **sessionTokenOnly** 標籤。

* 將新增至允許清單的IP最小化：現成可用的安全區域中，我們已新增3個專用網路範圍。 您不太可能使用所有這些IP位址。 所以只保留你需要的。

* 更新webApp/內部運算子，使其僅可在localhost中存取。
