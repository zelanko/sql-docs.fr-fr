---
title: Gestion de Caches (XMLA) | Documents Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6a34388f9c9d23d50fbd0de8842b8fc34f6bb8e4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="managing-caches-xmla"></a>Gestion des caches (XMLA)
  Vous pouvez utiliser la [ClearCache](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md) commande XML for Analysis (XMLA) pour effacer le cache de dimension spécifiée ou la partition. Effacement du cache contraint [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour régénérer le cache pour cet objet.  
  
## <a name="specifying-objects"></a>Spécification d'objets  
 Le [objet](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) propriété de la **ClearCache** commande peut contenir une référence d’objet que pour un des objets suivants. Si une référence d'objet désigne un objet différent de ceux mentionnés ci-dessous, une erreur se produit :  
  
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
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
