---
title: 交貨報告
seo-title: 交貨報告
description: 交貨報告
seo-description: null
page-status-flag: never-activated
uuid: 83ea834e-08f7-441b-8f15-a25ec07c4aab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: cc832666-ad18-49ce-afcc-f9169b683ae8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 18309c190c351cc57f7af24f48b2a772c1840319

---


# 人員／人員與收件者 {#person-people-and-recipients}

此範例可協助您瞭解Adobe Campaign中的人員／人員與收件者之間的差異。 我們會傳送傳送給多人，以強調人與收件者之間的差異，同時詳細說明下列指標的計算方法：

* **[!UICONTROL Clicks]**
* **[!UICONTROL Distinct clicks for the population reached]**
* **[!UICONTROL Distinct opens for the population reached]**
* **[!UICONTROL Estimation of forwards]**
* **[!UICONTROL Raw reactivity]**

>[!NOTE]
>
>這些指標用於報 **[!UICONTROL Tracking indicators]** 告。 For more on this, refer to [Tracking indicators](../../reporting/using/delivery-reports.md#tracking-indicators).

傳送會新增三個連結。 它會傳送給4位收件者：

![](assets/s_ncs_user_indicators_example_1.png)

* **[!UICONTROL John Davis]** :此收件者不會開啟電子郵件（因此不會按任何連結）。
* **[!UICONTROL Marie Stuart]** :開啟電子郵件，但不點選任何連結。
* **[!UICONTROL Florian David]** :開啟電子郵件並按9次連結。 他還會將電子郵件轉寄給開啟並按兩下的人。
* **[!UICONTROL Henry Macdonald]** :此收件者已將其網際網路瀏覽器設定為拒絕Cookie。 他開啟電子郵件並點按連結4次。

傳回下列追蹤記錄：

![](assets/s_ncs_user_indicators_example_2.png)

為了更清楚地瞭解人員和收件者的計數方式，我們將分析每個個人檔案的記錄檔。

## 步驟1:約翰 {#step-1--john}

**[!UICONTROL John Davis]** 不開啟電子郵件（因此不點選任何連結）。

![](assets/s_ncs_user_indicators_example_8.png)

由於John既未開啟也未點按電子郵件，因此他不會出現在記錄檔中。

**中間計算：**

|  | 按下的收件者 | 點擊者 | 開啟的收件者 |
|---|---|---|---|
| 約翰 | - | - | - |
| 中級總計 | 0 | 0 | 0 |

## 步驟2:瑪麗 {#step-2--marie}

**[!UICONTROL Marie Stuart]** 開啟電子郵件，但不點選任何連結。

![](assets/s_ncs_user_indicators_example_7.png)

Marie的開啟狀態顯示在以下日誌中：

![](assets/s_ncs_user_indicators_example_4bis.png)

開啟被指派給收件者：瑪麗。 因此，Adobe Campaign會新增收件者至計數。

**中間計算：**

|  | 按下的收件者 | 點擊者 | 開啟的收件者 |
|---|---|---|---|
| 約翰 | - | - | - |
| 瑪麗 | - | - | +1 |
| 中級總計 | 0 | 0 | 1 |

## 步驟3:弗洛里安 {#step-3--florian}

**[!UICONTROL Florian David]** 開啟電子郵件並按9次連結。 他還會將電子郵件轉寄給開啟並按兩下的人。

![](assets/s_ncs_user_indicators_example_9.png)

Florian的動作（按一下即可開啟，按9下即可完成）會顯示在下列記錄檔中：

![](assets/s_ncs_user_indicators_example_3bis.png)

**收件者**:開啟和點按會指派給相同的收件者(Florian)。 由於此收件者與前一個(Marie)不同，Adobe Campaign會新增一個收件者至計數。

人員：由於此收件者的瀏覽器接受Cookie，因此我們可看到相同的識別碼(UUID)已指派給所有點按記錄： **`fe37a503 [...]`**。 Adobe Campaign會正確地將這些點按識別為屬於同一人。 新人員會加入計數。

**中間計算：**

|  | 按下的收件者 | 點擊者 | 開啟的收件者 |
|---|---|---|---|
| 約翰 | - | - | - |
| 瑪麗 | - | - | +1 |
| 弗洛里安 | +1 | +1 | +1 |
| 中級總計 | 1 | 1 | 2 |

下列記錄檔與Florian將電子郵件轉寄給的人所開啟和點按兩次相符：

![](assets/s_ncs_user_indicators_example_6bis.png)

**收件者**:其開啟和點按次數會指派給轉送電子郵件的收件者(Florian)。 由於此收件者已被計算過，因此收件者計數仍維持不變。

![](assets/s_ncs_user_indicators_example_12.png)

**人物**:關於點按，我們可看到相同的識別碼(UUID)已指派給所有記錄： **`9ab648f9 [...]`**。 此識別碼尚未計算。 因此，會在計數中新增一個人。

![](assets/s_ncs_user_indicators_example_13.png)

**中間計算：**

|  | 按下的收件者 | 點擊者 | 開啟的收件者 |
|---|---|---|---|
| 約翰 | - | - | - |
| 瑪麗 | - | - | +1 |
| 弗洛里安 | +1 | +1 | +1 |
| 未知人物 | - | +1 | - |
| 中級總計 | 1 | 2 | 2 |

## 步驟4:亨利 {#step-4--henry}

**[!UICONTROL Henry Macdonald]** 已設定其網際網路瀏覽器拒絕Cookie。 他開啟電子郵件並點按連結4次。

![](assets/s_ncs_user_indicators_example_10.png)

Henry所執行的開啟和4次點按次數會顯示在下列記錄中：

![](assets/s_ncs_user_indicators_example_5bis.png)

**收件者**:開啟和點按會指派給相同的收件者(Henry)。 由於此收件者尚未被計算，Adobe Campaign會將收件者新增至計數。

**人物**:由於Henry的瀏覽器不接受Cookie，因此每次點按都會產生新的識別碼(UUID)。 4次點按中，每次都會被解讀為來自不同的人。 由於這些識別碼尚未被計算，因此會將其新增至計數。

**中間計算：**

|  | 按下的收件者 | 點擊者 | 開啟的收件者 |
|---|---|---|---|
| 約翰 | - | - | - |
| 瑪麗 | - | - | +1 |
| 弗洛里安 | +1 | +1 | +1 |
| 未知人物 | - | +1 | - |
| 亨利 | +1 | +4 | +1 |
| 中級總計 | 2 | 6 | 3 |

## 摘要 {#summary}

在傳送層級，我們有下列結果：

![](assets/s_ncs_user_indicators_example.png)

* **[!UICONTROL Clicks]** （點按的收件者）:2
* **[!UICONTROL Distinct clicks for the population reached]** （點擊的人員）:6
* **[!UICONTROL Distinct opens for the population reached]** （開啟的收件者）:3

前向反應性的計算和估算如下：

![](assets/s_ncs_user_indicators_example11.png)

* **[!UICONTROL Estimation of forwards]** = **B - A** （因此6 - 2 = 4）
* **[!UICONTROL Raw reactivity]** = **A / C** （因此2 / 3 = 66,67%）

>[!NOTE]
>
>在下列公式中：
>
>* A代表指 **[!UICONTROL Clicks]** 標（點按的收件者）。
>* B代表指 **[!UICONTROL Distinct clicks for the population reached]** 標（點按的人員）。
>* C代表指 **[!UICONTROL Distinct opens for the population reached]** 標（開啟的收件者）。