---
product: campaign
title: 建立執行個體並登入
description: 建立執行個體並登入
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 1%

---

# 建立執行個體並登入{#creating-an-instance-and-logging-on}



若要建立新執行個體和Adobe Campaign資料庫，請套用以下程式：

1. 建立連線。
1. 登录以创建相關執行個體。
1. 建立和配置資料庫。

>[!NOTE]
>
>**只有內部**&#x200B;識別碼才能執行此操作。如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

當 Adobe Campaign 控制台啟動時，您可以訪問一個登入 頁面。

要建立新執行個體，追隨以下步驟：

1. 按兩下憑據欄位右上角的連結以存取連接配置視窗。 此連結可以是&#x200B;**[!UICONTROL New...]**&#x200B;或現有的執行個體名稱。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下&#x200B;**[!UICONTROL Add > Connection]**&#x200B;並輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 指定透過URL連線至您的Adobe Campaign應用程式伺服器。 請使用電腦的DNS或別名，或您的IP位址。

   例如，您可以使用`https://<machine>.<domain>.com`型別URL。

   >[!CAUTION]
   >
   >對於連接URL，僅使用以下字元： `[a-z]`、 `[A-Z]`、、 `[0-9]` 和破折號 （-） 或句號。

1. 按兩下 **[!UICONTROL Ok]** 以確認設置：您現在可以開始執行個體創建過程。
1. 在 **[!UICONTROL Connection settings]** 窗口中，輸入 **內部** 登入及其連接到 Adobe Campaign 應用程式 伺服器的密碼。 連接后，您可以訪問執行個體创建精靈以聲明新執行個體
1. **[!UICONTROL Name]**&#x200B;在欄位中，輸入&#x200B;**執行個體名稱**。由於此名稱用於生成配置文件&#x200B;**`<instance>`配置.xml**&#x200B;並在命令行參數中用於標識執行個體，因此請確保選擇不含特殊字元的短名稱。例如： **電子行銷**。

   ![](assets/s_ncs_install_create_instance.png)

   添加到域名的執行個體名稱不得超過40個字符。 這使您可以限制「新增訊息-ID」標頭的大小，並防止郵件被視為垃圾郵件，尤其是通過SpamAssassin等工具。

1. 在 **[!UICONTROL DNS masks]** 欄位中，輸入 **應附加執行個體的 DNS 掩码** 清單。 Adobe Campaign伺服器會使用HTTP請求中顯示的主機名稱，來判斷要連絡的執行個體。

   主機名稱包含在字串&#x200B;**https://**&#x200B;和伺服器位址的第一個斜線字元&#x200B;**/**&#x200B;之間。

   您可以定義以逗號分隔的值清單。

   此？ 和 &#42; 字元可以作為通配符來替換一個或多個字元（DNS、連接埠等）。 對於執行個體， **演示&#42;** 值將與“https://demo”一起使用，就像它與“https://demo:8080”和平均“https://demo2”一樣。

   使用的名稱必須在您的 DNS 中定義。 您還可以在Windows中的c：/windows/system32/drivers/etc/hosts **檔和** Linux中的/etc/hosts **檔中通知** DNS名稱和IP地址之間的對應關係。因此，您必須修改連接設置以使用此 DNS 名稱才能連接到所選執行個體。

   伺服器必須以此名稱標識，特別是在電子郵件中上載影像時。

   此外，伺服器必須能夠通過此名稱連接到自身，如果可能，還可以通過環回位址 - 127.0.0.1 - 連接到自身，特別是允許以 PDF 格式導出報告。

1. 在 **[!UICONTROL Language]** 下拉清單中，選擇 **執行個體語言**：英文（美國）、英文（英國）、法文或日文。

   美式英文與英式英文之間的差異在[本節](../../platform/using/adobe-campaign-workspace.md#date-and-time)中說明。

   >[!CAUTION]
   >
   >執行個體語言在此步驟後無法修改。 Adobe Campaign例項並非多語言版本：您無法將介面從語言切換為其他語言。

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以確認執行個體宣告。 登出再登入，以宣告資料庫。

   >[!NOTE]
   >
   >可以從命令列建立例證。 有關詳細資訊，請參閱 [命令行](../../installation/using/command-lines.md)。
