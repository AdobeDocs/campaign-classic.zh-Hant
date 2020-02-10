---
title: '"網路追蹤標籤：定義」'
seo-title: '"網路追蹤標籤：定義」'
description: '"網路追蹤標籤：定義」'
seo-description: null
page-status-flag: never-activated
uuid: 915ddfd8-ad1b-41ac-96ed-f7fae687c09f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: b8996508-7173-4225-95e7-b51209aae1f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3ad288bc983002da82b564e8ab3f4244c6324573

---


# 網頁追蹤標籤：定義{#web-tracking-tag-definition}

網頁追蹤標籤只是使用適當參數建構的URL，透過HTTP查詢傳送至重新導向伺服器。

## 要傳送的資料格式 {#format-of-the-data-to-be-sent}

網頁追蹤URL的格式如下： **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>新增至URL的隨機數字可避免瀏覽器快取網頁所造成的問題。

下表列出重新導向伺服器支援的特殊參數清單。

<table>
                     <thead>
                        <tr>
                           <th>名稱</th>
                           <th>類型</th>
                           <th>說明</th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>ID</p> 
                           </td>
                           <td>
                              <p>作業Cookie</p> 
                           </td>
                           <td>
                              <p>傳送識別碼和收件者識別碼。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>永久Cookie</p> 
                           </td>
                           <td>
                              <p>收件者識別碼（若作業Cookie不存在，則很實用）。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>URL參數</p> 
                           </td>
                           <td>
                              <p>追蹤網頁的識別碼：這是唯一的必要參數。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>jobid</p> 
                           </td>
                           <td>
                              <p>URL參數</p> 
                           </td>
                           <td>
                              <p>若沒有工作階段Cookie，則使用傳送識別碼。 此值將以十六進位表示。
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>URL參數</p> 
                           </td>
                           <td>
                              <p>用於識別網際網路使用者的參數。 此參數的格式為"name=value"，其中name是收件人方案的欄位。 此參數會優先於作業Cookie中包含的識別碼。
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**幾個網頁追蹤URL**

* 造訪「首頁」識別碼頁面

   **https://myserver.adobe.com/r/9862?tagid=home**

* 收集業務量資料

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* 指定欄位以尋找收件者

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   帳號為10的收件者會傳送至首頁。

* 使用預設傳送

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   收件者會傳送至首頁。 此資訊將儲存在具有識別碼230（資料庫16中為e6）的傳送中，除非隨此查詢傳送包含傳送識別碼的作業Cookie。

>[!NOTE]
>
>所有透過URL參數傳送至重新導向伺服器的值都必須經過URL編碼。 在給定的示例中，請注意，字元&#39;=&#39;和&#39;|&#39;分別編碼為&#39;%3D&#39;和&#39;%7C&#39;。

## 資料傳輸方法 {#data-transmission-methods}

可能有下列方法：

* 將URL插入 **您要追蹤的網****`<img>`** 頁中併入之HTML標籤的「src」屬性。
* 產生您要追蹤的網頁時，直接呼叫重新導向伺服器。

