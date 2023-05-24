---
product: campaign
title: 開始使用匯入及匯出資料
description: 進一步瞭解Campaign中的資料匯入和匯出
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d6055d97-75fc-4ed7-89bd-8336157454eb
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 12%

---

# 開始使用匯入及匯出資料 {#get-started-data-import-export}



Adobe Campaign Classic提供資料管理功能，可讓您匯入和匯出資料。 這些操作可以使用工作流程或一般匯入和匯出來執行。

>[!IMPORTANT]
>
>使用此功能時，請記住Adobe Campaign合約規定的SFTP儲存、資料庫儲存和作用中設定檔限制。

## 工作流程 {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工作流程** 是自動化匯入程式的實用方式。 無論您是從本機檔案或從SFTP匯入資料，這些都能讓您標準化資料管理程式。

使用工作流程，可以根據排程自動重複匯入和匯出操作，例如自動化多個資訊系統之間的資料交換。

如需詳細資訊，請參閱[本章節](../../platform/using/import-export-workflows.md)。

## 一般匯入和匯出 {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

此外，Campaign Classic還提供 **一般匯入和匯出** 可讓您建立不定期的匯入或匯出工作。

匯入和匯出是在專用範本中設定，您可以設定並使用這些範本來啟動和監控匯入和匯出作業。

如需一般匯入和匯出的詳細資訊，請參閱 [本節](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>一般匯入和匯出應僅用於偶爾操作。 為確保資料一致性並提升效率，建議您使用工作流程執行匯入和匯出作業。

## 資料加密和壓縮 {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

Campaign Classic可讓您匯入壓縮或加密的檔案，以及匯出壓縮或加密的檔案。

這些作業會透過將預處理階段套用至您要利用的資料在工作流程中執行。

如需詳細資訊，請參閱下列區段。

* [解壓縮或解密檔案](../../platform/using/unzip-decrypt.md)
* [壓縮或加密檔案](../../platform/using/zip-encrypt.md)

## 最佳實務及疑難排解 {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

您應該關注幾個專案 [最佳實務](../../platform/using/import-export-best-practices.md) 執行匯入和匯出作業時，可確保資料庫內的資料一致性，並避免在更新或匯出作業期間發生常見錯誤。

此外，您也可以參閱以下內容，瞭解與SFTP伺服器使用相關的建議和常見問題： [本節](../../platform/using/sftp-server-usage.md).
