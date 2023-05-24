---
product: campaign
title: 定義網路追蹤標籤
description: 定義網路追蹤標籤
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 2%

---

# 網路追蹤標籤：定義{#web-tracking-tag-definition}



網路追蹤標籤只是使用適當引數建構的URL，會透過HTTP查詢傳送至重新導向伺服器。

## 要傳送的資料格式 {#format-of-the-data-to-be-sent}

網路追蹤URL的格式如下： **https://`<name_of_redirection_server>`：`<port>`/r/`<random_number>`？`<parameters>`**

>[!NOTE]
>
>新增至URL的隨機數字可避免瀏覽器快取網頁所造成的問題。

下表提供重新導向伺服器支援的特殊引數清單。

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
                              <p>工作階段Cookie</p> 
                           </td>
                           <td>
                              <p>傳遞識別碼和收件者識別碼。</p> 
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
                              <p>收件者識別碼（如果工作階段Cookie不存在則很有用）。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>URL引數</p> 
                           </td>
                           <td>
                              <p>被追蹤網頁的識別碼：這是唯一的必要引數。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>jobid</p> 
                           </td>
                           <td>
                              <p>URL引數</p> 
                           </td>
                           <td>
                              <p>沒有工作階段Cookie時要使用的傳遞識別碼。 此值以十六進位表示。
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>URL引數</p> 
                           </td>
                           <td>
                              <p>用於識別網際網路使用者的引數。 此引數的格式為「name=value」，其中名稱是收件者綱要的欄位。 此引數的優先順序高於工作階段Cookie中包含的識別碼。
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**一些網路追蹤URL**

* 造訪「首頁」識別碼頁面

   **https://myserver.adobe.com/r/9862?tagid=home**

* 收集業務量資料

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* 指定欄位以尋找收件者

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   帳號為10的收件者會傳送到首頁。

* 使用預設傳遞

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   收件者會傳送至首頁。 除非使用此查詢傳送包含傳遞識別碼的工作階段Cookie，否則此資訊會以識別碼230 （資料庫16中的e6）儲存在傳遞中。

>[!NOTE]
>
>所有透過URL引數傳送至重新導向伺服器的值都必須經過URL編碼。 在提供的範例中，請注意，字元&#39;=&#39;和&#39;|&#39;分別編碼為&#39;%3D&#39;和&#39;%7C&#39;。

## 資料傳輸方法 {#data-transmission-methods}

可以使用下列方法：

* 將URL插入 **&quot;src&quot;** HTML的屬性 **`<img>`** 標籤已整合到您要追蹤的網頁中。
* 產生您要追蹤的網頁時，直接呼叫重新導向伺服器。
