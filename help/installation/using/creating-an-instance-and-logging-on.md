---
title: 建立例項並登入
seo-title: 建立例項並登入
description: 建立例項並登入
seo-description: null
page-status-flag: never-activated
uuid: cb1620b3-f6e8-41dc-9142-ac0da65b6f8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: c7395094-c635-45ab-8455-a050f7d16b64
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# 建立例項並登入{#creating-an-instance-and-logging-on}

若要建立新的例項和Adobe Campaign資料庫，請套用下列程式：

1. 建立連接。
1. 登入以建立相關例項。
1. 建立和配置資料庫。

>[!NOTE]
>
>只有內 **部識** 別碼才能執行這些操作。 For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

當Adobe Campaign主控台啟動時，您會存取登入頁面。

要建立新實例，請執行以下步驟：

1. 按一下憑據欄位右上角的連結以訪問連接配置窗口。 此連結可以是現 **[!UICONTROL New...]** 有的例項名稱。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 按一 **[!UICONTROL Add > Connection]** 下並輸入Adobe Campaign應用程式伺服器的標籤和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 指定透過URL連線至Adobe Campaign應用程式伺服器。 使用DNS或電腦的別名或您的IP地址。

   例如，您可以使用類 [`https://<machine>.<domain>.com`](https://machine) 型URL。

   >[!CAUTION]
   >
   >對於連線URL，僅使用下列字元： `[a-z]`、 `[A-Z]``[0-9]` 和破折號(-)或完全停止。

1. 按一 **[!UICONTROL Ok]** 下以確認設定：您現在可以從例項建立程式開始。
1. 在視 **[!UICONTROL Connection settings]** 窗中輸入 **內部登入** 及其密碼，以連線至Adobe Campaign應用程式伺服器。 連接後，您將訪問實例建立嚮導以聲明新實例
1. 在欄位 **[!UICONTROL Name]** 中，輸入實 **例名稱**。 由於此名稱用於生成配置檔案 **config-`<instance>`.xml** ，並用於命令行參數中來標識實例，因此請確保選擇一個不帶特殊字元的短名稱。 例如：電 **子行銷**。

   ![](assets/s_ncs_install_create_instance.png)

   新增至網域名稱的例項名稱不得超過40個字元。 這可讓您限制「Message-ID」標題的大小，並防止訊息被視為垃圾訊息，尤其是SpamAssassin等工具。

1. 在字 **[!UICONTROL DNS masks]** 段中，輸 **入應附加實例的DNS掩碼清單** 。 Adobe Campaign伺服器會使用出現在HTTP請求中的主機名稱來判斷要觸及哪個例項。

   主機名稱包含在字串https:// **和伺服器位址的第** 一個斜線字元 **** /之間。

   您可以定義以逗號分隔的值清單。

   ? 和*字元可用作萬用字元，以取代一或多個字元（DNS、連接埠等）。 例如， **demo*** value將與&quot;https://demo&quot;搭配使用，就像與&quot;https://demo:8080&quot;甚至&quot;https://demo2&quot;搭配使用一樣。

   使用的名稱必須在您的DNS中定義。 您還可以通知Windows中 **c:/windows/system32/drivers/etc/hosts** file和Linux中 **/etc/hosts** file中的DNS名稱與IP地址之間的對應。 因此，您必須修改連接設定以使用此DNS名稱，才能連接到所選實例。

   伺服器必須由此名稱來識別，尤其是在電子郵件中上傳影像時。

   此外，伺服器必須能夠通過此名稱連接自己，如果可能，還必須通過環回地址(127.0.0.1)連接自己，尤其要允許以PDF格式導出報告。

1. 在下拉 **[!UICONTROL Language]** 式清單中，選取例 **項語言**:英文（美國）、英文（英國）、法文或日文。

   本節將說明美國英文與英國英文之 [差異](../../platform/using/adobe-campaign-workspace.md#date-and-time)。

   >[!CAUTION]
   >
   >此步驟後無法修改實例語言。 Adobe Campaign實例不是多語言版本：您無法將介面從語言切換為其他語言。

1. 按一下 **[!UICONTROL Ok]** 確認實例聲明。 註銷並重新登錄以聲明資料庫。

   >[!NOTE]
   >
   >可從命令行建立實例。 For more on this, refer to [Command lines](../../installation/using/command-lines.md).

