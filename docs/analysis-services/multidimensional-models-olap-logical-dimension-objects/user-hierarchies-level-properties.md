---
title: "Niveau de propriétés - hiérarchies utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
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
ms.openlocfilehash: dea548f76a6197f557a520bfa0153133643bed3a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="user-hierarchies---level-properties"></a>Hiérarchies des utilisateurs - propriétés de niveau
  Le tableau suivant répertorie et décrit les propriétés d'un niveau dans une hiérarchie définie par l'utilisateur.  
  
|Propriété|Description|  
|--------------|-----------------|  
|Description|Contient la description du niveau.|  
|HideMemberIf|Indique si et quand un membre d'un niveau doit être masqué par rapport aux applications clientes. Cette propriété peut avoir les valeurs suivantes :<br /><br /> Never<br /> Les membres ne sont jamais masqués. Ceci est la valeur par défaut.<br /><br /> OnlyChildWithNoName<br /> Le membre est masqué s'il est le seul enfant de son parent et que son nom est vide.<br /><br /> OnlyChildWithParentName<br /> Le membre est masqué s'il est le seul enfant de son parent et qu'il a le même nom que lui.<br /><br /> NoName<br /> Le membre est masqué si son nom est vide.<br /><br /> ParentName<br /> Le membre est masqué s'il a le même nom que son parent.|  
|ID|Contient l'identificateur (ID) unique du niveau.|  
|Nom|Contient le nom convivial du niveau. Par défaut, le niveau a le même nom que l'attribut source.|  
|SourceAttribute|Contient le nom de l'attribut source sur lequel est basé le niveau.|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la hiérarchie utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
