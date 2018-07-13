---
title: Élément KPI (CSDLBI) | Microsoft Docs
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
ms.assetid: 203ee6e8-eef2-4476-b09f-bd95e492ddaa
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0a649ffffe6f2d9f5902ede9e6d7a6126fd09e25
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155080"
---
# <a name="kpi-element-csdlbi"></a>Élément KPI (CSDLBI)
  L'élément Kpi définit un calcul qui peut être utilisé comme indicateur de performance clé (KPI). Dans un modèle de données Business Intelligence, les indicateurs de performance clés sont basés sur les mesures et, comme telles, la définition de l'indicateur de performance clé contient toutes les métadonnées associées à des mesures, ainsi que les informations nécessaires pour la présentation des valeurs d'indicateur de performance clé, notamment un graphique par défaut.  
  
 L'élément Kpi ne spécifie pas la formule, contenue dans la définition de la mesure, mais spécifie plutôt les métadonnées supplémentaires associées aux mesures utilisées comme indicateur de performance clé. Une fois que vous avez désigné une mesure en tant qu'indicateur de performance clé, vous ne pouvez pas l'utiliser comme mesure dans d'autres contextes.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément Kpi.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Documentation|non|Description du KPI.|  
|KpiGoal|Oui|Référence à une colonne qui contient des valeurs qui peuvent être utilisées comme cible.<br /><br /> Consultez [Élément PropertyRef &#40;CSDLBI&#41;](propertyref-element-csdlbi.md).|  
|KpiStatus|Oui|Référence à une colonne qui contient des valeurs qui représentent l'état actuel de l'indicateur de performance clé.|  
|StatusGraphic|Oui|Référence à une image qui indique une progression négative, neutre ou positive sur les cibles définies dans l'indicateur de performance clé.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous concevez un modèle, vous pouvez créer un indicateur de performance clé en créant une mesure, puis en attribuant la mesure à utiliser comme indicateur de performance clé. Vous ajoutez ensuite des informations spécifiques aux indicateurs de performance clés, tels qu'un graphique à utiliser dans l'affichage des tendances.  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple suivant, dans CSDLBI version 1.0, illustre un indicateur de performance clé qui mesure les ventes, de l'exemple de modèle tabulaire AdventureWorks.  
  
```  
  
<Property Name="InternetCurrSalesPerf" Type="Double">  
  <bi:Measure>  
    <bi:Kpi StatusGraphic="Three Stars Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Goal" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Status" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre un indicateur de performance clé du cube Contoso Operations.  
  
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
 [Informations techniques de référence sur les annotations pour le décisionnel dans CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
