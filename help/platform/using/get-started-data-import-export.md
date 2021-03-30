---
solution: Campaign Classic
product: campaign
title: 開始使用匯入和匯出資料
description: 進一步瞭解Campaign Classic中的資料匯入和匯出。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 12%

---


# 開始使用匯入和匯出資料 {#get-started-data-import-export}

Adobe Campaign Classic提供資料管理功能，讓您匯入和匯出資料。 這些操作可以使用工作流或通用導入和導出來執行。

>[!IMPORTANT]
>
>使用此功能時，請記住SFTP儲存空間、資料庫儲存空間和作用中的設定檔限制，請依照您的Adobe Campaign合約規定。

## 工作流程 {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工** 作流程是自動化匯入程式的有用方式。無論您是從本機檔案或從SFTP匯入資料，都可讓您標準化資料管理程式。

有了工作流程，匯入和匯出作業可以根據排程自動重複，例如自動化多個資訊系統之間的資料交換。

如需詳細資訊，請參閱[本章節](../../platform/using/import-export-workflows.md)。

## 一般匯入和匯出 {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

此外，Campaign Classic還提供&#x200B;**一般匯入和匯出**，讓您建立偶爾匯入或匯出工作。

導入和導出在專用模板中配置，您可以配置並使用這些模板來啟動和監視導入和導出作業。

有關一般導入和導出的詳細資訊，請參閱[本節](../../platform/using/about-generic-imports-exports.md)。

>[!IMPORTANT]
>一般進口和出口只能用於臨時操作。 為確保資料的一致性並提高效率，建議您使用工作流程來執行匯入和匯出作業。

## 資料加密和壓縮{#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic可讓您匯入壓縮或加密的檔案，以及匯出壓縮或加密的檔案。

這些操作是在工作流程中執行的，方法是將預處理階段套用至您想要運用的資料。

如需詳細資訊，請參閱下列區段。

* [解壓縮或解密檔案](../../platform/using/unzip-decrypt.md)
* [壓縮或加密檔案](../../platform/using/zip-encrypt.md)

## 最佳實務及疑難排解 {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

在執行導入和導出操作時，應遵循幾個[最佳實踐](../../platform/using/import-export-best-practices.md)，以確保資料庫中的資料一致性，並避免在更新或導出過程中出現常見錯誤。

此外，[本節](../../platform/using/sftp-server-usage.md)提供與SFTP伺服器使用相關的建議和常見問題。
