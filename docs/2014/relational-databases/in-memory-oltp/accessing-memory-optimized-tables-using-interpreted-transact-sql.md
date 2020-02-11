---
title: Accès aux tables optimisées en mémoire à l’aide du Transact-SQL interprété | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c81ac6c0c8dcf7e24c80b426654164c668fcf3a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62468606"
---
# <a name="accessing-memory-optimized-tables-using-interpreted-transact-sql"></a>Accès aux tables optimisées en mémoire à l’aide du Transact-SQL interprété
  À quelques exceptions près, vous accédez aux tables mémoire optimisées à l'aide d'une requête [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'une opération DML (SELECT, INSERT, UPDATE ou DELETE), de lots ad hoc et de modules SQL, tels que des procédures stockées, des fonctions table, des déclencheurs et des vues.  
  
 Le [!INCLUDE[tsql](../../includes/tsql-md.md)] interprété fait référence à des lots ou des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] autres qu'une procédure stockée compilée en mode natif. L'accès par [!INCLUDE[tsql](../../includes/tsql-md.md)] interprété aux tables mémoire optimisées est appelé un accès d'interopérabilité.  
  
 Les tables mémoire optimisées sont également accessibles à l'aide d'une procédure stockée compilée en mode natif. Les procédures stockées compilées en mode natif sont recommandées pour les opérations OLTP critiques pour les performances.  
  
 L'accès en [!INCLUDE[tsql](../../includes/tsql-md.md)] interprété est recommandé dans les scénarios suivants :  
  
-   Requêtes ad hoc et tâches d'administration.  
  
-   Requêtes de rapports qui utilisent généralement des constructions non disponibles dans les procédures stockées compilées en mode natif (telles que les fonctions de fenêtre).  
  
-   Pour migrer des parties de votre application qui ont un impact sur les performances vers des tables mémoire optimisées, avec des modifications de code minimes (ou sans aucune modification du code). Potentiellement, vous constaterez de meilleures performances en migrant des tables. Si vous migrez ensuite des procédures stockées vers des procédures stockées compilées en mode natif, vous constaterez des améliorations de performances accrues.  
  
-   Lorsqu'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] n'est pas disponible pour les procédures stockées compilées en mode natif.  
  
 Les constructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes ne sont pas prises en charge dans les procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] interprétées qui accèdent aux données dans une table mémoire optimisée.  
  
|Domaine|Non pris en charge|  
|----------|-----------------|  
|Accès aux tables|TRUNCATE TABLE<br /><br /> MERGE (table mémoire optimisée comme cible).<br /><br /> Curseurs DYNAMIC et KEYSET (dégradés automatiquement en STATIC).<br /><br /> Accédez aux modules CLR à l'aide de la connexion contextuelle.<br /><br /> Référencement d'une table mémoire optimisée à partir d'une vue indexée.|  
|Bases de données croisées|Requêtes de bases de données croisées<br /><br /> Transactions de bases de données croisées<br /><br /> Serveurs liés|  
  
## <a name="table-hints"></a>Indicateurs de table  
 Pour plus d'informations sur les indicateurs de table, consultez. [Indicateurs de table &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table). L’isolement d’instantané a été [!INCLUDE[hek_2](../../includes/hek-2-md.md)]ajouté pour prendre en charge.  
  
 Les indicateurs de table suivants ne sont pas pris en charge lors de l'accès à une table de mémoire optimisée à l'aide du [!INCLUDE[tsql](../../includes/tsql-md.md)]interprété.  
  
|||||  
|-|-|-|-|  
|HOLDLOCK|IGNORE_CONSTRAINTS|IGNORE_TRIGGERS|NOWAIT|  
|PAGLOCK|READCOMMITTED|READCOMMITTEDLOCK|READPAST|  
|READUNCOMMITTED|ROWLOCK|SPATIAL_WINDOW_MAX_CELLS = *integer*|TABLOCK|  
|TABLOCKXX|UPDLOCK|XLOCK||  
  
 Lors de l'accès à une table mémoire optimisée à partir d'une transaction explicite ou implicite à l'aide du [!INCLUDE[tsql](../../includes/tsql-md.md)] interprété, vous devez inclure un indicateur de table de niveau d'isolement tel que SNAPSHOT, REPEATABLEREAD ou SERIALIZABLE, ou utiliser MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT. Pour plus d’informations, consultez [instructions pour les niveaux d’isolation des transactions avec des tables optimisées en mémoire](memory-optimized-tables.md) et [options ALTER database SET &#40;&#41;Transact-SQL ](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
> [!NOTE]  
>  Un indicateur de table de niveau d'isolation n'est pas obligatoire pour les tables mémoire optimisées accessibles par des requêtes qui s'exécutent en mode de validation automatique.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge d'OLTP en mémoire par Transact-SQL](transact-sql-support-for-in-memory-oltp.md)   
 [Migration vers OLTP en mémoire](migrating-to-in-memory-oltp.md)  
  
  
