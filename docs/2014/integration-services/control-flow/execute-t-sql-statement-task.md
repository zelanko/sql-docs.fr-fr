---
title: Exécuter l’instruction T-SQL, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 74be247e47e50b61dfea84863a5969008f160ff0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044273"
---
# <a name="execute-t-sql-statement-task"></a>Tâche Exécuter l'instruction T-SQL
  La tâche Exécuter l'instruction T-SQL exécute des instructions Transact-SQL. Pour plus d’informations, consultez [Référence Transact-SQL &#40;moteur de base de données&#41;](/sql/t-sql/language-reference) et [Requêtes Integration Services &#40;SSIS&#41;](../integration-services-ssis-queries.md).  
  
 Cette tâche est similaire à la tâche d'exécution SQL. Toutefois, la tâche Exécuter l'instruction T-SQL ne prend en charge que la version Transact-SQL du langage SQL et vous ne pouvez pas recourir à cette tâche pour exécuter des instructions sur les serveurs qui utilisent d'autres dialectes du langage SQL. Pour exécuter des requêtes paramétrables, enregistrer les résultats des requêtes dans des variables ou utiliser des expressions de propriété, vous devez utiliser la tâche d'exécution SQL et non pas la tâche Exécuter l'instruction T-SQL. Pour plus d'informations, consultez [Execute SQL Task](execute-sql-task.md).  
  
## <a name="configuration-of-the-execute-t-sql-task"></a>Configuration de la tâche Exécuter l'instruction T-SQL  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Exécuter la tâche de l’instruction T-SQL &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)   
 [MERGE dans les packages Integration Services](merge-in-integration-services-packages.md)  
  
  
