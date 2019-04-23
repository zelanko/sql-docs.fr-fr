---
title: Propriétés de niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c55a596461e03ce91a822e4578f7de56fe27f8f1
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60156526"
---
# <a name="level-properties"></a>Propriétés de niveau 
  Le tableau suivant répertorie et décrit les propriétés d'un niveau dans une hiérarchie définie par l'utilisateur.  
  
|Propriété|Description|  
|--------------|-----------------|  
|Description|Contient la description du niveau.|  
|HideMemberIf|Indique si et quand un membre d'un niveau doit être masqué par rapport aux applications clientes. Cette propriété peut avoir les valeurs suivantes :<br /><br /> Never<br /> Les membres ne sont jamais masqués. Valeur par défaut.<br /><br /> OnlyChildWithNoName<br /> Le membre est masqué s'il est le seul enfant de son parent et que son nom est vide.<br /><br /> OnlyChildWithParentName<br /> Le membre est masqué s'il est le seul enfant de son parent et qu'il a le même nom que lui.<br /><br /> NoName<br /> Le membre est masqué si son nom est vide.<br /><br /> ParentName<br /> Le membre est masqué s'il a le même nom que son parent.|  
|ID|Contient l'identificateur (ID) unique du niveau.|  
|Nom|Contient le nom convivial du niveau. Par défaut, le niveau a le même nom que l'attribut source.|  
|SourceAttribute|Contient le nom de l'attribut source sur lequel est basé le niveau.|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la hiérarchie utilisateur](user-hierarchies-properties.md)  
  
  
