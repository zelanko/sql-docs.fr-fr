---
title: "Mesurer l’élément (CSDLBI) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: bfbc9274-053a-421a-bb81-2095bba710be
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ee1d1fdcdd17b9ade86e9f9acc6b6a41ed9cc930
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="measure-element-csdlbi"></a>Élément Measure (CSDLBI)
  L'élément Measure est un type complexe qui repose sur l'élément Property CSDL. Les annotations CSDLBI ajoutent des attributs qui prennent en charge la définition de formules complexes à utiliser dans les modèles de données Business Intelligence.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau ci-dessous répertorie les éléments et les attributs qui définissent l'élément Measure, en plus de tous les attributs applicables à l'élément Property.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Kpi|Non|Élément requis uniquement pour les mesures utilisées comme indicateur de performance clé. Toutes les mesures sont des indicateurs de performance clés, mais tous les indicateurs de performance clés doivent être basés sur la définition d'une mesure.<br /><br /> [Élément KPI &#40; CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md)|  
|IsSimpleMeasure|Non|Valeur true/false qui indique si la formule utilisée dans la mesure est l'un des agrégations simples (SUM, COUNT, MIN, MAX, AVG, DistinctCount).<br /><br /> La valeur par défaut est true.|  
  
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
 [Informations techniques de référence pour les Annotations BI au langage CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  

