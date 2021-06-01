---
product: campaign
title: 建立執行個體並登入
description: 建立執行個體並登入
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 5%

---

# 建立執行個體並登入{#creating-an-instance-and-logging-on}

若要建立新例項和Adobe Campaign資料庫，請套用下列程式：

1. 建立連線。
1. 登入以建立相關例項。
1. 建立及設定資料庫.

>[!NOTE]
>
>只有&#x200B;**內部**&#x200B;標識符可以執行這些操作。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

啟動Adobe Campaign主控台時，您會存取登入頁面。

若要建立新例項，請遵循下列步驟：

1. 按一下認證欄位右上角的連結，以存取連線設定視窗。 此連結可以是&#x200B;**[!UICONTROL New...]**&#x200B;或現有實例名稱。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下&#x200B;**[!UICONTROL Add > Connection]** ，然後輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 透過URL指定與Adobe Campaign應用程式伺服器的連線。 使用電腦的DNS、別名或IP地址。

   例如，您可以使用[`https://<machine>.<domain>.com`](https://myserver.adobe.com)類型URL。

   >[!CAUTION]
   >
   >對於連線URL，僅使用下列字元：`[a-z]`、`[A-Z]`、`[0-9]`和破折號(-)或完全停止。

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以確認設定：您現在可以從執行個體建立程式開始。
1. 在&#x200B;**[!UICONTROL Connection settings]**&#x200B;視窗中，輸入&#x200B;**internal**&#x200B;登入資訊及其密碼以連線至Adobe Campaign應用程式伺服器。 連接後，您將訪問實例建立嚮導以聲明新實例
1. 在&#x200B;**[!UICONTROL Name]**&#x200B;欄位中，輸入&#x200B;**實例名稱**。 由於此名稱用於生成配置檔案&#x200B;**config-`<instance>`.xml**，並用於命令行參數中以標識實例，因此請確保選擇一個短名稱，不帶特殊字元。 例如：**eMarketing**。

   ![](assets/s_ncs_install_create_instance.png)

   新增至網域名稱的執行個體名稱不得超過40個字元。 這可讓您限制「Message-ID」標題的大小，並防止郵件被視為垃圾訊息，尤其是透過SpamAssassin等工具。

1. 在&#x200B;**[!UICONTROL DNS masks]**&#x200B;欄位中，輸入應附加實例的&#x200B;**DNS掩碼清單**。 Adobe Campaign伺服器會使用HTTP要求中顯示的主機名稱，來判斷要存取的執行個體。

   主機名包含在伺服器地址的字串&#x200B;**https://**&#x200B;和第一個斜線字元&#x200B;**/**&#x200B;之間。

   您可以定義以逗號分隔的值清單。

   ? 和*字元可作為萬用字元來取代一或多個字元（DNS、連接埠等）。 例如，**demo***&#x200B;值將與&quot;https://demo&quot;搭配使用，如同與&quot;https://demo:8080&quot;甚至&quot;https://demo2&quot;搭配使用。

   使用的名稱必須在DNS中定義。 您還可以在Windows中的&#x200B;**c:/windows/system32/drivers/etc/hosts**&#x200B;檔案和Linux中的&#x200B;**/etc/hosts**&#x200B;檔案中通知DNS名稱與IP地址之間的對應。 因此，您必須修改連接設定以使用此DNS名稱，才能連接到您選擇的實例。

   伺服器必須以此名稱識別，尤其是用於上傳電子郵件中的影像。

   此外，伺服器必須能夠通過此名稱（如果可能的話）通過環回地址(127.0.0.1)連接到自身，尤其是允許以PDF格式導出報告。

1. 在&#x200B;**[!UICONTROL Language]**&#x200B;下拉式清單中，選取&#x200B;**例項語言**:英文（美國）、英文（英國）、法文或日文。

   [本節](../../platform/using/adobe-campaign-workspace.md#date-and-time)說明美國英語和英國英語之間的差異。

   >[!CAUTION]
   >
   >此步驟之後無法修改執行個體語言。 Adobe Campaign例項不會多語言：您無法將介面從語言切換為其他語言。

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以確認執行個體聲明。 註銷並重新登錄以聲明資料庫。

   >[!NOTE]
   >
   >可以從命令行建立實例。 有關詳細資訊，請參閱[命令行](../../installation/using/command-lines.md)。
