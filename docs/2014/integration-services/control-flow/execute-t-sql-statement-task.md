---
title: Exécuter l’instruction T-SQL, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f20f64c9a26d1e9b030c01618a63157757c0b205
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831734"
---
# <a name="execute-t-sql-statement-task"></a>Tâche Exécuter l'instruction T-SQL
  La tâche Exécuter l'instruction T-SQL exécute des instructions Transact-SQL. Pour plus d’informations, consultez [Référence Transact-SQL &#40;moteur de base de données&#41;](/sql/t-sql/language-reference) et [Requêtes Integration Services &#40;SSIS&#41;](../integration-services-ssis-queries.md).  
  
 Cette tâche est similaire à la tâche d'exécution SQL. Toutefois, la tâche Exécuter l'instruction T-SQL ne prend en charge que la version Transact-SQL du langage SQL et vous ne pouvez pas recourir à cette tâche pour exécuter des instructions sur les serveurs qui utilisent d'autres dialectes du langage SQL. Pour exécuter des requêtes paramétrables, enregistrer les résultats des requêtes dans des variables ou utiliser des expressions de propriété, vous devez utiliser la tâche d'exécution SQL et non pas la tâche Exécuter l'instruction T-SQL. Pour plus d'informations, consultez [Execute SQL Task](execute-sql-task.md).  
  
## <a name="configuration-of-the-execute-t-sql-task"></a>Configuration de la tâche Exécuter l'instruction T-SQL  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Exécuter la tâche de l’instruction T-SQL &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)   
 [MERGE in Integration Services Packages](merge-in-integration-services-packages.md)  
  
  
