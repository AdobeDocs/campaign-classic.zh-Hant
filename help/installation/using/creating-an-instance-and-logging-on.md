---
product: campaign
title: 建立執行個體並登入
description: 建立執行個體並登入
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 5%

---

# 建立執行個體並登入{#creating-an-instance-and-logging-on}

![](../../assets/v7-only.svg)

要建立新實例和Adobe Campaign資料庫，請應用以下過程：

1. 建立連接。
1. 登錄以建立相關實例。
1. 建立及設定資料庫.

>[!NOTE]
>
>僅 **內部** 標識符可以執行這些操作。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

啟動Adobe Campaign控制台時，您將訪問登錄頁。

要建立新實例，請執行以下步驟：

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。 此連結可以是 **[!UICONTROL New...]** 或現有實例名稱。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下 **[!UICONTROL Add > Connection]** 並輸入Adobe Campaign應用伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通過URL指定到Adobe Campaign應用程式伺服器的連接。 使用DNS或電腦的別名或IP地址。

   例如，您可以使用 `https://<machine>.<domain>.com` 鍵。

   >[!CAUTION]
   >
   >對於連接URL，僅使用以下字元： `[a-z]`。 `[A-Z]`。 `[0-9]` 和短划線(-)或句號。

1. 按一下 **[!UICONTROL Ok]** 確認設定：現在，您可以從實例建立過程開始。
1. 在 **[!UICONTROL Connection settings]** ，輸入 **內部** 登錄及其密碼，以連接到Adobe Campaign應用伺服器。 連接後，可以訪問實例建立嚮導來聲明新實例
1. 在 **[!UICONTROL Name]** ，輸入 **實例名稱**。 由於此名稱用於生成配置檔案 **配置`<instance>`.xml** 並用於命令行參數中以標識實例，確保選擇不帶特殊字元的短名稱。 例如： **電子營銷**。

   ![](assets/s_ncs_install_create_instance.png)

   添加到域名的實例名稱不能超過40個字元。 這樣，您就可以限制「Message-ID」報頭的大小，並防止郵件被視為垃圾郵件，尤其是通過SpamAssassin等工具。

1. 在 **[!UICONTROL DNS masks]** ，輸入 **DNS掩碼清單** 實例應附加到的。 Adobe Campaign伺服器使用HTTP請求中顯示的主機名來確定要訪問哪個實例。

   主機名包含在字串之間 **https://** 第一個斜槓字元 **/** 的子菜單。

   可以定義用逗號分隔的值清單。

   此 ? 和 &#42; 字元可用作通配符以替換一個或多個字元（DNS、埠等）。 例如， **演示&#42;** value將與&quot;https://demo&quot;一起使用，與&quot;https://demo:8080&quot;甚至&quot;https://demo2&quot;一樣。

   使用的名稱必須在DNS中定義。 您還可以通知DNS名稱與IP地址之間的通信 **c:/windows/system32/drivers/etc/hosts** 檔案 **/etc/hosts** 檔案。 因此，必須修改連接設定才能使用此DNS名稱，才能連接到所選實例。

   伺服器必須由此名稱標識，尤其是用於在電子郵件中上載影像。

   此外，伺服器必須能夠通過此名稱和環回地址（如果可能）連接到自身 — 127.0.0.1 — 特別是允許以PDF格式導出報告。

1. 在 **[!UICONTROL Language]** 下拉清單，選擇 **實例語言**:英語（美國）、英語（英國）、法語或日語。

   有關美國英語與英國英語之差異，請參閱 [此部分](../../platform/using/adobe-campaign-workspace.md#date-and-time)。

   >[!CAUTION]
   >
   >此步驟後無法修改實例語言。 Adobe Campaign實例不會多語言：無法將介面從語言切換到其他語言。

1. 按一下 **[!UICONTROL Ok]** 確認實例聲明。 註銷並重新登錄以聲明資料庫。

   >[!NOTE]
   >
   >可以從命令行建立實例。 有關此內容的詳細資訊，請參閱 [命令行](../../installation/using/command-lines.md)。
