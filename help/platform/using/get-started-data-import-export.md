---
product: campaign
title: 開始使用匯入及匯出資料
description: 進一步了解以Campaign Classic匯入和匯出資料。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d6055d97-75fc-4ed7-89bd-8336157454eb
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 11%

---

# 開始使用匯入及匯出資料 {#get-started-data-import-export}

![](../../assets/common.svg)

Adobe Campaign Classic提供資料管理功能，可讓您匯入和匯出資料。 這些操作可使用工作流程或一般匯入和匯出來執行。

>[!IMPORTANT]
>
>使用此功能時，請記得您的Adobe Campaign合約所規定的SFTP儲存空間、資料庫儲存空間和作用中設定檔限制。

## 工作流程 {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工作流程** 是自動匯入程式的實用方法。 無論您是從本機檔案匯入資料，還是從SFTP匯入資料，都可讓您將資料管理程式標準化。

使用工作流程，可以根據計畫自動重複導入和導出操作，例如自動在多個資訊系統之間交換資料。

如需詳細資訊，請參閱[本章節](../../platform/using/import-export-workflows.md)。

## 一般匯入和匯出 {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

此外，Campaign Classic提供 **一般匯入和匯出** 可讓您建立偶爾的匯入或匯出工作。

匯入和匯出是在專用範本中設定，您可以設定並使用這些範本來啟動和監視匯入和匯出作業。

如需一般匯入和匯出的詳細資訊，請參閱 [本節](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>一般匯入和匯出應僅用於偶爾作業。 為確保資料一致性並提高效率，建議您使用工作流程執行匯入和匯出操作。

## 資料加密和壓縮 {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic可讓您匯入壓縮或加密的檔案，以及匯出壓縮或加密的檔案。

這些操作是在工作流程中執行，方法是將預先處理階段套用至您要運用的資料。

如需詳細資訊，請參閱下列區段。

* [解壓縮或解密檔案](../../platform/using/unzip-decrypt.md)
* [壓縮或加密檔案](../../platform/using/zip-encrypt.md)

## 最佳實務及疑難排解 {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

您應遵循數個 [最佳實務](../../platform/using/import-export-best-practices.md) 執行匯入和匯出作業時，以確保資料庫內的資料一致性，並避免在更新或匯出作業期間出現常見錯誤。

此外，您可在以下網址取得與SFTP伺服器使用相關的建議和常見問題： [本節](../../platform/using/sftp-server-usage.md).
