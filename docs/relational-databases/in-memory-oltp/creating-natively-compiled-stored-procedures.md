---
title: Création de procédures stockées compilées en mode natif | Microsoft Docs
description: Apprenez-en davantage sur les fonctionnalités Transact-SQL prises en charge uniquement pour les procédures stockées compilées en mode natif. Découvrez comment créer des procédures stockées compilées en mode natif dans SQL Server.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fd6c808ecc53838feb9466283c83919231ce67ad
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537582"
---
# <a name="creating-natively-compiled-stored-procedures"></a>Création de procédures stockées compilées en mode natif
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Les procédures stockées compilées en mode natif n'implémentent pas la surface d'exposition totale de programmabilité et de requête [!INCLUDE[tsql](../../includes/tsql-md.md)] . Certaines constructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ne peuvent pas être utilisées dans des procédures stockées compilées en mode natif. Pour plus d’informations, consultez [Fonctionnalités prises en charge pour les modules T-SQL compilés en mode natif](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
Les fonctionnalités [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes sont uniquement prises en charge pour les procédures stockées compilées en mode natif :  
  
-   Blocs Atomic. Pour plus d’informations, consultez [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md).  
  
-   Contraintes `NOT NULL` sur les paramètres et les variables. Vous ne pouvez pas affecter de valeurs **NULL** aux paramètres ou aux variables déclarés en tant que **NOT NULL**. Pour plus d’informations, consultez [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md).  
  
    -   `CREATE PROCEDURE dbo.myproc (@myVarchar VARCHAR(32) NOT NULL) AS (...)`  
  
    -   `DECLARE @myVarchar VARCHAR(32) NOT NULL = "Hello"; -- Must initialize to a value.`  
  
    -   `SET @myVarchar = NULL; -- Compiles, but fails during run time.`  
  
-   Liaison de schéma des procédures stockées compilées en mode natif.  
  
Les procédures stockées compilées en mode natif sont créées à l’aide de [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md). L'exemple suivant illustre une table optimisée en mémoire et une procédure stockée compilée en mode natif utilisée pour insérer des lignes dans la table.  
  
```sql  
CREATE TABLE [dbo].[T2] (  
  [c1] [int] NOT NULL, 
  [c2] [datetime] NOT NULL,
  [c3] nvarchar(5) NOT NULL, 
  CONSTRAINT [PK_T1] PRIMARY KEY NONCLUSTERED ([c1])  
  ) WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
CREATE PROCEDURE [dbo].[usp_2] (@c1 int, @c3 nvarchar(5)) 
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
)  
  DECLARE @c2 datetime = GETDATE();  
  INSERT INTO [dbo].[T2] (c1, c2, c3) values (@c1, @c2, @c3);  
END  
GO  
```  
 
Dans l’exemple de code, **NATIVE_COMPILATION** indique que cette procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] est une procédure stockée compilée en mode natif. Les options suivantes sont requises :  
  
|Option|Description|  
|------------|-----------------|  
|**SCHEMABINDING**|Les procédures stockées compilées en mode natif doivent être liées au schéma des objets référencés. Autrement dit, les tables référencées par la procédure ne peuvent pas être supprimées. Les tables référencées dans la procédure doivent inclure le nom du schéma, et les caractères génériques (\*) ne sont pas autorisés dans les requêtes (pas de `SELECT * from...`). **SCHEMABINDING** est uniquement prise en charge pour les procédures stockées compilées en mode natif dans cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**BEGIN ATOMIC**|Le corps d'une procédure stockée compilée en mode natif doit être un bloc Atomic. Les blocs Atomic garantissent l'exécution atomique de la procédure stockée. Si la procédure est appelée en dehors du contexte d'une transaction active, elle démarre une nouvelle transaction, qui valide la transaction à la fin du bloc Atomic. Deux options sont obligatoires pour les blocs Atomic dans les procédures stockées compilées en mode natif :<br /><br /> **TRANSACTION ISOLATION LEVEL**. Consultez [Niveaux d’isolement des transactions pour les tables mémoire optimisées](https://msdn.microsoft.com/library/8a6a82bf-273c-40ab-a101-46bd3615db8a) pour connaître les niveaux d’isolement pris en charge.<br /><br /> **LANGUAGE**. Le langage de la procédure stockée doit être défini sur l'un des langages ou des alias de langage disponibles.|  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
