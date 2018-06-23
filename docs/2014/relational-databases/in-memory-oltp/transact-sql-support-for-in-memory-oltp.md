---
title: Prise en charge d’OLTP en mémoire par Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
caps.latest.revision: 52
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: f5c7dd02a31a466e5e6e96a815ed27795f62f978
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045374"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Prise en charge d'OLTP en mémoire par Transact-SQL
  Vous pouvez accédez aux tables optimisées en mémoire à l'aide d'une requête Transact-SQL ou d'une instruction DML (SELECT, INSERT, UPDATE ou DELETE), d'une instruction ad hoc et d'un module SQL, par exemple des procédures stockées, des fonctions table, des fonctions scalaires, des déclencheurs et des vues. Pour plus d’informations, consultez [accès Tables à l’aide de Transact-SQL interprété](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).  
  
 Les procédures stockées qui font référence uniquement aux tables optimisées en mémoire peuvent être nativement compilées en code machine ce qui offre des gains de performances par rapport à des procédures stockées (disques) interprétées. Pour bénéficier d'un accès optimisé aux tables optimisées en mémoire, utilisez des procédures stockées compilées en mode natif. Pour plus d’informations, consultez [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md).  
  
 Lors de la création et de la modification d'objets de base de données (instructions DDL), les instructions suivantes ont été modifiées :  
  
-   [MODIFIER le fichier de base de données et les Options de groupe de fichiers &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) (consultez `MEMORY_OPTIMIZED_DATA`)  
  
-   [CRÉER une base de données &#40;SQL Server Transact-SQL&#41; ](/sql/t-sql/statements/create-database-sql-server-transact-sql) (consultez `MEMORY_OPTIMIZED_DATA`)  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-procedure-transact-sql) (consultez `NATIVE_COMPILATION`, `SCHEMABINDING`, `EXECUTE AS`, et `BEGIN ATOMIC`)  
  
-   [CREATE TABLE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-table-transact-sql) (consultez `MEMORY_OPTIMIZED`, `DURABILITY`, `BUCKET_COUNT`, `INDEX`, et `HASH`)  
  
-   [CREATE TYPE &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-type-transact-sql) (consultez `MEMORY_OPTIMIZED`, `BUCKET_COUNT`, `INDEX`, et `HASH`)  
  
-   [DÉCLARER @local_variable &#40;Transact-SQL&#41; ](/sql/t-sql/language-elements/declare-local-variable-transact-sql) (consultez `NULL`  |  `NOT NULL`)  
  
 Les tables optimisées en mémoire prennent en charge `PRIMARY KEY` et `NOT NULL`. Pour plus d’informations sur l’implémentation des contraintes non prises en charge, consultez [migration vérifier et contraintes de clé étrangère](../../database-engine/migrating-check-and-foreign-key-constraints.md).  
  
 Pour plus d’informations sur les fonctionnalités non prises en charge, consultez [Les constructions Transact-SQL ne sont pas prises en charge par l’OLTP en mémoire](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Types de données pris en charge](supported-data-types-for-in-memory-oltp.md)  
  
-   [Accès aux tables à mémoire optimisée à l’aide du Transact-SQL interprété](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)  
  
-   [Vues système, des procédures stockées, des vues de gestion dynamique et des Types d’attente pour l’OLTP en mémoire](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;optimisation en mémoire&#41;](in-memory-oltp-in-memory-optimization.md)   
 [Problèmes de migration pour les procédures stockées compilées en mode natif](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Fonctionnalités prises en charge de SQL Server](unsupported-sql-server-features-for-in-memory-oltp.md)   
 [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)  
  
  
