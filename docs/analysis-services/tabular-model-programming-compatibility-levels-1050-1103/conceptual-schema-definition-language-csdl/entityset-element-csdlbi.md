---
title: Élément EntitySet (CSDLBI) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: d4703c9e-5594-472e-a85b-0f5bd0d73d6f
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4e931f1756fc10028f0398c2e33e1f1b7a71aa1f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="entityset-element-csdlbi"></a>Élément EntitySet (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  L'élément EntitySet définit une collection d'entités d'un type spécifique dans un modèle de données CSDLBI.  
  
 L'EntitySet doit spécifier chaque type d'entité inclus dans le modèle de données. Des informations sur ces entités de modèle sont spécifiées en répertoriant les entités enfants du type, élément Entity. Pour plus d’informations, consultez [Élément EntityType &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitytype-element-csdlbi.md).  
  
 Des propriétés telles que le classement et le langage sont définies au niveau de l'EntityContainer, et non sur des objets individuels. Toutefois, les colonnes et les attributs du texte du modèle peuvent avoir des légendes ou des traductions dans d'autres langues.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent un EntitySet.  
  
|Nom d'attribut|Est obligatoire|Description|  
|--------------------|-----------------|-----------------|  
|Légende|Non|Description conviviale du jeu d'entités.|  
|CollectionCaption|Non|Chaîne qui contient le nom au pluriel de l'entité.|  
|ReferenceName|Non|Contient le nom non fusionné et complet de l'entité. Dans un modèle multidimensionnel, correspond au nom CubeDimension.|  
|Caché|Non|Indique si l'entité est masquée. Par défaut, les entités ne sont pas masquées.|  
  
## <a name="example"></a>Exemple  
 **Sous forme de tableau**  
  
 L'exemple suivant, en CSDLBI version 1.1, affiche les définitions des tables Date et Geography, du modèle tabulaire AdventureWorks.  
  
```  
  
<EntitySet   
   Name="Date"   
   EntityType="Sandbox. Date">  
<bi:EntitySet />  
</EntitySet>  
  
<EntitySet   
   Name="Geography"   
   EntityType="Sandbox.Geography">  
<bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="example"></a>Exemple  
 **Multidimensionnel**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre plusieurs éléments EntitySet du cube Contoso Retail Operations.  
  
```  
  
<EntitySet Name="Outage" EntityType="Sandbox.Outage">  
       <bi:EntitySet />  
</EntitySet>  
  
<EntitySet Name="Store" EntityType="Sandbox.Store">  
     <bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations techniques de référence pour les Annotations BI au langage CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
