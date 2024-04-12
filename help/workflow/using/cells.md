---
product: campaign
title: 儲存格
description: 儲存格
feature: Workflows, Targeting Activity
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 8%

---

# 儲存格{#cells}



此 **[!UICONTROL Cells]** 活動會以資料欄的形式，提供各種子集的檢視。 它有助於子集操作，也設計為鼓勵個人化可能性。

![](assets/wf_split_cells.png)

此活動可設定為根據使用者需求輸入特定引數。 依預設，每個子集的詳細資訊會透過在專用視窗中顯示 **[!UICONTROL Selection]** 和 **[!UICONTROL Advanced]** 索引標籤。 在下列範例中，表單已修改： **[!UICONTROL Data]** 索引標籤已新增，以啟用每個子集的優惠方案與優先順序層級的關聯。

![](assets/wf_split_cells_with_customization.png)

針對此設定，已將以下資訊新增至工作流程表單(在 **[!UICONTROL Administration > Configurations > Input forms]** Adobe Campaign節點)：

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

Adobe Campaign中的登入表單個人化是保留給專家使用者。 如需詳細資訊，請參閱本[區段](../../configuration/using/identifying-a-form.md)。
