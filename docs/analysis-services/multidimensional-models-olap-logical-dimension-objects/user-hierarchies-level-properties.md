---
title: "Niveau de propriétés - hiérarchies utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: db94622cfc84d97cb6f8e7578421f4933a63af94
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="user-hierarchies---level-properties"></a>Hiérarchies des utilisateurs - propriétés de niveau
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Le tableau suivant répertorie et décrit les propriétés d’un niveau dans une hiérarchie définie par l’utilisateur.  
  
|Propriété|Description|  
|--------------|-----------------|  
|Description|Contient la description du niveau.|  
|HideMemberIf|Indique si et quand un membre d'un niveau doit être masqué par rapport aux applications clientes. Cette propriété peut avoir les valeurs suivantes :<br /><br /> Never<br /> Les membres ne sont jamais masqués. Il s'agit de la valeur par défaut.<br /><br /> OnlyChildWithNoName<br /> Le membre est masqué s'il est le seul enfant de son parent et que son nom est vide.<br /><br /> OnlyChildWithParentName<br /> Le membre est masqué s'il est le seul enfant de son parent et qu'il a le même nom que lui.<br /><br /> NoName<br /> Le membre est masqué si son nom est vide.<br /><br /> ParentName<br /> Le membre est masqué s'il a le même nom que son parent.|  
|ID|Contient l'identificateur (ID) unique du niveau.|  
|Nom   |Contient le nom convivial du niveau. Par défaut, le niveau a le même nom que l'attribut source.|  
|SourceAttribute|Contient le nom de l'attribut source sur lequel est basé le niveau.|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la hiérarchie utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
