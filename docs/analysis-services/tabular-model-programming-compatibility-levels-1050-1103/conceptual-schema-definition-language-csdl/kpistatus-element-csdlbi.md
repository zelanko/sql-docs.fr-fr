---
title: L’élément KpiStatus (CSDLBI) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 6fee5b82-caa8-46a1-ad68-bbce3e11e01e
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8895d3fce311650e60de08304abe211ba5306c96
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="kpistatus-element-csdlbi"></a>Élément KpiStatus (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  L'élément KpiStatus définit une référence à la colonne qui contient la valeur utilisée comme un indicateur d'état dans un indicateur de performance clé (KPI).  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément KpiStatus.  
  
|Nom|Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|PropertyRef|Oui|Référence à une colonne qui contient la valeur utilisée comme un indicateur d'état dans un indicateur de performance clé (KPI).<br /><br /> Cet élément DOIT contenir exactement une référence de colonne, tel que le définit le type TPropertyRefComplex.|  
  
## <a name="example"></a>Exemple  
 **Sous forme de tableau**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre un indicateur de performance clé de l'exemple de modèle tabulaire AdventureWorks. L'élément KpiStatus fait référence à une colonne (représentée en tant que PropertyRef) qui contient la valeur.  
  
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
 **Multidimensionnel**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre un indicateur de performance clé du cube Contoso Operations. L'élément KpiStatus référence une mesure qui calcule la valeur de l'état de l'indicateur de performance clé (KPI).  
  
```  
<bi:Measure   
       Caption="Sum of SalesAmount"   
       ReferenceName="Sum of SalesAmount"   
       FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
  
    <bi:Kpi   
       StatusGraphic="Three Circles Colored">  
  
      <bi:KpiGoal>  
         <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Goal" />  
       </bi:KpiGoal>  
  
       <bi:KpiStatus>  
          <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Status" />  
        </bi:KpiStatus>  
  
       </bi:Kpi>  
</bi:Measure>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément KPI & #40 ; CSDLBI & #41 ;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md)  
  
  
