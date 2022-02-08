---
product: campaign
title: 定義Web跟蹤標籤
description: 定義Web跟蹤標籤
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 2%

---

# 網路追蹤標籤：定義{#web-tracking-tag-definition}

![](../../assets/v7-only.svg)

Web跟蹤標籤只是用適當參數構造的URL，通過HTTP查詢發送到重定向伺服器。

## 要發送的資料的格式 {#format-of-the-data-to-be-sent}

Web跟蹤URL的格式如下： **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>添加到URL的隨機數避免了瀏覽器快取網頁所帶來的問題。

下表列出了重定向伺服器支援的特殊參數。

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
                              <p>會話Cookie</p> 
                           </td>
                           <td>
                              <p>傳遞標識符和收件人標識符。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>UUID230</p> 
                           </td>
                           <td>
                              <p>永久Cookie</p> 
                           </td>
                           <td>
                              <p>收件者標識符（如果缺少會話cookie，則非常有用）。</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>標籤</p> 
                           </td>
                           <td>
                              <p>URL參數</p> 
                           </td>
                           <td>
                              <p>跟蹤網頁的標識符：這是唯一必需的參數。</p> 
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
                              <p>如果沒有會話cookie，則使用的傳遞標識符。 此值將以十六進位表示。
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
                              <p>用於標識Internet用戶的參數。 此參數的格式為"name=value"，其中name是收件人架構的欄位。 此參數優先於會話cookie中包含的標識符。
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**幾個Web跟蹤URL**

* 訪問「首頁」標識符頁面

   **https://myserver.adobe.com/r/9862?tagid=home**

* 收集業務卷資料

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* 指定查找收件人的欄位

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   帳號為10的收件人將發送到首頁。

* 使用預設交貨

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   收件人被發送到首頁。 此資訊將儲存在標識符為230（資料庫16中的e6）的傳遞中，除非使用此查詢發送包含傳遞標識符的會話cookie。

>[!NOTE]
>
>所有通過URL參數發送到重定向伺服器的值必須是URL編碼。 在給定的示例中，請注意，字元「=」和「|」分別編碼為「%3D」和「%7C」。

## 資料傳輸方法 {#data-transmission-methods}

可以使用以下方法：

* 在 **&quot;源&quot;** HTML的屬性 **`<img>`** 標籤併入要跟蹤的網頁中。
* 生成要跟蹤的網頁時直接調用重定向伺服器。
