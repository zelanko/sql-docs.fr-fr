---
title: "Élément PropertyRef (CSDLBI) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 8299efb9-e224-4a82-bdfc-a74ec92f8711
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bebac79077aed4065b9468396740462d9844fda6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="propertyref-element-csdlbi"></a>Élément PropertyRef (CSDLBI)
  L'élément PropertyRef est un type simple qui référence une colonne qui fournit une valeur requise par une autre propriété.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément PropertyRef.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Nom|Oui|Chaîne qui contient le nom de la propriété qui est la cible de la référence.|  
  
## <a name="propertyrefs-element"></a>Élément PropertyRefs  
 PropertyRefs est un type complexe qui définit une collection de propriétés, chaque propriété étant contenue dans un élément PropertyRef.  
  
 Le tableau suivant répertorie les éléments et les attributs du type PropertyRefs.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|PropertyRef|Oui|Chaîne contenant la référence de la propriété.|  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre un élément PropertyRef qui spécifie la source d'une formule utilisée dans une mesure, de l'exemple de modèle tabulaire AdventureWorks.  
  
```  
<bi:Measure Caption="Total Current Quarter Margin Performance" ReferenceName="Total Current Quarter Margin Performance" Width="0" IsSimpleMeasure="false">  
  <bi:Kpi StatusGraphic="Three Symbols UnCircled Colored">  
    <bi:KpiGoal>  
      <bi:PropertyRef Name="Measures___Total_Current_Quarter_Margin_Performance_Goal_" />  
    </bi:KpiGoal>  
    <bi:KpiStatus>  
      <bi:PropertyRef Name="Measures___Total_Current_Quarter_Margin_Performance_Status_" />  
    </bi:KpiStatus>  
  </bi:Kpi>  
</bi:Measure>  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre un indicateur de performance clé du cube Contoso Operations. Les éléments PropertyRef pointent vers les colonnes qui contiennent la formule ou les valeurs utilisées pour définir l'objectif de l'indicateur de performance clé et l'état en rapport avec cet objectif.  
  
```  
<Property Name="Sum_of_SalesAmount" Type="Decimal" Precision="19" Scale="4">  
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
 [Informations techniques de référence sur les annotations pour le décisionnel dans CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
