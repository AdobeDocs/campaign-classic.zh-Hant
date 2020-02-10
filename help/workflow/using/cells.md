---
title: 儲存格
seo-title: 儲存格
description: 儲存格
seo-description: null
page-status-flag: never-activated
uuid: 1b18928f-04e1-4268-ab8e-ff74d78599de
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: f7187d42-56e9-4681-b172-22abd43ecd29
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 儲存格{#cells}

該 **[!UICONTROL Cells]** 活動以資料列的形式提供了各種子集的視圖。 它有助於子集操作，也旨在鼓勵個人化的可能性。

![](assets/wf_split_cells.png)

您可以設定此活動，以根據使用者需求輸入特定參數。 依預設，每個子集的詳細資料會透過和標籤在專用視窗中詳 **[!UICONTROL Selection]** 細 **[!UICONTROL Advanced]** 說明。 在下列範例中，表單已修改：已新 **[!UICONTROL Data]** 增標籤，以啟用選件與每個子集之優先順序層級的關聯。

![](assets/wf_split_cells_with_customization.png)

對於此設定，下列資訊已新增至工作流程表單(位於Adobe Campaign **[!UICONTROL Administration > Configurations > Input forms]** 樹狀結構的節點):

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

Adobe Campaign中的登入表單個人化保留給專家使用者。 For more on this, refer to this [section](../../configuration/using/identifying-a-form.md).
