---
title: "Création de procédures stockées compilées en mode natif | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c358b4c12f78b7d56444d0a4bd0e8e6910c174aa
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="creating-natively-compiled-stored-procedures"></a>Création de procédures stockées compilées en mode natif
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Les procédures stockées compilées en mode natif n'implémentent pas la surface d'exposition totale de programmabilité et de requête [!INCLUDE[tsql](../../includes/tsql-md.md)] . Certaines constructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ne peuvent pas être utilisées dans des procédures stockées compilées en mode natif. Pour plus d’informations, consultez [Fonctionnalités prises en charge pour les modules T-SQL compilés en mode natif](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
 À l'inverse, plusieurs fonctionnalités [!INCLUDE[tsql](../../includes/tsql-md.md)] ne sont prises en charge que pour les procédures stockées compilées en mode natif :  
  
-   Blocs Atomic. Pour plus d’informations, voir [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md).  
  
-   Contraintes **NOT NULL** sur les paramètres et les variables. Vous ne pouvez pas affecter de valeurs **NULL** aux paramètres ou aux variables déclarés en tant que **NOT NULL**. Pour plus d’informations, consultez [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md).  
  
    -   CREATE PROCEDURE dbo.myproc (@myVarchar  varchar(32)  **not null**) ...  
  
    -   DECLARE @myVarchar  varchar(32)  **not null = "Hello"**; -- *(initialisation de valeur requise)*  
  
    -   SET @myVarchar **= null**; -- *(compilation, mais échec au moment de l’exécution)*  
  
-   Liaison de schéma des procédures stockées compilées en mode natif.  
  
 Les procédures stockées compilées en mode natif sont créées à l’aide de [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md). L'exemple suivant illustre une table optimisée en mémoire et une procédure stockée compilée en mode natif utilisée pour insérer des lignes dans la table.  
  
```tsql  
create table dbo.Ord  
(OrdNo integer not null primary key nonclustered,   
 OrdDate datetime not null,   
 CustCode nvarchar(5) not null)   
 with (memory_optimized=on)  
go  
  
create procedure dbo.OrderInsert(@OrdNo integer, @CustCode nvarchar(5))  
with native_compilation, schemabinding  
as   
begin atomic with  
(transaction isolation level = snapshot,  
language = N'English')  
  
  declare @OrdDate datetime = getdate();  
  insert into dbo.Ord (OrdNo, CustCode, OrdDate) values (@OrdNo, @CustCode, @OrdDate);  
end  
go  
```  
  
 Dans l’exemple de code, **NATIVE_COMPILATION** indique que cette procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] est une procédure stockée compilée en mode natif. Les options suivantes sont requises :  
  
|Option|Description|  
|------------|-----------------|  
|**SCHEMABINDING**|Les procédures stockées compilées en mode natif doivent être liées au schéma des objets référencés. Autrement dit, les tables référencées par la procédure ne peuvent pas être supprimées. Les tables référencées dans la procédure doivent inclure le nom du schéma, et les caractères génériques (\*) ne sont pas autorisés dans les requêtes (pas de `SELECT * from...`). **SCHEMABINDING** est uniquement prise en charge pour les procédures stockées compilées en mode natif dans cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**BEGIN ATOMIC**|Le corps d'une procédure stockée compilée en mode natif doit être un bloc Atomic. Les blocs Atomic garantissent l'exécution atomique de la procédure stockée. Si la procédure est appelée en dehors du contexte d'une transaction active, elle démarre une nouvelle transaction, qui valide la transaction à la fin du bloc Atomic. Deux options sont obligatoires pour les blocs Atomic dans les procédures stockées compilées en mode natif :<br /><br /> **TRANSACTION ISOLATION LEVEL**. Consultez [Niveaux d’isolement des transactions pour les tables mémoire optimisées](http://msdn.microsoft.com/library/8a6a82bf-273c-40ab-a101-46bd3615db8a) pour connaître les niveaux d’isolement pris en charge.<br /><br /> **LANGUAGE**. Le langage de la procédure stockée doit être défini sur l'un des langages ou des alias de langage disponibles.|  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
