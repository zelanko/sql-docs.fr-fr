---
title: Niveaux d’isolement | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8a6a82bf-273c-40ab-a101-46bd3615db8a
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7fb341cb36e97fbd06f38363c84d87f975d23eed
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37329959"
---
# <a name="transaction-isolation-levels"></a>Niveaux d'isolement des transactions
  Les niveaux d'isolation suivants sont pris en charge pour les transactions qui accèdent à des tables mémoire optimisées.  
  
-   SNAPSHOT  
  
-   REPEATABLE READ  
  
-   SERIALIZABLE  
  
-   READ COMMITTED  
  
 Le niveau d'isolation de la transaction peut être spécifié dans le bloc Atomic d'une procédure stockée compilée en mode natif. Pour plus d’informations, consultez [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql). Lors de l'accès aux tables mémoire optimisées à partir du [!INCLUDE[tsql](../includes/tsql-md.md)] interprété, le niveau d'isolation peut être spécifié à l'aide d'indicateurs de table.  
  
 Vous devez spécifier le niveau d'isolation de la transaction lorsque vous définissez une procédure stockée compilée en mode natif. Vous devez spécifier le niveau d'isolation dans les indicateurs de table lors de l'accès aux tables mémoire optimisées à partir des transactions utilisateur en mode [!INCLUDE[tsql](../includes/tsql-md.md)] interprété. Pour plus d’informations, consultez [instructions pour les niveaux d’Isolation des transactions avec Tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Le niveau d'isolation READ COMMITTED est pris en charge pour les tables mémoire optimisées avec des transactions validées automatiquement. READ COMMITTED n'est pas valide dans les transactions utilisateur ou dans un bloc atomique. READ COMMITTED n'est pas pris en charge avec les transactions utilisateur explicites ou implicites. Le niveau d'isolation READ_COMMITTED_SNAPSHOT est pris en charge pour les tables mémoire optimisées avec transactions en mode de validation automatique et uniquement si la requête n'accède pas à des tables sur disque. En outre, les transactions démarrées à l'aide du [!INCLUDE[tsql](../includes/tsql-md.md)] interprété avec le niveau d'isolation SNAPSHOT ne peuvent pas accéder aux tables mémoire optimisées. Les transactions utilisées avec le [!INCLUDE[tsql](../includes/tsql-md.md)] interprété et le niveau d'isolation REPEATABLE READ ou SERIALIZABLE doivent accéder aux tables mémoire optimisées avec le niveau d'isolation SNAPSHOT. Pour plus d’informations sur ce scénario, consultez [les Transactions entre conteneurs](cross-container-transactions.md).  
  
 READ COMMITTED est le niveau d'isolement par défaut dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Lorsque le niveau d'isolation de la session est READ COMMITED (ou un niveau inférieur), procédez comme suit :  
  
-   Utilisez explicitement un indicateur de niveau d'isolation supérieur pour accéder à la table mémoire optimisée, par exemple WITH (SNAPSHOT).  
  
-   Spécifiez l'option SET `MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT`, qui définira le niveau d'isolation pour la table mémoire optimisée sur SNAPSHOT (comme si vous aviez inclus des indicateurs WITH(SNAPSHOT) à chaque table mémoire optimisée). Pour plus d’informations sur `MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT`, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
 Alternativement, si le niveau d'isolement de la session est READ COMMITTED, utilisez des transactions en mode de validation automatique.  
  
 Les transactions SNAPSHOT démarrées dans le [!INCLUDE[tsql](../includes/tsql-md.md)] interprété ne peuvent pas accéder aux tables mémoire optimisées.  
  
 Les niveaux d'isolation des transactions pris en charge pour les tables mémoire optimisées fournissent les mêmes garanties logiques que les tables sur disque. Le mécanisme utilisé pour fournir des garanties de niveau d'isolation est différent.  
  
 Pour les tables sur disque, la plupart des garanties de niveau d'isolation sont implémentées à l'aide d'un verrouillage, qui empêche les conflits par blocage. Pour les tables mémoire optimisées, les garanties sont appliquées à l'aide d'un mécanisme de détection de conflit, qui évite de prendre des verrous. L'exception est l'isolation SNAPSHOT sur les tables sur disque. Cela est implémenté de façon similaire à l'isolation SNAPSHOT sur les tables mémoire optimisées à l'aide d'un mécanisme de détection de conflit.  
  
 SNAPSHOT  
 Ce niveau d'isolation spécifie que les données lues par n'importe quelle instruction d'une transaction représenteront la version cohérente d'un point de vue transactionnel des données qui existaient au début de la transaction. La transaction peut seulement reconnaître les modifications de données qui ont été validées avant qu'elle ne commence. Autrement dit, les modifications de données effectuées par d'autres transactions après le début de la transaction active ne sont pas visibles pour les instructions qui s'exécutent dans le cadre de ladite transaction. Les instructions d'une transaction obtiennent un instantané des données validées telles qu'elles existaient au début de cette transaction.  
  
 Les opérations d'écriture (mises à jour, insertions et suppressions) sont toujours totalement isolées des autres transactions. Par conséquent, les opérations d'écriture dans une transaction SNAPSHOT peuvent être en conflit avec les opérations d'écriture d'autres transactions. Lorsque la transaction active tente de mettre à jour ou de supprimer une ligne mise à jour ou supprimée par une autre transaction validée après le début de la transaction active, la transaction prend fin avec le message d'erreur suivant.  
  
 Erreur 41302. La transaction en cours a tenté de mettre à jour un enregistrement dans la table X qui a été mis à jour depuis le début de cette transaction. La transaction a été abandonnée.  
  
 Lorsque la transaction active tente d'insérer une ligne avec la même valeur de clé primaire qu'une ligne insérée par une autre transaction validée avant la transaction active, il y a un échec de validation avec le message d'erreur suivant.  
  
 Erreur 41325. La transaction en cours n'a pas été validée en raison d'un échec de validation SERIALIZABLE.  
  
 Si une transaction écrit sur une table qui est supprimée avant la validation de la transaction, celle-ci est arrêtée avec le message d'erreur suivant :  
  
 Erreur 41305. La transaction en cours n'a pas été validée en raison d'un échec de validation REPEATABLE READ.  
  
 REPEATABLE READ  
 Ce niveau d'isolation inclut les garanties fournies par le niveau d'isolation SNAPSHOT. En outre, REPEATABLE READ garantit que pour n'importe quelle ligne lue par la transaction, au moment de la validation de la transaction, la ligne n'a pas été modifiée par une autre transaction. Chaque opération de lecture dans la transaction est renouvelable jusqu'à la fin de la transaction.  
  
 Si la transaction active a lu une ligne qui a ensuite été mise à jour par une autre transaction validée avant la transaction active, la validation échoue avec le message d'erreur suivant.  
  
 Erreur 41305. La transaction en cours n'a pas été validée en raison d'un échec de validation REPEATABLE READ.  
  
 SERIALIZABLE  
 Ce niveau d'isolation inclut les garanties fournies par REPEATABLE READ. Aucune ligne fantôme n'est apparue entre l'instantané et la fin de la transaction. Les lignes fantômes correspondent à la condition de filtre d'une sélection, d'une mise à jour ou d'une suppression.  
  
 La transaction est exécutée comme s'il n'existait aucune transaction simultanée. Toutes les actions se produisent presque à un seul point de sérialisation (heure de validation).  
  
 Si l'une de ces garanties n'est pas respectée, la transaction échoue avec le message d'erreur suivant :  
  
 Erreur 41325. La transaction en cours n'a pas été validée en raison d'un échec de validation SERIALIZABLE.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des Transactions sur les Tables optimisées en mémoire](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)   
 [Instructions pour les niveaux d’Isolation des transactions avec Tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md)   
 [Instructions pour la logique de nouvelle tentative des transactions sur des tables à mémoire optimisée](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
  