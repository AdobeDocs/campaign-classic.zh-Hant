---
product: campaign
title: 設定安全性區域
description: 瞭解如何設定安全性區域
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

# 定義安全性區域（內部部署）{#defining-security-zones}



每個運運算元都必須連結到區域才能登入執行個體，而且運運算元IP必須包含在安全性區域中定義的位址或位址集中。 在Adobe Campaign伺服器的設定檔案中執行安全區域設定。

運運算元會從主控台中的設定檔連結至安全性區域，您可在以下位置存取： **[!UICONTROL Administration > Access management > Operators]** 節點。 [了解更多](#linking-a-security-zone-to-an-operator)。

>[!NOTE]
>
>此程式僅限於 **內部部署** 部署。
>
>As a **託管** 客戶，如果您能存取 [Campaign控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)，您可以使用Security Zone自助服務介面。 [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hant)
>
>其他 **混合/託管** 客戶需要聯絡Adobe支援團隊，將IP新增至允許清單。

## 建立安全性區域 {#creating-security-zones}

區域由下列專案定義：

* 一或多個IP位址範圍（IPv4和IPv6）
* 與每個IP位址範圍相關聯的技術名稱

安全區域會互鎖，這表示在另一個區域中定義新區域會減少可以登入該區域的操作者數量，同時增加指派給每個操作者的許可權。

區域必須在伺服器設定期間定義，在 **serverConf.xml** 檔案。 所有引數都可在 **serverConf.xml** 列於 [本節](../../installation/using/the-server-configuration-file.md).

每個區域都會定義許可權，例如：

* HTTP連線而非HTTPS
* 錯誤顯示(Java錯誤、JavaScript、C++等)
* 報表和WebApp預覽
* 透過登入/密碼驗證
* 非安全連線模式

>[!NOTE]
>
>**每個運運算元都必須連結至區域**. 如果運運算元的IP位址屬於區域定義的範圍，則運運算元可以登入執行個體。\
>運運算元的IP位址可定義於數個區域中。 在此案例中，運運算元會收到 **set** 每個區域的可用許可權數量。

現成可用 **serverConf.xml** 檔案包含三個區域： **公用、VPN和LAN**.

>[!NOTE]
>
>**開箱即用的設定是安全的**. 不過，在從舊版Adobe Campaign移轉之前，可能需要暫時降低安全性，才能移轉和核准新規則。

如何在中定義區域的範例 **serverConf.xml** 檔案：

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

定義區域的所有權利如下：

* **allowDebug**：啟用webApp在「偵錯」模式下執行
* **allowEmptyPassword**：授權使用密碼連線到執行個體
* **allowHTTP**：不需要使用HTTPS通訊協定即可建立工作階段
* **allowUserPassword**：工作階段Token可以有下列形式»`<login>/<password>`&quot;
* **sessionTokenOnly**：連線URL中不需要安全性權杖
* **showError**：伺服器端的錯誤會轉送並顯示

>[!IMPORTANT]
>
>在區域定義中，每個屬性都具有 **true** 值會降低安全性。

使用訊息中心時，如果有多個執行個體，您需要使用建立其他安全性區域 **sessionTokenOnly** 屬性定義為 **true**，僅新增必要的IP位址。 有關設定執行個體的詳細資訊，請參閱 [本檔案](../../message-center/using/configuring-instances.md).

## 安全性區域的最佳實務 {#best-practices-for-security-zones}

在「 」的定義 **區域網路** 安全區域，可以新增定義技術存取許可權的IP位址遮罩。 此新增將啟用對伺服器上託管之所有執行個體的存取權。

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

我們建議直接在專屬於執行個體的設定檔案中定義IP位址範圍，以供僅存取特定執行個體的操作者使用。

在 **`config-<instance>.xml`** 檔案：

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## 安全區域中的子網路和代理 {#sub-networks-and-proxies-in-a-security-zone}

此 **proxy** 引數可用於 **子網路** 元素來指定安全區域中的Proxy使用。

當參照Proxy且連線透過此Proxy （透過HTTP X-Forwarded-For標頭可見）進入時，已驗證的區域是Proxy的使用者端區域，而不是Proxy的使用者端區域。

>[!IMPORTANT]
>
>如果已設定Proxy且可以覆寫它（如果不存在，則覆寫它），將進行測試的IP位址將能夠被偽造。
>
>此外，中繼現在會像代理一樣產生。 因此，您可以將IP位址127.0.0.1新增至安全性區域設定中的代理程式清單。
>
>例如：「 」 `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`「。

可能會出現各種情況：

* 子網路會直接在安全性區域中參考，且未設定Proxy：子網路的使用者可以直接連線至Adobe Campaign伺服器。

   ![](assets/8101_proxy1.png)

* 為安全性區域中的子網路指定Proxy：此子網路的使用者可以透過此Proxy存取Adobe Campaign伺服器。

   ![](assets/8101_proxy2.png)

* Proxy包含在安全區域子網路中：透過此Proxy具有存取權的使用者（無論其來源為何）都可以存取Adobe Campaign伺服器。

   ![](assets/8101_proxy3.png)

可能存取Adobe Campaign伺服器的代理程式IP位址必須同時輸入到 **`<subnetwork>`** 相關和第一層子網路 **`<subnetwork name="all"/>`**. 例如，此處為IP位址為10.131.146.102的Proxy：

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

## 將安全區域連結至操作員 {#linking-a-security-zone-to-an-operator}

定義區域後，每個運運算元都必須連結到其中一個運運算元，才能登入執行個體，而且運運算元的IP位址必須包含在區域中參考的位址或位址範圍內。

區域的技術設定是在Campaign伺服器的設定檔案中執行： **serverConf.xml**.

在此之前，您必須先設定現成可用的設定 **[!UICONTROL Security zone]** 將標籤連結至區域中定義之區域的內部名稱的列舉 **serverConf.xml** 檔案。

此設定可在Campaign檔案總管中完成：

1. 按一下 **[!UICONTROL Administration > Platform > Enumerations]** 節點。
1. 選取 **[!UICONTROL Security zone (securityZone)]** 系統分項清單。

   ![](assets/enum_securityzone.png)

1. 針對伺服器組態檔中定義的每個安全區域，按一下 **[!UICONTROL Add]** 按鈕。
1. 在 **[!UICONTROL Internal name]** 欄位中，輸入中定義的區域名稱 **serverConf.xml** 檔案。 它對應至 **@name** 的屬性 `<securityzone>`  元素。 在中輸入連結至內部名稱的標籤  **標籤**&#x200B;欄位。

   ![](assets/enum_addsecurityvalue.png)

1. 按一下「確定」並儲存修改。

定義區域後，以及 **[!UICONTROL Security zone]** 列舉已設定，您必須將每個運運算元連結至安全性區域：

1. 按一下 **[!UICONTROL Administration > Access management > Operators]** 節點。
1. 選取您要連結安全區域的操作員，然後按一下 **[!UICONTROL Edit]** 標籤。
1. 前往 **[!UICONTROL Access rights]** 標籤並按一下 **[!UICONTROL Edit access parameters...]** 連結。

   ![](assets/zone_operator.png)

1. 從「 」中選取區域 **[!UICONTROL Authorized connection zone]** 下拉式清單

   ![](assets/zone_operator_selection.png)

1. 按一下 **[!UICONTROL OK]** 並儲存修改以套用這些變更。



## 建議

* 請確定您的反向Proxy不允許出現在subNetwork中。 如果是這種情況， **全部** 流量會被偵測為來自此本機IP，因此會受信任。

* 最小化sessionTokenOnly=&quot;true&quot;的使用：

   * 警告：如果此屬性設定為true，則運運算元可顯示於 **CRSF攻擊**.
   * 此外，sessionToken Cookie未設定httpOnly旗標，因此某些使用者端JavaScript程式碼可以讀取。
   * 不過，多個執行儲存格上的Message Center需要sessionTokenOnly：在sessionTokenOnly設為&quot;true&quot;的情況下建立新的安全性區域並新增 **僅需要的IP** 在此區域中。

* 可能的話，請將所有allowHTTP、showErrors設定為false （不適用於localhost）並檢查它們。

   * allowHTTP = &quot;false&quot;：強制運運算元使用HTTPS
   * showErrors = &quot;false&quot;：隱藏技術錯誤（包括SQL錯誤）。 它可防止顯示太多資訊，但會降低行銷人員解決錯誤的能力（無需向管理員要求更多資訊）

* 只有在行銷使用者/管理員使用的IP上，才將allowDebug設定為true，這些使用者/管理員需要建立（事實上是預覽）調查、webApps和報表。 此旗標可讓這些IP顯示轉送規則並偵錯。

   * 當allowDebug設為false時，輸出為：

      ```
      <redir status='OK' date='...' sourceIP='...'/>
      ```

   * 當allowDebug設定為true時，輸出為：

      ```
      <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
      ```

* 切勿將allowEmptyPassword、allowUserPassword、allowSQLInjection設定為true。 這些屬性僅允許從v5和v6.0順利移轉：

   * **allowEmptyPassword** 可讓操作員使用空白密碼。 如果您遇到這種情況，請通知所有操作員要求他們設定截止日期的密碼。 一旦過了這個期限，就將此屬性變更為false。

   * **allowUserPassword** 可讓操作員傳送其認證作為引數（以便由apache/IIS/proxy記錄）。 此功能過去曾用來簡化API的使用。 無論某些協力廠商應用程式是否使用此功能，您都可以簽入您的逐步指南（或規格）。 若是如此，您必須通知他們變更使用API的方式，並儘快移除此功能。

   * **allowSQLInjection** 可讓使用者使用舊語法執行SQL插入。 此屬性應設為false。 您可以使用/nl/jsp/ping.jsp？zones=true來檢查您的安全性區域設定。 此頁面顯示目前IP的安全性措施（使用這些安全性旗標計算）的有效狀態。

* HttpOnly cookie/useSecurityToken：請參閱 **sessionTokenOnly** 標幟。

* 最小化新增到允許清單的IP：開箱即用，在安全區域中，我們為私人網路新增了3個範圍。 您不太可能會使用所有這些IP位址。 所以只保留您需要的內容。

* 將webApp/內部運運算元更新為僅可在localhost中存取。
