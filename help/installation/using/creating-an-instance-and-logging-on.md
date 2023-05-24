---
product: campaign
title: 建立執行個體並登入
description: 建立執行個體並登入
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 5%

---

# 建立執行個體並登入{#creating-an-instance-and-logging-on}



若要建立新執行個體和Adobe Campaign資料庫，請套用下列程式：

1. 建立連線。
1. 登入以建立相關執行個體。
1. 建立及設定資料庫.

>[!NOTE]
>
>僅限 **內部** 識別碼可執行這些操作。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

啟動Adobe Campaign主控台時，您可以存取登入頁面。

若要建立新執行個體，請遵循下列步驟：

1. 按一下認證欄位右上角的連結，即可存取連線設定視窗。 此連結可以是 **[!UICONTROL New...]** 或現有執行個體名稱。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一下 **[!UICONTROL Add > Connection]** 並輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 透過URL指定與您的Adobe Campaign應用程式伺服器的連線。 使用電腦的DNS或別名，或您的IP位址。

   例如，您可以使用 `https://<machine>.<domain>.com` 輸入URL。

   >[!CAUTION]
   >
   >對於連線URL，僅使用下列字元： `[a-z]`， `[A-Z]`， `[0-9]` 和破折號(-)或句號。

1. 按一下 **[!UICONTROL Ok]** 若要確認設定：您現在可以開始執行個體建立程式。
1. 在 **[!UICONTROL Connection settings]** 視窗，輸入 **內部** 登入及其密碼以連線至Adobe Campaign應用程式伺服器。 連線後，您可以存取執行個體建立精靈來宣告新的執行個體
1. 在 **[!UICONTROL Name]** 欄位，輸入 **執行個體名稱**. 由於此名稱用於產生設定檔案 **config-`<instance>`.xml** 和會用於命令列引數中以識別例項，請務必選擇不含特殊字元的簡短名稱。 例如： **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   新增到網域名稱的執行個體名稱不能超過40個字元。 這可讓您限制「Message-ID」標頭的大小，並防止將郵件視為垃圾郵件，尤其是SpamAssassin等工具。

1. 在 **[!UICONTROL DNS masks]** 欄位，請輸入 **DNS遮罩清單** 應附加執行個體的目標。 Adobe Campaign伺服器會使用HTTP請求中顯示的主機名稱來判斷要連絡的執行個體。

   主機名稱包含在字串之間 **https://** 和第一個斜線字元 **/** 伺服器位址的。

   您可以定義以逗號分隔的值清單。

   此 ? 和 &#42; 字元可用作萬用字元，以取代一個或多個字元（DNS、連線埠等）。 例如， **示範&#42;** 值將與「https://demo」搭配使用，就像與「https://demo:8080」甚至「https://demo2」搭配使用一樣。

   使用的名稱必須在您的DNS中定義。 您還可以通知DNS名稱和IP位址之間的對應 **c：/windows/system32/drivers/etc/hosts** Windows中的檔案和 **/etc/hosts** Linux中的檔案。 因此，您必須修改連線設定以使用此DNS名稱，才能連線到您選擇的執行個體。

   伺服器必須以此名稱識別，尤其是在電子郵件中上傳影像時。

   此外，伺服器必須能夠使用此名稱連線到自身，如果可能的話，還要使用回送位址127.0.0.1，尤其是要允許報表以PDF格式匯出。

1. 在 **[!UICONTROL Language]** 下拉式清單，選取 **執行個體語言**：英文（美國）、英文（英國）、法文或日文。

   美式英文與英式英文的差異詳見 [本節](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >此步驟之後無法修改執行個體語言。 Adobe Campaign執行個體不是多語言的：您無法將介面從語言切換為其他語言。

1. 按一下 **[!UICONTROL Ok]** 以確認執行個體宣告。 登出再登入以宣告資料庫。

   >[!NOTE]
   >
   >可以從命令列建立例證。 有關詳細資訊，請參閱 [命令列](../../installation/using/command-lines.md).
