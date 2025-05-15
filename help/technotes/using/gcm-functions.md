---
product: campaign
title: 新的GCM型函式
description: 新的GCM型函式
feature: Technote
exl-id: 154dee7a-a1e9-40a2-bfa5-3641382d0574
source-git-commit: b6d64f66d287dba79be5eddec48ee852c2c7740c
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 2%

---

# 以 GCM 為基礎的函式 {#new-functions}

為了改善安全性，我們不再將AES （進階加密標準）演演算法與CBC （密碼區塊鏈結）模式搭配用於密碼編譯操作。 已引入新的加密功能。 這些函式會將AES與Galois/Counter Mode (AES-GCM)搭配使用，提供更安全的替代方案。 這些函式可在JavaScript、JSP、SOAP API和XML結構描述中使用，可讓客戶從CBC轉換到GCM進行加密和解密。

本檔案列出新推出的AES-GCM函式以及即將淘汰的CBC型函式。

新函式：

* [EncryptString API函式](#encryptString-api-xtk)
* [EncryptStringWithServerPassword API函式](#EncryptStringWithServerPassword-api-xtk)
* [encryptString javascript函式](#encryptString-javascript)

可用於GCM的舊版函式：

* [DecryptString javascript函式](#decryptString-javascript)
* [DecryptPassword javascript函式](#decryptPassword-javascript)

[已棄用的函式](#depracated-functions)

## API函式

### Encryptstring {#encryptString-api-xtk}

使用AES演演算法搭配GCM模式使用例項金鑰加密字元字串。

```
            String 
            encrypted = EncryptString (
            String       
            decrypted
            

      )
         
```

**引數**：解密的文字

**傳回值**：已加密

**結構描述**： xtk：session

**靜態**：是

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

使用含GCM模式的AES演演算法，以伺服器金鑰加密字元字串。


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**引數**：已解密

**傳回值**：已加密

**結構描述**： xtk：session

**靜態**：是

## Javascript函式

### encryptString() {#encryptString-javascript}

使用例項的鍵或任何其他鍵加密字元字串。

```
            encryptString (str [, key
      ] [, useSalt ])
         
```

**引數**：

* str：要加密的字元字串。
* 金鑰：AES加密金鑰以base 64:256位元編碼（如果金鑰長度為32）；192位元（如果金鑰長度為24）；128位元（如果金鑰長度為16或未指定金鑰）。
* useSalt：使用資料的Salt進行加密。 預設為True。

**傳回值**：傳回加密的字元字串。

**備註**

加密會根據下列方法進行：

* unicode字元字串會轉換為UTF-8字串。
* 檢查字元會新增到加密文字的末端。
* 在Galois/Counter Mode (GCM)模式中，此字串是使用AES演演算法加密的，使用salt加上12位元組初始化向量和16位元組標籤。 如果未提供索引鍵作為引數，則會使用例項索引鍵。
* 加密文字將包含標籤和初始化向量。
* 然後加密區塊會轉換為基底64。

解密是使用decryptString函式執行。

**功能**

提供於：

* 內容管理
* 傳遞屬性
* 傳遞訊息
* 類型規則
* 匯入
* JSSP
* SOAP方法
* WebApp
* 工作流程

### decryptString() {#decryptString-javascript}

使用例項的鍵或任何其他鍵解密字元字串。 此舊版函式可搭配GCM使用。 不建議使用AES-CBC模式加密的加密文字解密。

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**引數**：

* str：要解密的字元字串。
* 金鑰：AES加密金鑰以base 64:256位元編碼（如果金鑰長度為32）；192位元（如果金鑰長度為24）；128位元（如果金鑰長度為16或未指定金鑰）。
* useSalt：使用資料的鹽來解密。 預設為True。

**傳回值**：傳回解密的字元字串。

**警告**：使用此方法無法再解密儲存在資料庫中的密碼（選項/外部帳戶）。 為此，請使用[decryptPassword](#decryptPassword-javascript)。

### decryptPassword() {#decryptPassword-javascript}

解密儲存在外部帳戶中的密碼。 此舊版函式可搭配GCM使用。 不建議使用AES-CBC模式加密的加密文字解密。

```
            decryptPassword (str)
         
```

**引數**：

* str：要解密的字元字串。

**傳回值**：傳回純文字密碼。

**備註**

無法在工作流程、網頁應用程式、報表或傳遞中呼叫此函式。 可在JSSP或SOAP呼叫實作中呼叫它。 範例：

```
        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## 已棄用的函式 {#depracated-functions}

下列函式已完全淘汰：

* cryptString
* 加密
* EncryptServerPassword
