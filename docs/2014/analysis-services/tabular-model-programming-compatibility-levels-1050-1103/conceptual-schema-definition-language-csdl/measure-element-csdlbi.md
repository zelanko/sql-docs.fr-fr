---
title: Mesurer, élément (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfbc9274-053a-421a-bb81-2095bba710be
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0c3a2f2ef1c1dcc80e0b8ac9cb68ce5d5694d104
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224015"
---
# <a name="measure-element-csdlbi"></a>Élément Measure (CSDLBI)
  L'élément Measure est un type complexe qui repose sur l'élément Property CSDL. Les annotations CSDLBI ajoutent des attributs qui prennent en charge la définition de formules complexes à utiliser dans les modèles de données Business Intelligence.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau ci-dessous répertorie les éléments et les attributs qui définissent l'élément Measure, en plus de tous les attributs applicables à l'élément Property.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Kpi|non|Élément requis uniquement pour les mesures utilisées comme indicateur de performance clé. Toutes les mesures sont des indicateurs de performance clés, mais tous les indicateurs de performance clés doivent être basés sur la définition d'une mesure.<br /><br /> [Élément KPI &#40;CSDLBI&#41;](kpi-element-csdlbi.md)|  
|IsSimpleMeasure|non|Valeur true/false qui indique si la formule utilisée dans la mesure est l'un des agrégations simples (SUM, COUNT, MIN, MAX, AVG, DistinctCount).<br /><br /> La valeur par défaut est true.|  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre deux mesures de l'exemple de modèle tabulaire AdventureWorks. La deuxième mesure a été convertie en un indicateur de performance clé, en ajoutant des élément KPI.  
  
```  
  
<Property   
    Name="Order_Lines_Count"   
    Type="Int64">  
<bi:Measure   
    Caption="Order Lines Count"   
    ReferenceName="Order Lines Count"   
    Width="0"   
    IsSimpleMeasure="false" />  
</Property>  
  
<Property   
    Name="Total_Current_Quarter_Sales_Performance"   
    Type="Double">  
<bi:Measure   
    Caption="Total Current Quarter Sales Performance"   
    ReferenceName="Total Current Quarter Sales Performance"   
    Width="0"   
    IsSimpleMeasure="false">  
    <bi:Kpi   
    StatusGraphic="Three Signs Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="Measures___Total_Current_Quarter_Sales_Performance_Goal_" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="Measures___Total_Current_Quarter_Sales_Performance_Status_" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
```  
  
## <a name="example"></a>Exemple  
 **Multidimensiona ;**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre une mesure du cube Contoso Operations utilisée en tant qu'indicateur de performance clés.  
  
```  
  
<Property   
    Name="Sum_of_SalesAmount"   
    Type="Decimal" Precision="19" Scale="4">  
<Documentation>  
<Summary>KPI Description</Summary>  
</Documentation>  
<bi:Measure   
    Caption="Sum of SalesAmount"   
    ReferenceName="Sum of SalesAmount"   
    FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
<bi:Kpi   
    StatusGraphic="Three Circles Colored">  
    <bi:KpiGoal>  
        <bi:PropertyRef Name="v_Sum_of_SalesAmount_Goal" />  
    </bi:KpiGoal>  
    <bi:KpiStatus>  
        <bi:PropertyRef Name="v_Sum_of_SalesAmount_Status" />  
    </bi:KpiStatus>  
</bi:Kpi>  
</bi:Measure>  
</Property>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations techniques de référence sur les annotations pour le décisionnel dans CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
