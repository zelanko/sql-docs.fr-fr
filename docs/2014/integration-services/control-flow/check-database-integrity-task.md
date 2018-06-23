---
title: Vérifier l’intégrité de la base de données, tâche | Microsoft Docs
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
- sql12.dts.designer.checkdatabaseintegritytask.f1
helpviewer_keywords:
- data integrity [Integration Services]
- Check Database Integrity task [Integration Services]
- checking database consistency
- database consistency checks [Integration Services]
- verifying database consistency
- integrity checking [Integration Services]
ms.assetid: 5a82fe99-4503-429f-9337-e6bac7649fe4
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 71862e23c831a6b211d461227435bdf6e0b97d99
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053122"
---
# <a name="check-database-integrity-task"></a>Tâche Vérifier l'intégrité de la base de données
  La tâche Vérifier l'intégrité de la base de données contrôle l'allocation et l'intégrité de la structure de tous les objets de la base de données spécifiée. La tâche peut vérifier une ou plusieurs bases de données et vous pouvez indiquer si vous souhaitez également contrôler les index de base de données.  
  
 La tâche Vérifier l'intégrité de la base de données encapsule l'instruction DBCC CHECKDB. Pour plus d’informations, consultez [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql).  
  
## <a name="configuration-of-the-check-database-integrity-task"></a>Configuration de la tâche Vérifier l'intégrité de la base de données  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Tâche Vérifier l’intégrité de la base de données &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/check-database-integrity-task-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
  
