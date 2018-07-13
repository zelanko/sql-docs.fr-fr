---
title: Gestion des Caches (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: da13c86e86a2f51719a9d4f0aedfda33935766ae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180808"
---
# <a name="managing-caches-xmla"></a>Gestion des caches (XMLA)
  Vous pouvez utiliser la [ClearCache](../xmla/xml-elements-commands/clearcache-element-xmla.md) commande XML for Analysis (XMLA) pour effacer le cache de dimension spécifiée ou la partition. Effacement du cache contraint [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour régénérer le cache pour cet objet.  
  
## <a name="specifying-objects"></a>Spécification d'objets  
 Le [objet](../xmla/xml-elements-properties/object-element-xmla.md) propriété de la `ClearCache` commande peut contenir une référence d’objet pour un seul des objets suivants. Si une référence d'objet désigne un objet différent de ceux mentionnés ci-dessous, une erreur se produit :  
  
 Base de données  
 Efface le cache pour l'ensemble des dimensions et des partitions contenues dans la base de données.  
  
 Dimension  
 Efface le cache pour la dimension spécifiée.  
  
 Cube  
 Efface le cache pour l'ensemble des partitions contenues dans les groupes de mesures du cube.  
  
 Groupe de mesures  
 Efface le cache pour l'ensemble des partitions contenues dans le groupe de mesures.  
  
 Partition  
 Efface le cache pour la partition spécifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
