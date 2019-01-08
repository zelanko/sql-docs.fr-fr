---
title: Réorganiser l’index, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.reorganizeindextask.f1
helpviewer_keywords:
- reorganizing indexes
- Reorganize Index task [Integration Services]
- indexes [Integration Services]
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 25b16c91d94022c6b328e64290e3271f7d0aa2d3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52790921"
---
# <a name="reorganize-index-task"></a>Tâche Réorganiser l'index
  La tâche Réorganiser l'index réorganise les index dans les vues et les tables de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations sur la gestion des index, consultez [Réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 La tâche Réorganiser l'index permet à un package de réorganiser les index dans une ou plusieurs bases de données. Si la tâche réorganise uniquement les index d'une base de données, vous pouvez choisir les vues ou les tables dont les index sont à réorganiser. En outre, la tâche Réorganiser l'index comprend une option qui permet de compacter les données d'objets volumineux. Les données d'objets volumineux peuvent avoir les types de données suivants : `image`, `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)` ou `xml`. Pour plus d’informations, consultez [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
 La tâche Réorganiser l'index encapsule l'instruction Transact-SQL ALTER INDEX. Si vous choisissez de compacter les données d'objet volumineux, l'instruction utilise la clause REORGANIZE WITH (LOB_COMPACTION = ON), sinon l'option LOB_COMPACTION a pour valeur OFF. Pour plus d’informations, consultez [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
  
> [!IMPORTANT]  
>  Le temps que prend la tâche à créer l'instruction Transact-SQL qu'elle exécute est proportionnel au nombre d'index qu'elle réorganise. Si la tâche est configurée de manière à réorganiser les index dans toutes les tables et vues d'une base de données avec de nombreux index ou à réorganiser les index de plusieurs bases de données, elle peut prendre beaucoup de temps pour générer l'instruction Transact-SQL.  
  
## <a name="configuration-of-the-reorganize-index-task"></a>Configuration de la tâche Réorganiser l'index  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Tâche Réorganiser l’index &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la façon de définir ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , consultez [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)  
  
  
