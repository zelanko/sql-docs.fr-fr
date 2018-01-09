---
title: Partitions distantes | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- storage [Analysis Services], partitions
- archiving remote partitions [Analysis Services]
- partitions [Analysis Services], remote
- restoring remote partitions [Analysis Services]
- backing up remote partitions [Analysis Services]
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- MasterDataSourceID property
- remote partitions [Analysis Services]
ms.assetid: 63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4366b335e5092818e33de8a0ea1b7ab8d7af607c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="partitions---remote-partitions"></a>Partitions - Partitions distantes
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Les données d’une partition distante sont stockées sur une autre instance de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l’instance qui contient les définitions (métadonnées) de la partition et son cube parent. Une partition distante est administrée sur la même instance d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans laquelle la partition et son cube parent sont définis.  
  
> [!NOTE]  
>  Pour stocker une partition distante, l’ordinateur doit disposer d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installé et s’exécute le même niveau de service pack que l’instance où la partition a été définie. Les partitions distantes sur des instances d'une version antérieure d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne sont pas prises en charge.  
  
 Lorsque les partitions distantes sont incluses dans un groupe de mesures, l'utilisation de la mémoire et de l'unité centrale du cube est répartie sur l'ensemble des partitions du groupe de mesures. Par exemple, lorsqu'une partition distante est traitée, seule ou dans le cadre du traitement de son cube parent, la mémoire et l'unité centrale sont essentiellement utilisées pour cette partition sur l'instance distante d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Un cube qui contient des partitions distantes peut contenir des dimensions activées en écriture ; cependant, ses performances peuvent en être affectées. Pour plus d’informations sur les dimensions activées en écriture, consultez [Write Dimensions](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).  
  
## <a name="storage-modes-for-remote-partitions"></a>Modes de stockage des partitions distantes  
 Les partitions distantes peuvent recourir à tous les types de stockage utilisés par les partitions locales : MOLAP (OLAP multidimensionnel), HOLAP (OLAP hybride) ou ROLAP (OLAP relationnel). Les partitions distantes peuvent également utiliser la mise en cache proactive. Les données stockées sur l'instance distante d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dépendent du mode de stockage appliqué à la partition distante.  
  
|||  
|-|-|  
|Type de stockage|data|  
|MOLAP|Agrégations de la partition et une copie des données sources de la partition|  
|HOLAP|Agrégations des partitions|  
|ROLAP|Pas de données de partition|  
  
 Si un groupe de mesures contient plusieurs partitions MOLAP ou HOLAP stockées sur plusieurs instances d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le cube distribue les données du groupe de mesures entre ces instances d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="merging-remote-partitions"></a>Fusion des partitions distantes  
 Les partitions distantes peuvent être fusionnées uniquement avec d'autres partitions distantes qui sont stockées sur la même instance distante d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pour plus d’informations sur la fusion de partitions, consultez [fusionner des Partitions dans Analysis Services &#40; SSAS - multidimensionnel &#41; ](../../analysis-services/multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md).  
  
## <a name="archiving-and-restoring-remote-partitions"></a>Archivage et restauration des partitions distantes  
 Les données des partitions distantes peuvent être archivées ou restaurées lorsque la base de données qui stocke la partition distante est archivée ou restaurée. Si vous restaurez une base de données sans restaurer une partition distante, vous devez traiter la partition distante avant d'utiliser les données de la partition. Pour plus d’informations sur l’archivage et la restauration des bases de données, consultez [sauvegarde et restauration des Services de bases de données Analysis](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et gérer une Partition distante &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md)   
 [Pour des objets de traitement Analysis Services](../../analysis-services/multidimensional-models/processing-analysis-services-objects.md)  
  
  
