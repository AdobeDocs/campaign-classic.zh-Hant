---
solution: Campaign Classic
product: campaign
title: 建立執行個體並登入
description: 建立執行個體並登入
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 5%

---

# 建立執行個體並登入{#creating-an-instance-and-logging-on}

要建立新實例和Adobe Campaign資料庫，請應用以下過程：

1. 建立連接。
1. 登入以建立相關例項。
1. 建立及設定資料庫.

>[!NOTE]
>
>只有&#x200B;**internal**&#x200B;標識符可以執行這些操作。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

啟動Adobe Campaign控制台時，您將訪問登錄頁。

要建立新實例，請執行以下步驟：

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。 此連結可以是&#x200B;**[!UICONTROL New...]**&#x200B;或現有的例項名稱。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下&#x200B;**[!UICONTROL Add > Connection]**&#x200B;並輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 指定透過URL連線至您的Adobe Campaign應用程式伺服器。 使用DNS或電腦的別名或您的IP地址。

   例如，您可以使用[`https://<machine>.<domain>.com`](https://myserver.adobe.com)類型URL。

   >[!CAUTION]
   >
   >對於連線URL，僅使用下列字元：`[a-z]`、`[A-Z]`、`[0-9]`和破折號(-)或完全停止。

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;確認設定：您現在可以從例項建立程式開始。
1. 在&#x200B;**[!UICONTROL Connection settings]**&#x200B;窗口中，輸入&#x200B;**internal**&#x200B;登錄及其密碼以連接到Adobe Campaign應用程式伺服器。 連接後，您將訪問實例建立嚮導以聲明新實例
1. 在&#x200B;**[!UICONTROL Name]**&#x200B;欄位中，輸入&#x200B;**例項名稱**。 由於此名稱用於生成配置檔案&#x200B;**config-`<instance>`.xml**，並用於命令行參數中以識別實例，請確保選擇一個不帶特殊字元的短名稱。 例如：**eMarketing**。

   ![](assets/s_ncs_install_create_instance.png)

   新增至網域名稱的例項名稱不得超過40個字元。 這可讓您限制「Message-ID」標題的大小，並防止訊息被視為垃圾訊息，尤其是SpamAssassin等工具。

1. 在&#x200B;**[!UICONTROL DNS masks]**&#x200B;欄位中，輸入應將實例附加到的&#x200B;**DNS掩碼清單。** Adobe Campaign伺服器使用HTTP請求中顯示的主機名來確定要訪問的實例。

   主機名包含在伺服器地址的字串&#x200B;**https://**&#x200B;和第一個斜線字元&#x200B;**/**&#x200B;之間。

   您可以定義以逗號分隔的值清單。

   ? 和*字元可用作萬用字元，以取代一或多個字元（DNS、連接埠等）。 例如，**demo***&#x200B;值將與&quot;https://demo&quot;搭配使用，就像與&quot;https://demo:8080&quot;甚至&quot;https://demo2&quot;一樣。

   使用的名稱必須在您的DNS中定義。 您還可以在Windows的&#x200B;**c:/windows/system32/drivers/etc/hosts**&#x200B;檔案和Linux的&#x200B;**/etc/hosts**&#x200B;檔案中通知DNS名稱與IP地址的對應。 因此，您必須修改連接設定以使用此DNS名稱，才能連接到所選實例。

   伺服器必須由此名稱來識別，尤其是在電子郵件中上傳影像時。

   此外，伺服器必須能夠通過此名稱連接自己，如果可能，還必須通過環回地址(127.0.0.1)連接自己，尤其要允許以PDF格式導出報告。

1. 在&#x200B;**[!UICONTROL Language]**&#x200B;下拉式清單中，選取&#x200B;**例項語言**:英文（美國）、英文（英國）、法文或日文。

   本節[說明美國英文與英國英文的差異。](../../platform/using/adobe-campaign-workspace.md#date-and-time)

   >[!CAUTION]
   >
   >此步驟後無法修改實例語言。 Adobe Campaign實例不會多語言：您無法將介面從語言切換為其他語言。

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;確認實例聲明。 註銷並重新登錄以聲明資料庫。

   >[!NOTE]
   >
   >可從命令行建立實例。 有關詳細資訊，請參閱[命令行](../../installation/using/command-lines.md)。
