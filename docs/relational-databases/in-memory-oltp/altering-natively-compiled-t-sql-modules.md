---
title: "Modification de modules T-SQL compilés en mode natif | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 010318a0-6807-47c3-8ecc-bb7cb60513f0
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4696039c56ebf5f1fd6ea440cd27da84721f35b9
ms.lasthandoff: 04/11/2017

---
# <a name="altering-natively-compiled-t-sql-modules"></a>Altering Natively Compiled T-SQL Modules
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (et versions ultérieures) et [!INCLUDE[ssSDS](../../includes/sssds-md.md)] , vous pouvez effectuer des opérations ALTER sur les procédures stockées compilées en mode natif et d’autres modules T-SQL compilés en mode natif tels que des fonctions scalaires définies par l’utilisateur et des déclencheurs à l’aide de l’instruction ALTER.  
  
 Lors de l’exécution de l’instruction ALTER sur un module T-SQL compilé en mode natif, le module est recompilé à l’aide d’une nouvelle définition. Quand la recompilation est en cours, l’ancienne version du module reste disponible pour l’exécution. Une fois la compilation terminée, les exécutions de module sont purgées et la nouvelle version du module est installée. Quand vous modifiez un module T-SQL compilé en mode natif, vous pouvez modifier les options suivantes.  
  
-   Paramètres  
  
-   EXECUTE AS  
  
-   TRANSACTION ISOLATION LEVEL  
  
-   LANGUAGE  
  
-   DATEFIRST  
  
-   DATEFORMAT  
  
-   DELAYED_DURABILITY  
  
> [!NOTE]  
>  Les modules T-SQL compilés en mode natif ne peuvent pas être convertis en modules non compilés dans ce mode. Les modules T-SQL non compilés en mode natif ne peuvent pas être convertis en modules compilés dans ce mode.  
  
 Pour en savoir plus sur la fonctionnalité ALTER PROCEDURE et sur sa syntaxe, consultez [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)  
  
 Vous pouvez exécuter sp_recompile sur des modules T-SQL compilés en mode natif, ce qui entraîne leur recompilation lors de la prochaine exécution.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant représente la création d’une table optimisée en mémoire (T1) et d’une procédure stockée compilée en mode natif (SP1), qui sélectionne toutes les colonnes de la table T1. Ensuite, SP1 est modifiée pour supprimer la clause EXECUTE AS, modifier LANGUAGE et sélectionner une seule colonne (C1) à partir de T1.  
  
```  
CREATE TABLE [dbo].[T1]  
(  
[c1] [int] NOT NULL,  
[c2] [float] NOT NULL,  
CONSTRAINT [PK_T1] PRIMARY KEY NONCLUSTERED ([c1])  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
CREATE PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
)  
 SELECT c1, c2 from dbo.T1  
END  
GO  
  
ALTER PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'Dutch'  
)  
 SELECT c1 from dbo.T1  
END  
GO  
  
```  
  
  
