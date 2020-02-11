---
title: Partitions (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 708b9bdf-8c0b-4476-809a-8f616be23a58
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f5dd80a1f6645e7d1c766e88de653fa1e8f1f4cc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66066902"
---
# <a name="partitions-ssas-tabular"></a>Partitions (SSAS Tabulaire)
  Les partitions divisent une table en sections logiques. Chaque partition peut ensuite être traitée (actualisée) indépendamment d'autres partitions. Les partitions créées à l'aide de la boîte de dialogue Partitions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] au cours de la création de modèles s'appliquent à la base de données model de l'espace de travail. Lorsque le modèle est déployé, les partitions définies pour la base de données model de l'espace de travail sont dupliquées dans la base de données model déployée. Vous pouvez continuer à créer et gérer des partitions pour une base de données model déployée à l'aide de la boîte de dialogue Partitions dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  Les informations fournies dans cette rubrique décrivent les partitions créées pendant la génération de modèles à l'aide de la boîte de dialogue Gestionnaire de partitions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations sur la création et la gestion de partitions pour un modèle déployé, consultez [Créer et gérer des partitions de modèles tabulaires &#40;SSAS Tabulaire&#41;](create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
 Sections de cette rubrique :  
  
-   [Avantages](#bkmk_benefits)  
  
-   [Tâches associées](#bkmk_related_tasks)  
  
##  <a name="bkmk_benefits"></a>Avantageuse  
 Les partitions, dans les modèles tabulaires, divisent une table en objets partition logiques. Chaque partition peut ensuite être traitée indépendamment d'autres partitions. Par exemple, une table peut comprendre certains ensembles de lignes qui contiennent des données qui changent rarement, alors que d'autres ensembles de lignes comportent des données qui changent souvent. Dans ces cas, il est inutile de traiter toutes les données lorsque vous pouvez vous contenter de traiter uniquement une partie des données. Les partitions permettent de diviser des parties de données devant être traitées fréquemment afin de les séparer des données qui peuvent être traitées moins souvent.  
  
 La création de modèles efficaces fait appel à des partitions permettant d'éliminer tout traitement inutile et la charge qui en résulte au niveau du processeur sur les serveurs Analysis Services, tout en veillant en même temps à ce que les données soient traitées et actualisées suffisamment souvent pour refléter les données les plus récentes des sources de données. La manière d'implémenter et d'utiliser des partitions lors de la création de modèles peut être très différente de la façon dont les partitions sont implémentées et utilisées pour les modèles déployés. Gardez à l'esprit que, pendant la phase de création de modèles, vous pouvez utiliser uniquement un sous-ensemble des données qui figureront au final dans votre modèle déployé.  
  
### <a name="processing-partitions"></a>Traitement de partitions  
 Pour les modèles déployés, le traitement s'effectue à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ou en exécutant un script qui inclut la commande Traiter et spécifie les options et les paramètres de traitement. Lors de la création de modèles à l'aide de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], vous pouvez exécuter des opérations de traitement à l'aide d'une commande Traiter dans le menu Modèle ou de la barre d'outils. Une opération de traitement peut être spécifiée pour une partition, une table ou les deux.  
  
 Lorsqu'une opération de traitement est exécutée, une connexion à la source de données est établie à l'aide de la connexion de données. Les nouvelles données sont importées dans les tables de modèle, les relations et les hiérarchies sont créées ou reconstruites pour chaque table, et les calculs des colonnes calculées et des mesures sont actualisés.  
  
 En divisant une table en partitions logiques, vous pouvez déterminer de manière sélective les éléments, la date et le mode de traitement des données dans chaque partition. Lorsque vous déployez un modèle, le traitement des partitions peut être effectué manuellement à l'aide de la boîte de dialogue Partitions dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ou en utilisant un script qui exécute une commande Traiter.  
  
### <a name="partitions-in-the-model-workspace-database"></a>Partitions dans la base de données model de l'espace de travail  
 Vous pouvez créer de nouvelles partitions, modifier, fusionner ou supprimer des partitions à l'aide du Gestionnaire de partitions dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Le gestionnaire de partitions fournit deux modes pour sélectionner des tables, des lignes et des colonnes pour une partition : Mode Aperçu de la table et mode de requête SQL. Toutes les partitions sont définies à l'aide d'une requête SQL ; toutefois, à l'aide du mode Aperçu de la table, vous pouvez afficher un aperçu et sélectionner les données à inclure dans la partition. La requête SQL est créée et validée automatiquement. Étant donné que le mode Aperçu de la table correspond au même aperçu de la table que celui affiché dans la boîte de dialogue Modifier les propriétés de la table et de la page Aperçu de la table de l'Assistant Importation de table, le nombre maximal de lignes dans l'aperçu est de 50.  
  
### <a name="partitions-in-a-deployed-model-database"></a>Partitions dans une base de données model déployée  
 Lorsque vous déployez un modèle, les partitions pour la base de données model déployée apparaissent en tant qu'objets de base de données dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous pouvez créer, modifier, fusionner et supprimer des partitions pour un modèle déployé à l'aide de la boîte de dialogue Partitions dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. La gestion des partitions pour un modèle déployé dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] n'est pas traitée dans cette rubrique. Pour en savoir plus sur la gestion des partitions dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], consultez [Créer et gérer des partitions de modèles tabulaires &#40;SSAS Tabulaire&#41;](create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_related_tasks"></a> Tâches associées  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Créer et gérer des partitions dans la base de données de l’espace de travail &#40;&#41;SSAS tabulaire](workspace-database-ssas-tabular.md)|Décrit comment créer et gérer des partitions dans la base de données model de l'espace de travail à l'aide du gestionnaire de partitions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|  
|[Traiter les partitions dans la base de données de l’espace de travail &#40;SSAS tabulaire&#41;](process-partitions-in-the-workspace-database-ssas-tabular.md)|Explique comment traiter (actualiser) des partitions dans la base de données model de l'espace de travail.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mode DirectQuery &#40;&#41;tabulaire SSAS](directquery-mode-ssas-tabular.md)   
 [Traiter des données &#40;tabulaires SSAS&#41;](../process-data-ssas-tabular.md)  
  
  
