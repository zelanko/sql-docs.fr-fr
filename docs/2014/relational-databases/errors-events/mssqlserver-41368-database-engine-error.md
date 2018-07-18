---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8619e3cfb8766caab9d9afbe5ed166761eeeb04f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409718"
---
# <a name="mssqlserver41368"></a>MSSQLSERVER_41368
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41368|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|Texte du message|L'accès aux tables optimisées en mémoire selon le niveau d'isolement READ COMMITTED est pris en charge uniquement pour les transactions validées automatiquement. Cela n'est pas pris en charge pour les transactions explicites ou implicites. Spécifiez un niveau d'isolement pris en charge pour la table optimisée en mémoire à l'aide d'un indicateur de table, comme WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Explication  
 L'accès aux tables optimisées en mémoire selon le niveau d'isolement READ COMMITTED est pris en charge uniquement pour les transactions validées automatiquement. Pour plus d’informations, consultez [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md).  
  
 Lors de l'accès à une table optimisée en mémoire à partir d'une transaction explicite démarrée par BEGIN TRANSACTION, ou à partir d'une transaction implicite, si IMPLICIT_TRANSACTIONS a la valeur ON, le niveau d'isolement READ COMMITTED n'est pas pris en charge.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Lors de l'accès à une table optimisée en mémoire à partir d'une transaction READ COMMITTED implicite ou explicite, utilisez SNAPSHOT pour accéder à la table. Cela peut être obtenue à l’aide de l’indicateur de table WITH (SNAPSHOT) (pour plus d’informations, consultez [instructions pour les niveaux d’Isolation des transactions avec Tables optimisées en mémoire](../in-memory-oltp/memory-optimized-tables.md)) ou en définissant la base de données d’option MEMORY_OPTIMIZED_ELEVATE_TO_ On d’instantané (pour plus d’informations, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)).  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
