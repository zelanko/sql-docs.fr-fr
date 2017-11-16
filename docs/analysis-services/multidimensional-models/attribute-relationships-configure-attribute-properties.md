---
title: "Configurer les propriétés de relation d’attribut | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b43a3d43e189279b45d5347b746a047f8f76eb88
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="attribute-relationships---configure-attribute-properties"></a>Relations d’attributs - configurer les propriétés d’attribut
  Le tableau suivant répertorie et décrit les propriétés d'une relation d'attribut.  
  
|Propriété|Description|  
|--------------|-----------------|  
|Attribut|Contient le nom de l'attribut.|  
|Cardinalité|Indique la cardinalité de la relation. Les valeurs sont Many, pour une relation plusieurs-à-un, ou One, pour une relation un-à-un. La valeur par défaut est Many. Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], la propriété de cardinalité n’a aucun effet ; son utilisation est réservée pour une implémentation future.|  
|Nom|Contient le nom convivial de l'attribut.|  
|RelationshipType|Indique si les relations de membres changent avec le temps. Les valeurs sont Rigid, qui signifie que les relations entre membres ne changent pas avec le temps, ou Flexible, qui signifie que les relations entre membres changent avec le temps. La valeur par défaut est Flexible. Si vous définissez une relation comme flexible, les agrégations sont supprimées et recalculées dans le cadre de la mise à jour incrémentielle (elles ne sont pas supprimées si seuls de nouveaux membres sont ajoutés). Si vous définissez une relation rigide, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] conserve les agrégations une fois la dimension mise à jour de manière incrémentielle. Si une relation rigide change, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] génère une erreur pendant le traitement incrémentiel. En spécifiant les relations et les propriétés de relations appropriées, vous améliorez les performances de requête et de traitement.|  
|Visible|Détermine la visibilité de la relation d'attribut. Les valeurs sont True ou False. La valeur par défaut est True.|  
  
  

