---
title: Prise en charge d’OLTP en mémoire par Transact-SQL | Microsoft Docs
description: Découvrez les instructions Transact-SQL qui incluent des options de syntaxe pour prendre en charge l’OLTP en mémoire. Utilisez les liens vers des références supplémentaires sur les fonctionnalités prises en charge.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b1cc7c30-1747-4c21-88ac-e95a5e58baac
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 27f21922951ad42dc4f26625a2558b03f0425715
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753197"
---
# <a name="transact-sql-support-for-in-memory-oltp"></a>Prise en charge d'OLTP en mémoire par Transact-SQL
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes incluent des options de syntaxe pour prendre en charge l’OLTP en mémoire :  
  
-   [Options de fichiers et de groupes de fichiers ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md) (ajout de **MEMORY_OPTIMIZED_DATA**)  
  
-   [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)  
  
-   [CRÉER une base de données & #40 ; SQL Server Transact-SQL & #41 ;](../../t-sql/statements/create-database-sql-server-transact-sql.md) (ajout de **MEMORY_OPTIMIZED_DATA**)  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)  
  
-   [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
  
-   [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
-   [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)  
  
-   [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
    Dans une procédure stockée compilée en mode natif, vous pouvez déclarer une variable comme étant **NOT NULL**. Vous ne pouvez pas le faire dans une procédure stockée standard.  
  
 **AUTO_UPDATE_STATISTICS** peut avoir la valeur **ON** pour les tables optimisées en mémoire, à compter de SQL Server 2016. Pour plus d’informations, consultez [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md).  
  
 [SET STATISTICS XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-xml-transact-sql.md) L’option ON n’est pas prise en charge avec les procédures stockées compilées en mode natif.  
  
 Pour plus d’informations sur les fonctionnalités non prises en charge, consultez [Les constructions Transact-SQL ne sont pas prises en charge par l’OLTP en mémoire](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
 Pour plus d’informations sur les constructions prises en charge dans et sur les procédures stockées compilées en mode natif, consultez [Fonctionnalités prises en charge pour les modules T-SQL compilés en mode natif](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md) et [Constructions prises en charge dans les procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md).  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)   
 [Problèmes de migration pour les procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Fonctionnalités SQL Server non prises en charge pour l’OLTP en mémoire](../../relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md)   
 [Procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
