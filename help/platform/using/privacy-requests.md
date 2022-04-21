---
product: campaign
title: 管理隱私請求
description: 瞭解隱私請求
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: a8044037e889f59d4288a0746001e84d319f6bcf
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 98%

---

# 關於隱私權請求 {#privacy-requests}

![](../../assets/v7-only.svg)

如需隱私權管理的一般簡報，請參閱[本節](privacy-management.md)。

此資訊適用於 GDPR、CCPA、PDPA 及 LGPD。如需這些法規的詳細資訊，請參閱[本節](privacy-management.md#privacy-management-regulations)。

>[!NOTE]
>
>[本節](#sale-of-personal-information-ccpa)會詳細說明專屬於 CCPA 的選擇退出個人資訊銷售。

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

為協助您加速隱私權準備，Adobe Campaign 可讓您處理存取和刪除要求。[本節](privacy-management.md#right-access-forgotten)說明&#x200B;**存取權限**&#x200B;及&#x200B;**被遺忘的權利**（刪除要求）。

Adobe Campaign 為資料控制方執行隱私權存取和刪除請求提供兩種可能性：

* 透過 **Adobe Campaign 介面**：針對每個隱私權請求，資料控制方會在 Adobe Campaign 建立新的隱私權請求。請參閱[本節](privacy-requests-ui.md)。
* 透過&#x200B;**API**：Adobe Campaign 提供 API允許使用 SOAP 自動處理隱私權請求。請參閱[本節](privacy-requests-api.md)。

>[!NOTE]
>
>如需關於個人資料及管理資料之不同實體 (資料控制方、資料處理方和資料主體) 的詳細資訊，請參閱[個人資料和人員](privacy-and-recommendations.md#personal-data)。

## 先決條件 {#prerequesites}

Adobe Campaign 提供資料控制方工具，可針對儲存在 Adobe Campaign 中的資料而建立和處理隱私權要求。然而，資料控制方有責任處理與資料主體（電子郵件、客戶服務或 Web 入口網站）的關係。

因此，身為資料控制方的您，應負責確認提出要求之資料主體的身份，並確認傳回給要求者的資料與資料主體有關。

## 安裝隱私權套件 {#install-privacy-package}

為了使用此功能，您需要透過&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**&#x200B;功能表安裝&#x200B;**[!UICONTROL Privacy Data Protection Regulation]**&#x200B;套件。 有關如何安裝軟體套件的詳細資訊，請參閱[詳細文件](../../installation/using/installing-campaign-standard-packages.md)。

在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]**&#x200B;下建立了兩個專屬於隱私權的新資料夾：

* **[!UICONTROL Privacy Requests]**：您可在此建立您的隱私權請求並追蹤其演進。
* **[!UICONTROL Namespaces]**：您將在這裡定義用於識別 Adobe Campaign 資料庫中資料主體的欄位。

![](assets/privacy-folders.png)

在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;中，每天會執行三個技術工作流程來處理隱私權請求。

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**：此工作流程會產生儲存在 Adobe Campaign 的收件者資料，並讓該資料可在隱私權請求的畫面中下載。
* **[!UICONTROL Delete privacy requests data]**：此工作流程會刪除收件者儲存在 Adobe Campaign 的資料。
* **[!UICONTROL Privacy request cleanup]**：此工作流程會清除 90 天以前的存取請求檔案。

在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**&#x200B;中，已新增了&#x200B;**[!UICONTROL Privacy Data Right]**&#x200B;已命名的權限。 資料控制方若要使用隱私權工具，必須具備此已命名的權限。 這可讓他們建立新請求、追蹤其演進、使用 API 等。

![](assets/privacy-right.png)

## 命名空間 {#namesspaces}

在建立隱私權要求之前，您必須先定義要使用的命名空間。這是將用於識別 Adobe Campaign 資料庫中資料主體的金鑰。

三個現成可用命名空間：電子郵件、手機和行動電話。 如果您需要不同的命名空間 (例如收件者自訂欄位)，您可以從&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**&#x200B;建立新的命名空間。

>[!NOTE]
>
>為獲得最佳效能，建議使用立即可用的命名空間。
