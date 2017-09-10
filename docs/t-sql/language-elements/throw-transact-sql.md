---
title: THROW (Transact-SQL) | Documents Microsoft
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
- THROW_TSQL
- THROW
dev_langs:
- TSQL
helpviewer_keywords:
- THROW statement
ms.assetid: 43661b89-8f13-4480-ad53-70306cbb14c5
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7e61cb9edc75dda4368e31e9eac6e4e452d4387f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="throw-transact-sql"></a>THROW (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Lève une exception et transfère l'exécution à un bloc CATCH d'une construction TRY…CATCH dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
THROW [ { error_number | @local_variable },  
        { message | @local_variable },  
        { state | @local_variable } ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *error_number*  
 Constante ou variable qui représente l'exception. *error_number* est **int** et doit être supérieure ou égale à 50 000 et inférieur ou égal à 2147483647.  
  
 *Message*  
 Chaîne ou variable qui décrit l'exception. *message* est **nvarchar (2048)**.  
  
 *état*  
 Constante ou variable comprise entre 0 et 255 qui indique l'état à associer au message. *état* est **tinyint**.  
  
## <a name="remarks"></a>Notes  
 L'instruction qui précède l'instruction THROW doit être suivie du terminateur d'instruction, le point-virgule (;).  
  
 Si une construction TRY…CATCH n'est pas disponible, la session prend fin. Le numéro de ligne et la procédure où l'exception est levée sont définis. La gravité est définie sur 16.  
  
 Si l'instruction THROW est spécifiée sans paramètres, elle doit apparaître à l'intérieur d'un bloc CATCH. Cela provoque la levée de l'exception interceptée. Toute erreur qui se produit dans une instruction THROW entraîne la fin du lot d’instruction.  
  
 % est un caractère réservé dans le texte du message d'une instruction THROW et doit être placé dans une séquence d'échappement. Doublez le caractère % pour retourner % en tant que partie du texte du message, par exemple « L'augmentation a dépassé de 15 %% la valeur d'origine. »  
  
## <a name="differences-between-raiserror-and-throw"></a>Différences entre RAISERROR et THROW  
 Le tableau suivant répertorie quelques-unes des différences entre les instructions RAISERROR et THROW.  
  
|RAISERROR (instruction)|Instruction THROW|  
|-------------------------|---------------------|  
|Si un *msg_id* est passé à RAISERROR, l’ID doit être défini dans sys.messages.|Le *error_number* paramètre n’a pas à être défini dans sys.messages.|  
|Le *chaîne_du_message* paramètre peut contenir **printf** mise en forme de styles.|Le *message* paramètre n’accepte pas **printf** mise en forme du style.|  
|Le *gravité* paramètre spécifie la gravité de l’exception.|Il est sans *gravité* paramètre. La gravité d'exception est toujours définie sur 16.|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-throw-to-raise-an-exception"></a>A. Utilisation de THROW pour lever une exception  
 L’exemple suivant montre comment utiliser la `THROW` instruction pour lever une exception.  
  
```tsql  
THROW 51000, 'The record does not exist.', 1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Msg 51000, Level 16, State 1, Line 1`  
  
 `The record does not exist.`  
  
### <a name="b-using-throw-to-raise-an-exception-again"></a>B. Utilisation de THROW pour lever à nouveau une exception  
 L'exemple suivant montre comment utiliser l'instruction `THROW` pour lever une nouvelle fois la dernière exception levée.  
  
```tsql  
USE tempdb;  
GO  
CREATE TABLE dbo.TestRethrow  
(    ID INT PRIMARY KEY  
);  
BEGIN TRY  
    INSERT dbo.TestRethrow(ID) VALUES(1);  
--  Force error 2627, Violation of PRIMARY KEY constraint to be raised.  
    INSERT dbo.TestRethrow(ID) VALUES(1);  
END TRY  
BEGIN CATCH  
  
    PRINT 'In catch block.';  
    THROW;  
END CATCH;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `PRINT 'In catch block.';`  
  
 `Msg 2627, Level 14, State 1, Line 1`  
  
 `Violation of PRIMARY KEY constraint 'PK__TestReth__3214EC272E3BD7D3'. Cannot insert duplicate key in object 'dbo.TestRethrow'.`  
  
 `The statement has been terminated.`  
  
### <a name="c-using-formatmessage-with-throw"></a>C. Utilisation de FORMATMESSAGE avec THROW  
 L'exemple suivant indique comment utiliser la fonction `FORMATMESSAGE` avec `THROW` pour générer un message d'erreur personnalisé. L'exemple commence par créer un message d'erreur défini par l'utilisateur à l'aide de `sp_addmessage`. Étant donné que l’instruction THROW n’autorise pas les paramètres de substitution dans le *message* paramètre dans la même manière que RAISERROR, la fonction FORMATMESSAGE est utilisé pour passer les trois valeurs de paramètre attendus par le message d’erreur 60000.  
  
```tsql  
EXEC sys.sp_addmessage  
     @msgnum   = 60000  
,@severity = 16  
,@msgtext  = N'This is a test message with one numeric parameter (%d), one string parameter (%s), and another string parameter (%s).'  
    ,@lang = 'us_english';   
GO  
  
DECLARE @msg NVARCHAR(2048) = FORMATMESSAGE(60000, 500, N'First string', N'second string');   
  
THROW 60000, @msg, 1;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Msg 60000, Level 16, State 1, Line 2`  
  
 `This is a test message with one numeric parameter (500), one string parameter (First string), and another string parameter (second string).`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-throw-to-raise-an-exception"></a>D. Utilisation de THROW pour lever une exception  
 L’exemple suivant montre comment utiliser la `THROW` instruction pour lever une exception.  
  
```tsql  
THROW 51000, 'The record does not exist.', 1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Msg 51000, Level 16, State 1, Line 1`  
  
 `The record does not exist.`  
  
## <a name="see-also"></a>Voir aussi  
 [FORMATMESSAGE &#40; Transact-SQL &#41;](../../t-sql/functions/formatmessage-transact-sql.md)   
 [Gravité des erreurs du moteur de base de données](../../relational-databases/errors-events/database-engine-error-severities.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)   
 [GOTO &#40; Transact-SQL &#41;](../../t-sql/language-elements/goto-transact-sql.md)   
 [BEGIN... FIN &#40; Transact-SQL &#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [XACT_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/xact-state-transact-sql.md)   
 [SET XACT_ABORT &#40; Transact-SQL &#41;](../../t-sql/statements/set-xact-abort-transact-sql.md)  
  
  


