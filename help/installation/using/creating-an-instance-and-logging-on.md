---
product: campaign
title: 建立執行個體並登入
description: 建立執行個體並登入
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 2%

---

# 建立執行個體並登入{#creating-an-instance-and-logging-on}



若要創建新的執行個體和Adobe Campaign資料庫，請應用以下過程：

1. 建立連接。
1. 登录以创建相關執行個體。
1. 建立和配置資料庫。

>[!NOTE]
>
>**只有內部**&#x200B;識別碼才能執行此操作。如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

當 Adobe Campaign 控制台啟動時，您可以訪問一個登入 頁面。

若要建立新執行個體，請遵循下列步驟：

1. 按一下認證欄位右上角的連結以存取連線設定視窗。 此連結可以是 **[!UICONTROL New...]** 或現有的執行個體名稱。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下 **[!UICONTROL Add > Connection]** 並輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 指定透過URL連線至您的Adobe Campaign應用程式伺服器。 使用計算機的 DNS 或別名，或者使用您的 IP 位址。

   例如，可以使用 `https://<machine>.<domain>.com` 類型URL。

   >[!CAUTION]
   >
   >對於連接URL，僅使用以下字元： `[a-z]`、 `[A-Z]`、、 `[0-9]` 和破折號 （-） 或句號。

1. 按兩下 **[!UICONTROL Ok]** 以確認設置：您現在可以開始執行個體創建過程。
1. 在 **[!UICONTROL Connection settings]** 窗口中，輸入 **內部** 登入及其連接到 Adobe Campaign 應用程式 伺服器的密碼。 連接后，您可以訪問執行個體创建精靈以聲明新執行個體
1. **[!UICONTROL Name]**&#x200B;在欄位中，輸入&#x200B;**執行個體名稱**。由於此名稱用於生成配置文件&#x200B;**`<instance>`配置.xml**&#x200B;並在命令行參數中用於標識執行個體，因此請確保選擇不含特殊字元的短名稱。例如： **電子行銷**.

   ![](assets/s_ncs_install_create_instance.png)

   新增到網域名稱的執行個體名稱不能超過40個字元。 這可讓您限制「訊息ID」標頭的大小，並防止將訊息視為垃圾訊息，尤其是SpamAssassin等工具。

1. 在 **[!UICONTROL DNS masks]** 欄位，輸入 **DNS遮罩清單** 應該附加執行個體的目標。 Adobe Campaign伺服器會使用HTTP請求中顯示的主機名稱，來判斷要連絡的執行個體。

   主機名稱包含在字串之間 **https://** 和第一個斜線字元 **/** 伺服器位址的。

   您可以定義一清單連串以逗号分隔的值。

   該 ？ 和 &#42; 字元可以作為通配符來替換一個或多個字元（DNS、連接埠等）。 對於執行個體， **演示&#42;** 值將與“https://demo”一起使用，就像它與“https://demo:8080”和平均“https://demo2”一樣。

   使用的名稱必須在您的 DNS 中定義。 您還可以在Windows中的c：/windows/system32/drivers/etc/hosts **檔和** Linux中的/etc/hosts **檔中通知** DNS名稱和IP地址之間的對應關係。因此，您必須修改連接設置以使用此 DNS 名稱才能連接到所選執行個體。

   伺服器必須以此名稱識別，尤其是在電子郵件中上傳影像時。

   此外，伺服器必須能夠使用此名稱連線到本身，如果可能的話，也必須使用回送位址127.0.0.1，尤其是要允許以PDF格式匯出報表。

1. 在 **[!UICONTROL Language]** 從下拉式清單中選取 **例項語言**：英文（美國）、英文（英國）、法文或日文。

   美式英文與英式英文的差異說明於 [本節](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >執行個體語言在此步驟後無法修改。 Adobe Campaign例項並非多語言版本：您無法將介面從語言切換為其他語言。

1. 按兩下 **[!UICONTROL Ok]** 以確認執行個體聲明。 註銷並重新登錄以聲明資料庫。

   >[!NOTE]
   >
   >可以從命令行创建執行個體。 有關詳細資訊，請參閱 [命令行](../../installation/using/command-lines.md)。
