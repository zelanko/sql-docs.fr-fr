---
title: Niveau de propriétés - hiérarchies utilisateur | Documents Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9d6cc848a772f290a6222bce2906228efdae6de
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="user-hierarchies---level-properties"></a>Hiérarchies des utilisateurs - propriétés de niveau
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Le tableau suivant répertorie et décrit les propriétés d'un niveau dans une hiérarchie définie par l'utilisateur.  
  
|Propriété| Description|  
|--------------|-----------------|  
| Description|Contient la description du niveau.|  
|HideMemberIf|Indique si et quand un membre d'un niveau doit être masqué par rapport aux applications clientes. Cette propriété peut avoir les valeurs suivantes :<br /><br /> Never<br /> Les membres ne sont jamais masqués. Ceci est la valeur par défaut.<br /><br /> OnlyChildWithNoName<br /> Le membre est masqué s'il est le seul enfant de son parent et que son nom est vide.<br /><br /> OnlyChildWithParentName<br /> Le membre est masqué s'il est le seul enfant de son parent et qu'il a le même nom que lui.<br /><br /> NoName<br /> Le membre est masqué si son nom est vide.<br /><br /> ParentName<br /> Le membre est masqué s'il a le même nom que son parent.|  
|ID|Contient l'identificateur (ID) unique du niveau.|  
|Nom|Contient le nom convivial du niveau. Par défaut, le niveau a le même nom que l'attribut source.|  
|SourceAttribute|Contient le nom de l'attribut source sur lequel est basé le niveau.|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la hiérarchie utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
