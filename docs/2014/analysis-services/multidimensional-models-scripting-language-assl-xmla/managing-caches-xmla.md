---
title: Gestion des Caches (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 72e36e7d8f0efc9880d0dd164a253030712ee120
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62727585"
---
# <a name="managing-caches-xmla"></a>Gestion des caches (XMLA)
  Vous pouvez utiliser la [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) commande XML for Analysis (XMLA) pour effacer le cache de dimension spécifiée ou la partition. Effacement du cache contraint [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour régénérer le cache pour cet objet.  
  
## <a name="specifying-objects"></a>Spécification d'objets  
 Le [objet](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) propriété de la `ClearCache` commande peut contenir une référence d’objet pour un seul des objets suivants. Si une référence d'objet désigne un objet différent de ceux mentionnés ci-dessous, une erreur se produit :  
  
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
  
  
