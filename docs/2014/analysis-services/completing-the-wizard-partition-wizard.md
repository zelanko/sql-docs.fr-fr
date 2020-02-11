---
title: Fin de l’Assistant (Assistant Partition) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.finish.f1
ms.assetid: 68a4dd5d-94d9-4a02-be31-949a6da0ef51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f7ab4ad7a819c18056ab5901f95caf1b74b23a25
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087527"
---
# <a name="completing-the-wizard-partition-wizard"></a>Fin de l'Assistant (Assistant Partition)
  Utilisez la page **Fin de l'Assistant** pour nommer la partition, définir la conception d'agrégation de la partition et éventuellement déployer et traiter la partition après avoir exécuté l'Assistant Partition.  
  
## <a name="options"></a>Options  
 **Nom**  
 Entrez le nom de la nouvelle partition. Si vous utilisez plusieurs tables, entrez le préfixe à combiner avec le nom de la table pour créer chaque nom de partition.  
  
 **Options d'agrégation**  
 Définit l'option d'agrégation de la partition.  
  
 Le tableau ci-après répertorie les options d'agrégation disponibles.  
  
|Option|Description|  
|------------|-----------------|  
|**Créer maintenant les agrégations pour la partition**|Conçoit les agrégations de la nouvelle partition après que l'Assistant Partition a créé la partition. Cette option démarre l'Assistant Conception d'agrégation lorsque vous cliquez sur **Terminer** dans l'Assistant Partition. Pour plus d’informations sur l’Assistant Conception d’agrégation, consultez [Aide (F1) de l’Assistant Conception d’agrégation](aggregation-design-wizard-f1-help.md).|  
|**Créer les agrégations ultérieurement**|Crée la partition sans concevoir d'agrégation à ce stade.|  
|**Copier la structure de l'agrégation à partir d'une partition existante**|Copie la conception d'agrégation depuis une partition existante dans le groupe de mesures vers la nouvelle partition. Cliquez sur cette option pour rendre l'option **Copier à partir de** disponible. Utilisez la zone **Copier à partir de** pour sélectionner la partition de la conception d'agrégation à copier.<br /><br /> Notez que les partitions qui peuvent être fusionnées ultérieurement doivent avoir la même structure de table et la même conception d’agrégation. Si vous fusionnez la nouvelle partition avec une partition existante dans le groupe de mesures, vous devez copier la conception d'agrégation existante dans la nouvelle partition.|  
  
 **Déployer et traiter maintenant**  
 Déploie et traite la partition dans l'instance [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] définie dans la page **Emplacements pour le traitement et le stockage**. L'Assistant déploie et traite la partition après que vous ayez cliqué sur **Terminer** dans cette page.  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions &#40;Analysis Services-données multidimensionnelles&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
