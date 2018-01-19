---
title: DEALLOCATE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DEALLOCATE
- DEALLOCATE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- locking [SQL Server], cursors
- DEALLOCATE statement
- deallocations [SQL Server]
- deleting cursor references
- removing cursor references
ms.assetid: c75cf73d-0268-4c57-973d-b8a84ff801fa
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f7dd1a4deca2a3c6db7db7596c94f0def97934da
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="deallocate-transact-sql"></a>DEALLOCATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Supprime une référence de curseur. Lorsque la dernière référence de curseur désallouée, les structures de données contenant le curseur sont publiées par [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DEALLOCATE { { [ GLOBAL ] cursor_name } | @cursor_variable_name }  
```  
  
## <a name="arguments"></a>Arguments  
 *cursor_name*  
 Nom d'un curseur déjà déclaré. Si un global et un curseur local portent *cursor_name* comme leur nom, *cursor_name* fait référence au curseur global si GLOBAL est précisé et au curseur local si GLOBAL n’est pas spécifié.  
  
 @*cursor_variable_name*  
 Est le nom d’un **curseur** variable. @*nom_de_variable_de_curseur* doit être de type **curseur**.  
  
## <a name="remarks"></a>Notes  
 Les instructions affectant les curseurs font référence à ceux-ci à l'aide d'un nom ou d'une variable de curseur. DEALLOCATE supprime l'association entre un curseur et le nom ou la variable de curseur. S'il s'agit du dernier nom ou de la dernière variable qui référence le curseur, ce dernier est désalloué et les ressources qu'il utilisait sont libérées. DEALLOCATE libère les verrous de défilement qui protègent l'isolation d'extractions. Les verrous de transaction, utilisés pour protéger les mises à jour, notamment les mises à jour pointées par le curseur, sont maintenus jusqu'à la fin de la transaction.  
  
 L'instruction DECLARE CURSOR alloue et associe un curseur à un nom de curseur.  
  
```  
DECLARE abc SCROLL CURSOR FOR  
SELECT * FROM Person.Person;  
```  
  
 Dès qu'un nom de curseur est associé à un curseur, vous ne pouvez pas lui affecter un autre curseur de même portée (GLOBAL ou LOCAL) tant que ce curseur n'a pas été libéré.  
  
 Une variable de curseur est associée à un curseur à l'aide de l'une des deux méthodes suivantes :  
  
-   en spécifiant son nom à l'aide d'une instruction SET qui affecte un curseur à une variable de curseur ;  
  
    ```  
    DECLARE @MyCrsrRef CURSOR;  
    SET @MyCrsrRef = abc;  
    ```  
  
-   en créant et en associant un curseur à une variable sans qu'il y ait de nom de curseur défini.  
  
    ```  
    DECLARE @MyCursor CURSOR;  
    SET @MyCursor = CURSOR LOCAL SCROLL FOR  
    SELECT * FROM Person.Person;  
    ```  
  
 Un DEALLOCATE @*nom_de_variable_de_curseur* instruction supprime uniquement la référence de la variable nommée au curseur. La variable est libérée uniquement lorsqu'elle est hors de portée à la fin d'un lot, d'une procédure stockée ou d'un déclencheur. Après un DEALLOCATE @*nom_de_variable_de_curseur* instruction, la variable peut être associée à un autre curseur à l’aide de l’instruction SET.  
  
```  
USE AdventureWorks2012;  
GO  
  
DECLARE @MyCursor CURSOR;  
SET @MyCursor = CURSOR LOCAL SCROLL FOR  
    SELECT * FROM Sales.SalesPerson;  
  
DEALLOCATE @MyCursor;  
  
SET @MyCursor = CURSOR LOCAL SCROLL FOR  
    SELECT * FROM Sales.SalesTerritory;  
GO  
```  
  
 Il n'est pas nécessaire de désallouer explicitement une variable de curseur. Elle est implicitement désallouée une fois qu'elle est hors de portée.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, tout utilisateur valide a l'autorisation d'utiliser l'instruction DEALLOCATE.  
  
## <a name="examples"></a>Exemples  
 Le script suivant montre comment les curseurs sont maintenus jusqu'à ce que le dernier nom ou la variable les référençant aient été libérés.  
  
```  
USE AdventureWorks2012;  
GO  
-- Create and open a global named cursor that  
-- is visible outside the batch.  
DECLARE abc CURSOR GLOBAL SCROLL FOR  
    SELECT * FROM Sales.SalesPerson;  
OPEN abc;  
GO  
-- Reference the named cursor with a cursor variable.  
DECLARE @MyCrsrRef1 CURSOR;  
SET @MyCrsrRef1 = abc;  
-- Now deallocate the cursor reference.  
DEALLOCATE @MyCrsrRef1;  
-- Cursor abc still exists.  
FETCH NEXT FROM abc;  
GO  
-- Reference the named cursor again.  
DECLARE @MyCrsrRef2 CURSOR;  
SET @MyCrsrRef2 = abc;  
-- Now deallocate cursor name abc.  
DEALLOCATE abc;  
-- Cursor still exists, referenced by @MyCrsrRef2.  
FETCH NEXT FROM @MyCrsrRef2;  
-- Cursor finally is deallocated when last referencing  
-- variable goes out of scope at the end of the batch.  
GO  
-- Create an unnamed cursor.  
DECLARE @MyCursor CURSOR;  
SET @MyCursor = CURSOR LOCAL SCROLL FOR  
SELECT * FROM Sales.SalesTerritory;  
-- The following statement deallocates the cursor  
-- because no other variables reference it.  
DEALLOCATE @MyCursor;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CLOSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [Curseurs](../../relational-databases/cursors.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [FETCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/fetch-transact-sql.md)   
 [OPEN &#40;Transact-SQL&#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  
