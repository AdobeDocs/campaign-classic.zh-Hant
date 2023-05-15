---
product: campaign
title: 定義網頁追蹤標籤
description: 定義網頁追蹤標籤
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 2%

---

# 網路追蹤標籤：定義{#web-tracking-tag-definition}



Web追蹤標籤只是使用適當參數建構的URL，會透過HTTP查詢傳送至重新導向伺服器。

## 要傳送的資料格式 {#format-of-the-data-to-be-sent}

網頁追蹤URL的格式如下： **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>新增至URL的隨機數字可避免瀏覽器快取網頁所造成的問題。

下表提供了重定向伺服器支援的特殊參數的清單。

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
                              <p>傳送識別碼和收件者識別碼。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>永久性Cookie</p> 
                           </td>
                           <td>
                              <p>收件者識別碼（若工作階段Cookie不存在，則此功能會很實用）。</p> 
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
                              <p>沒有工作階段Cookie時要使用的傳送識別碼。 此值將以十六進位表示。
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
                              <p>用於識別網際網路使用者的參數。 此參數的格式為"name=value"，其中name是收件者架構的欄位。 此參數的優先順序高於工作階段Cookie中包含的識別碼。
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

* 指定要查找收件人的欄位

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   帳號為10的收件者會傳送至首頁。

* 使用預設傳送

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   收件者會傳送至首頁。 此資訊將儲存在標識符為230的傳送中（資料庫16中為e6），除非與此查詢一起發送包含傳送標識符的會話Cookie。

>[!NOTE]
>
>所有透過URL參數傳送至重新導向伺服器的值都必須經過URL編碼。 在給定的示例中，請注意字元「=」和「|」分別編碼為「%3D」和「%7C」。

## 資料傳輸方法 {#data-transmission-methods}

可採用下列方法：

* 在 **&quot;src&quot;** 屬性的HTML **`<img>`** 標籤併入您要追蹤的網頁中。
* 在您要追蹤的網頁產生時，直接呼叫重新導向伺服器。
