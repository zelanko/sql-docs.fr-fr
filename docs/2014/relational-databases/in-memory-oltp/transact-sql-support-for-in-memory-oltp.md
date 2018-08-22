---
title: Prise en charge d’OLTP en mémoire par Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
caps.latest.revision: 52
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83a6cbab37e328110287b286d70a1c31cc26a36a
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393456"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Prise en charge d'OLTP en mémoire par Transact-SQL
  Vous pouvez accédez aux tables optimisées en mémoire à l'aide d'une requête Transact-SQL ou d'une instruction DML (SELECT, INSERT, UPDATE ou DELETE), d'une instruction ad hoc et d'un module SQL, par exemple des procédures stockées, des fonctions table, des fonctions scalaires, des déclencheurs et des vues. Pour plus d’informations, consultez [optimisées en mémoire aux Tables à l’aide de Transact-SQL interprété](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).  
  
 Les procédures stockées qui font référence uniquement aux tables optimisées en mémoire peuvent être nativement compilées en code machine ce qui offre des gains de performances par rapport à des procédures stockées (disques) interprétées. Pour bénéficier d'un accès optimisé aux tables optimisées en mémoire, utilisez des procédures stockées compilées en mode natif. Pour plus d’informations, consultez [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md).  
  
 Lors de la création et de la modification d'objets de base de données (instructions DDL), les instructions suivantes ont été modifiées :  
  
-   [ALTER DATABASE File et Options de groupe de fichiers &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (consultez `MEMORY_OPTIMIZED_DATA`)  
  
-   [CRÉER une base de données &#40;SQL Server Transact-SQL&#41; ](/sql/t-sql/statements/create-database-sql-server-transact-sql) (consultez `MEMORY_OPTIMIZED_DATA`)  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-procedure-transact-sql) (consultez `NATIVE_COMPILATION`, `SCHEMABINDING`, `EXECUTE AS`, et `BEGIN ATOMIC`)  
  
-   [CREATE TABLE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-table-transact-sql) (consultez `MEMORY_OPTIMIZED`, `DURABILITY`, `BUCKET_COUNT`, `INDEX`, et `HASH`)  
  
-   [Création d’un TYPE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-type-transact-sql) (consultez `MEMORY_OPTIMIZED`, `BUCKET_COUNT`, `INDEX`, et `HASH`)  
  
-   [DÉCLARER @local_variable &#40;Transact-SQL&#41; ](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (consultez `NULL`  |  `NOT NULL`)  
  
 Les tables optimisées en mémoire prennent en charge `PRIMARY KEY` et `NOT NULL`. Pour plus d’informations sur l’implémentation de contraintes non prises en charge, consultez [migration vérifier et Foreign Key Constraints](../../database-engine/migrating-check-and-foreign-key-constraints.md).  
  
 Pour plus d’informations sur les fonctionnalités non prises en charge, consultez [Les constructions Transact-SQL ne sont pas prises en charge par l’OLTP en mémoire](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Types de données pris en charge](supported-data-types-for-in-memory-oltp.md)  
  
-   [Accès aux tables à mémoire optimisée à l’aide du Transact-SQL interprété](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [Vues système, procédures stockées, DMV et types d’attente pour l’OLTP en mémoire](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;optimisation en mémoire&#41;](in-memory-oltp-in-memory-optimization.md)   
 [Problèmes de migration pour les procédures stockées compilées en mode natif](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Fonctionnalités prises en charge de SQL Server](unsupported-sql-server-features-for-in-memory-oltp.md)   
 [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)  
  
  
