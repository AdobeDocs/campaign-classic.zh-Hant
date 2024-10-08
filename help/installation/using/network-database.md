---
product: campaign
title: 網路、資料庫和 SSL/TLS
description: 進一步瞭解網路、資料庫和SSL/TLS設定最佳實務
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 9%

---

# 網路、資料庫和 SSL/TLS {#network-database}

## 網路設定

部署內部部署型別的架構時，很重要的一點要檢查是[網路組態](../../installation/using/network-configuration.md)。 請確定無法在伺服器外部直接存取Tomcat伺服器：

* 關閉外部IP上的Tomcat連線埠(8080) （必須在localhost上運作）
* 請勿將標準HTTP連線埠(80)對應到Tomcat連線埠(8080)

儘可能使用安全色版：POP3S而非POP3 （或透過TLS的POP3）。

## 資料庫

您必須套用您的資料庫引擎安全性最佳實務。

## SSL/TLS設定

若要檢查憑證，您可以使用openssl。 若要檢查作用中加密，您可以使用nmap：

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

您也可以使用兼具兩者的[slyze](https://github.com/nabla-c0d3/sslyze/releases) python指令碼。

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
