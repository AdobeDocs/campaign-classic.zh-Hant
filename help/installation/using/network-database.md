---
solution: Campaign Classic
product: campaign
title: 網路、資料庫和SSL/TLS
description: 進一步瞭解網路、資料庫和SSL/TLS組態最佳實務。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 63b2e6b95812f1649e636580984a1f0dcc9c5c53
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---


# 網路、資料庫和SSL/TLS {#network-database}

## 網路配置

部署內部部署類型的體系結構時，需要檢查的一個非常重要的問題是[網路配置](../../installation/using/network-configuration.md)。 確保Tomcat伺服器不直接在伺服器外部訪問：

* 在外部IP上關閉Tomcat埠(8080)（必須在localhost上工作）
* 不要將標準HTTP埠(80)映射到Tomcat 1埠(8080)

如果可能，請使用安全通道：POP3S改為POP3（或POP3 over TLS）。

## 資料庫

您必須應用資料庫引擎安全性最佳實踐。

## SSL/TLS配置

若要檢查憑證，您可以使用openssl。 若要檢查作用中的密碼，您可以使用nmap:

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

您也可以使用[sslyze](https://github.com/nabla-c0d3/sslyze/releases) python指令碼，該指令碼可同時執行這兩項操作。

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
