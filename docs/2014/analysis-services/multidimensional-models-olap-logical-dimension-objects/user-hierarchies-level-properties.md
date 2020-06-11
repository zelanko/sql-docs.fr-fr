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
ms.openlocfilehash: 553503b9d35142bcc998b4ec12ad2e29d4c66318
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545071"
---
# <a name="level-properties"></a>Propriétés de niveau 
  Le tableau suivant répertorie et décrit les propriétés d'un niveau dans une hiérarchie définie par l'utilisateur.  
  
|Propriété|Description|  
|--------------|-----------------|  
|Description|Contient la description du niveau.|  
|HideMemberIf|Indique si et quand un membre d'un niveau doit être masqué par rapport aux applications clientes. Cette propriété peut avoir les valeurs suivantes :<br /><br /> Jamais<br /> Les membres ne sont jamais masqués. Il s’agit de la valeur par défaut.<br /><br /> OnlyChildWithNoName<br /> Le membre est masqué s'il est le seul enfant de son parent et que son nom est vide.<br /><br /> OnlyChildWithParentName<br /> Le membre est masqué s'il est le seul enfant de son parent et qu'il a le même nom que lui.<br /><br /> NoName<br /> Le membre est masqué si son nom est vide.<br /><br /> ParentName<br /> Le membre est masqué s'il a le même nom que son parent.|  
|id|Contient l'identificateur (ID) unique du niveau.|  
|Nom|Contient le nom convivial du niveau. Par défaut, le niveau a le même nom que l'attribut source.|  
|SourceAttribute|Contient le nom de l'attribut source sur lequel est basé le niveau.|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la hiérarchie définie par l'utilisateur](user-hierarchies-properties.md)  
  
  
