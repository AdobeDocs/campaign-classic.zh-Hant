---
product: campaign
title: 網路、資料庫和 SSL/TLS
description: 進一步了解網路、資料庫和SSL/TLS設定最佳實務
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 9%

---

# 網路、資料庫和 SSL/TLS {#network-database}



## 網路設定

部署內部部署類型的架構時，務必檢查以下事項： [網路配置](../../installation/using/network-configuration.md). 請確保Tomcat伺服器不能直接在伺服器外部訪問：

* 關閉外部IP上的Tomcat埠(8080)（必須在localhost上工作）
* 請勿將標準HTTP埠(80)映射到Tomcat埠(8080)

如有可能，請使用安全通道：POP3S改為POP3（或POP3，而不是TLS）。

## 資料庫

您必須應用資料庫引擎安全性最佳實踐。

## SSL/TLS設定

若要檢查憑證，您可以使用openssl。 若要檢查作用中的加密，您可以使用nmap:

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

您也可以使用 [sslyze](https://github.com/nabla-c0d3/sslyze/releases) python指令碼，兩者兼有。

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
