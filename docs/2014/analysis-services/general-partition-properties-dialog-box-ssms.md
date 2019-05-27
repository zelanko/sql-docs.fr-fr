---
title: Général (boîte de dialogue Propriétés de Partition) (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.partitionproperties.general.f1
ms.assetid: efb505be-354f-4d23-8f2d-3e76fa50d27b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05d840d4e43d9856dedeb3fd446c8158f23275b4
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66081073"
---
# <a name="general-partition-properties-dialog-box-ssms"></a>Général (boîte de dialogue Propriétés de partition) (SSMS)
  Utilisez la page **Général** de la boîte de dialogue **Propriétés de partition** de SQL Server Management Studio pour définir les propriétés générales d'une partition d'un groupe de mesures d'un cube d'une base de données [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**ID de conception d’agrégation**|Affiche l'identificateur du modèle d'agrégation utilisé par la partition.|  
|**Préfixe d’agrégation**|Affiche le préfixe par défaut des instances d'agrégation contenues dans la partition.|  
|**Créer un horodateur**|Affiche la date et l'heure de création de la partition.|  
|**Mode de stockage actuel**|Affiche le mode de stockage actif de la partition.<br /><br /> Remarque : Ce mode peut varier selon les paramètres de mise en cache proactive pour la partition. Pour plus d’informations sur la mise en cache proactive, consultez [Mise en cache proactive &#40;partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Description**|Modifie la description de la référence de la partition.|  
|**Lignes estimées**|Tapez le nombre de lignes estimé dans la source de données sous-jacente représentée par la partition. Cette valeur est utilisée pendant le traitement pour estimer le temps et la capacité de stockage nécessaires au traitement de la partition.|  
|**Taille estimée**|Affiche la taille estimée de la partition.|  
|**ID**|Affiche l'identificateur de la partition.|  
|**Dernier traitement**|Affiche la date et l'heure du dernier traitement de la partition.|  
|**Dernière mise à jour du schéma**|Affiche la date et l'heure de la dernière mise à jour des métadonnées de la partition.|  
|**Nom**|Affiche le nom de la partition.|  
|**Mode de traitement**|Sélectionnez le mode de traitement à utiliser pour la partition. Pour plus d’informations sur les modes de traitement des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , consultez [traitement d’un objet de modèle multidimensionnel](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).|  
|**ID de Source de données distante**|Affiche l'identificateur de la source de données distante d'où est extraite la partition.<br /><br /> Remarque : Cette propriété contient une valeur uniquement pour les partitions distantes.|  
|**Slice**|Affiche l'expression qui identifie la tranche de données représentée par la partition.|  
|**Source**|Affiche la table ou la requête qui fournit la source de données pour la partition.|  
|**État**|Affiche l'état actuel du traitement de la partition.|  
|**Emplacement de stockage**|Affiche le dossier dans lequel les données de la partition sont stockées.<br /><br /> Remarque : Cette propriété contient une valeur uniquement si un emplacement de stockage autre que l’emplacement de stockage par défaut pour le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance est spécifiée.|  
|**Type**|Affiche le type de la partition.|  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions &#40;Analysis Services - Données multidimensionnelles&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Partitions distantes](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)   
 [Boîte de dialogue Propriétés de partition &#40;SSMS&#41;](partition-properties-dialog-box-ssms.md)   
 [Sélection &#40;boîte de dialogue Propriétés de Partition&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)   
 [Mise en cache proactive &#40;boîte de dialogue Propriétés de Partition&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md)   
 [Configuration d’erreur pour le Cube, Partition et le traitement de Dimension &#40;SSAS - multidimensionnel&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
  
