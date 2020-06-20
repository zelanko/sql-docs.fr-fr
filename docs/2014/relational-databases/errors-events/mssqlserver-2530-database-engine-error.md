---
title: MSSQLSERVER_2530 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 30b57aae907d6f0acc4d1c0e6021bf936621c69e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85034246"
---
# <a name="mssqlserver_2530"></a>MSSQLSERVER_2530
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|2530|  
|Source de l’événement|MSSQLSERVER|  
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
  
## <a name="see-also"></a>Voir aussi  
 [Activer les index et les contraintes](../indexes/enable-indexes-and-constraints.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)  
  
  
