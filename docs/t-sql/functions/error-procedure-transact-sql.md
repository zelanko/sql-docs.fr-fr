---
title: ERROR_PROCEDURE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ERROR_PROCEDURE_TSQL
- ERROR_PROCEDURE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_PROCEDURE function
- messages [SQL Server], trigger where occurred
- errors [SQL Server], stored procedure where occurred
- TRY...CATCH [SQL Server]
- CATCH block
- messages [SQL Server], stored procedure where occurred
- errors [SQL Server], trigger where occurred
ms.assetid: b81edbf0-856a-498f-ba87-48ff1426d980
caps.latest.revision: 44
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 87ee3dfd6ee464fd7bc0e6dc542eb5bd49afb49b
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39455193"
---
# <a name="errorprocedure-transact-sql"></a>ERROR_PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Cette fonction retourne le nom de la procédure stockée ou du déclencheur où une erreur se produit, si cette erreur a entraîné l’exécution du bloc CATCH d’une construction TRY…CATCH.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ERROR_PROCEDURE ( )  
```  
  
## <a name="return-types"></a>Types de retour  
**nvarchar(128)**  
  
## <a name="return-value"></a>Valeur retournée  
Quand elle est appelée dans un bloc CATCH de procédure stockée où une erreur se produit, la fonction `ERROR_PROCEDURE` retourne le nom de cette procédure stockée.  
  
`ERROR_PROCEDURE` retourne la valeur NULL si l’erreur ne s’est pas produite dans une procédure stockée ou un déclencheur.  
  
`ERROR_PROCEDURE` retourne NULL quand l’appel a lieu en dehors de l’étendue d’un bloc CATCH.  
  
## <a name="remarks"></a>Notes   
`ERROR_PROCEDURE` prend en charge les appels à partir de n’importe quel emplacement dans l’étendue d’un bloc CATCH.  
  
`ERROR_PROCEDURE` retourne le nom de la procédure stockée ou du déclencheur où une erreur se produit, quel que soit le nombre de fois où elle s’exécute ou l’emplacement de son exécution dans l’étendue du bloc `CATCH`. Ce comportement contraste avec celui d’une fonction comme @@ERROR, qui retourne uniquement un numéro d’erreur dans l’instruction immédiatement après celle qui a provoqué une erreur.  
  
Dans un bloc `CATCH` imbriqué, `ERROR_PROCEDURE` retourne le numéro d’erreur spécifique à l’étendue du bloc `CATCH` qui a référencé ce bloc `CATCH`. Par exemple, le bloc `CATCH` d’une construction TRY...CATCH externe peut comporter une construction `TRY...CATCH` interne. À l’intérieur de ce bloc `CATCH` interne, `ERROR_PROCEDURE` retourne le numéro de l’erreur qui a appelé le bloc `CATCH` interne. Si `ERROR_PROCEDURE` s’exécute dans le bloc `CATCH` externe, elle retourne le numéro de l’erreur qui a appelé ce bloc `CATCH` externe.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]
  
### <a name="a-using-errorprocedure-in-a-catch-block"></a>A. Utilisation d'ERROR_PROCEDURE dans un bloc CATCH  
L’exemple suivant illustre une procédure stockée qui génère une erreur de division par zéro. `ERROR_PROCEDURE` retourne le nom de la procédure stockée où l’erreur s’est produite.  
  
```  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that   
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_PROCEDURE() AS ErrorProcedure;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorProcedure
--------------------
usp_ExampleProc

(1 row(s) affected)

```  
  
### <a name="b-using-errorprocedure-in-a-catch-block-with-other-error-handling-tools"></a>B. Utilisation d'ERROR_PROCEDURE dans un bloc CATCH avec d'autres outils de gestion des erreurs  
L’exemple suivant illustre une procédure stockée qui génère une erreur de division par zéro. Outre le nom de la procédure stockée où l’erreur s’est produite, la procédure stockée retourne des informations sur cette erreur.  
  
```  
  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that   
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT   
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_MESSAGE() AS ErrorMessage,  
        ERROR_LINE() AS ErrorLine;  
        END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber ErrorSeverity ErrorState  ErrorProcedure   ErrorMessage                       ErrorLine
----------- ------------- ----------- ---------------- ---------------------------------- -----------
8134        16            1           usp_ExampleProc  Divide by zero error encountered.  6

(1 row(s) affected)

```  
  
## <a name="see-also"></a> Voir aussi  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40;Transact-SQL&#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  

