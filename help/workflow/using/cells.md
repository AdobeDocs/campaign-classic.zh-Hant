---
product: campaign
title: 儲存格
description: 儲存格
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 8%

---

# 儲存格{#cells}

![](../../assets/common.svg)

此 **[!UICONTROL Cells]** 活動以資料欄的形式提供各種子集的視圖。 它有助於進行子集操作，也旨在鼓勵個人化的可能性。

![](assets/wf_split_cells.png)

可以根據用戶需求配置此活動以輸入特定參數。 依預設，每個子集的詳細資訊會透過 **[!UICONTROL Selection]** 和 **[!UICONTROL Advanced]** 頁簽。 在以下範例中，已修改表單：a **[!UICONTROL Data]** 已新增索引標籤，以啟用選件與每個子集之優先順序層級的關聯。

![](assets/wf_split_cells_with_customization.png)

針對此設定，下列資訊已新增至工作流程表單(位於 **[!UICONTROL Administration > Configurations > Input forms]** Adobe Campaign樹節點):

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

Adobe Campaign中的登入表單個人化已保留給專家使用者。 如需詳細資訊，請參閱本[區段](../../configuration/using/identifying-a-form.md)。
