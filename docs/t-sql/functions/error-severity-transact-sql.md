---
title: ERROR_SEVERITY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_SEVERITY_TSQL
- ERROR_SEVERITY
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], severity
- messages [SQL Server], severity
- TRY...CATCH [SQL Server]
- CATCH block
- ERROR_SEVERITY function
ms.assetid: 50228f2f-6949-4d2e-8e43-fad11bf973ab
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 5c3cd713bcbb239c037ff0a43083058de117cb9b
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="errorseverity-transact-sql"></a>ERROR_SEVERITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie le degré de gravité de l'erreur qui a engendré l'exécution du bloc CATCH d'une structure TRY…CATCH.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ERROR_SEVERITY ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="return-value"></a>Valeur retournée  
 Lorsqu'elle est appelée dans un bloc CATCH, elle renvoie le degré de gravité du message d'erreur à l'origine de l'exécution du bloc CATCH.  
  
 Retourne NULL si l'appel a lieu en dehors de l'étendue d'un bloc CATCH.  
  
## <a name="remarks"></a>Notes  
 ERROR_SEVERITY peut être appelée depuis n'importe quel emplacement dans le champ d'un bloc CATCH.  
  
 ERROR_SEVERITY renvoie le degré de gravité de l'erreur, indépendamment du nombre d'exécutions ou de l'endroit où elle est exécutée dans le champ du bloc CATCH. Cela diffère des fonctions telles que @@ERROR, qui retourne uniquement le numéro d’erreur dans l’instruction immédiatement après celle qui provoque une erreur, ou dans la première instruction d’un bloc CATCH.  
  
 Dans les blocs CATCH imbriqués, ERROR_SEVERITY renvoie la gravité d'erreur propre au champ du bloc CATCH dans lequel elle est référencée. Par exemple, le bloc CATCH d'une construction TRY...CATCH externe peut comporter une construction TRY...CATCH imbriquée. Dans un bloc CATCH imbriqué, ERROR_SEVERITY renvoie le degré de gravité depuis l'erreur qui a appelé ce bloc. Si ERROR_SEVERITY est exécutée dans le bloc CATCH externe, elle renvoie le degré de gravité à partir de l'erreur qui a appelé ce bloc CATCH.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-errorseverity-in-a-catch-block"></a>A. Utilisation de ERROR_SEVERITY dans un bloc CATCH  
 L’exemple suivant montre un `SELECT` instruction qui génère une erreur de division par zéro. La gravité de l'erreur est renvoyée.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_SEVERITY() AS ErrorSeverity;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorseverity-in-a-catch-block-with-other-error-handling-tools"></a>B. Utilisation de ERROR_SEVERITY dans un bloc CATCH avec d'autres outils de gestion des erreurs  
 L'exemple suivant montre une instruction `SELECT` qui génère une erreur de division par zéro. Outre le degré de gravité, la procédure renvoie également les informations relatives à l'erreur.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errorseverity-in-a-catch-block-with-other-error-handling-tools"></a>C. Utilisation de ERROR_SEVERITY dans un bloc CATCH avec d'autres outils de gestion des erreurs  
 L'exemple suivant montre une instruction `SELECT` qui génère une erreur de division par zéro. Outre le degré de gravité, la procédure renvoie également les informations relatives à l'erreur.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  


