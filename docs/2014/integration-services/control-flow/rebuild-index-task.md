---
title: Reconstruire l’index, tâche| Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.rebuildindextask.f1
helpviewer_keywords:
- rebuilding indexes
- indexes [Integration Services]
- Rebuild Index task
ms.assetid: 021884dd-e72d-47b2-99e8-b741410509c3
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f5a97597fe88aabfef3d0c62ad4c21cfd7be9c76
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051774"
---
# <a name="rebuild-index-task"></a>tâche Reconstruire l'index
  La tâche Reconstruire l'index reconstruit les index dans les vues et les tables de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations sur la gestion des index, consultez [Réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 La tâche Reconstruire l'index permet à un package de reconstruire les index dans une ou plusieurs bases de données. Si la tâche reconstruit uniquement les index d'une base de données, vous pouvez choisir les vues et les tables dont la tâche reconstruit les index.  
  
 Cette tâche encapsule une instruction ALTER INDEX REBUILD avec les options de reconstruction d'index suivantes :  
  
-   Spécifiez un pourcentage FILLFACTOR ou utilisez la quantité d'origine de FILLFACTOR.  
  
-   Attribuez au paramètre PAD_INDEX la valeur ON afin d'allouer l'espace disponible spécifié par FILLFACTOR aux pages de niveau intermédiaire de l'index.  
  
-   Attribuez au paramètre SORT_IN_TEMPDB la valeur ON afin de stocker dans tempdb le résultat intermédiaire du tri utilisé pour reconstruire l'index. Lorsque le résultat intermédiaire du tri a pour valeur OFF, il est stocké dans la même base de données que l'index.  
  
-   Attribuez au paramètre IGNORE_DUP_KEY la valeur ON pour permettre une opération d'insertion de plusieurs lignes incluant les enregistrements qui violent des contraintes uniques afin d'insérer les enregistrements qui ne violent pas les contraintes uniques.  
  
-   Attribuez au paramètre ONLINE la valeur ON pour ne pas appliquer de verrous de table, afin que les requêtes ou les mises à jour portant sur la table sous-jacente puissent être exécutées pendant la réindexation.  
  
> [!NOTE]  
>  Les opérations d'index en ligne ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Pour plus d’informations sur l’instruction ALTER INDEX et sur les options de reconstruction d’index, consultez [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
  
> [!IMPORTANT]  
>  Le temps que prend la tâche pour créer l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qu'elle exécute est proportionnel au nombre d'index qu'elle reconstruit. Si la tâche est configurée de manière à reconstruire les index dans toutes les tables et vues d'une base de données possédant de nombreux index ou à reconstruire les index de plusieurs bases de données, elle peut prendre un temps considérable pour générer l'instruction Transact-SQL.  
  
## <a name="configuration-of-the-rebuild-index-task"></a>Configuration de la tâche Reconstruire l'index  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
 [Tâche Reconstruire l’index &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour plus d’informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , consultez [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)  
  
  
