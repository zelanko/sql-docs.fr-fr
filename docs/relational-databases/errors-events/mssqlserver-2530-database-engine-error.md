---
title: MSSQLSERVER_2530 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1d86bffff7d5adf252ce288e63af01c8097e1b9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver2530"></a>MSSQLSERVER_2530
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2530|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_INDEX_IS_OFFLINE|  
|Texte du message|L’index "%.*ls" sur la table "%.\*ls" est désactivé.|  
  
## <a name="explanation"></a>Explication  
L'instruction DBCC ne peut pas continuer, car l'index spécifié est désactivé. Lorsqu'un index est désactivé, il reste dans cet état tant qu'il n'est pas reconstruit, ou supprimé et recréé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
1.  Activez l'index désactivé à l'aide de l'une des méthodes suivantes :  
  
    -   Instruction ALTER INDEX avec la clause REBUILD  
  
    -   Instruction CREATE INDEX avec la clause DROP_EXISTING  
  
    -   DBCC DBREINDEX  
  
2.  Réexécutez l'instruction DBCC.  
  
## <a name="see-also"></a> Voir aussi  
[Activer les index et contraintes](~/relational-databases/indexes/enable-indexes-and-constraints.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[DBCC DBREINDEX &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)  
  
