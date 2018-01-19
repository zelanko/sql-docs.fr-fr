---
title: RAISERROR (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 02/21/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RAISERROR
- RAISERROR_TSQL
- RAISEERROR_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sysmessages system table
- errors [SQL Server], RAISERROR statement
- user-defined error messages [SQL Server]
- system flags
- generating errors [SQL Server]
- TRY block [SQL Server]
- recording errors
- ad hoc messages
- RAISERROR statement
- CATCH block
- messages [SQL Server], RAISERROR statement
ms.assetid: 483588bd-021b-4eae-b4ee-216268003e79
caps.latest.revision: "73"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: de9b90e46c344c4d287d677c9aa17e5d635aca6d
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="raiserror-transact-sql"></a>RAISERROR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Génère un message d'erreur et lance le traitement d'erreur pour la session. RAISERROR peut soit faire référence à un message défini par l’utilisateur stocké dans la vue de catalogue sys.messages ou générer un message de manière dynamique. Ce message est renvoyé en tant que message d'erreur du serveur à l'application appelante ou à un bloc CATCH associé d'une structure TRY…CATCH. Nouvelles applications doivent utiliser [lever](../../t-sql/language-elements/throw-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
RAISERROR ( { msg_id | msg_str | @local_variable }  
    { ,severity ,state }  
    [ ,argument [ ,...n ] ] )  
    [ WITH option [ ,...n ] ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
RAISERROR ( { msg_str | @local_variable }  
    { ,severity ,state }  
    [ ,argument [ ,...n ] ] )  
    [ WITH option [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Arguments  
 *msg_id*  
 Un numéro de message d’erreur définis par l’utilisateur est stocké dans la vue de catalogue sys.messages à l’aide de sp_addmessage. Les numéros d'erreur des messages d'erreur définis par l'utilisateur doivent être supérieurs à 50 000. Lorsque *msg_id* n’est pas spécifié, RAISERROR génère un message d’erreur avec un numéro d’erreur 50 000.  
  
 *msg_str*  
 Un message défini par l’utilisateur avec mise en forme est identique à la **printf** fonction dans la bibliothèque standard C. Le message d'erreur peut compter jusqu'à 2 047 caractères. Si le message contient au moins 2 048 caractères, seuls les 2 044 premiers sont affichés et des points de suspension sont ajoutés pour indiquer que le message a été tronqué. Notez que les paramètres de substitution utilisent plus de caractères que ce que la sortie affiche en raison de son comportement de stockage interne. Par exemple, le paramètre de substitution de *%d* avec une valeur affectée de 2 produit en fait un caractère dans la chaîne de message, mais prend également jusqu'à trois caractères supplémentaires de stockage. Ce besoin de stockage réduit le nombre de caractères disponibles pour le message émis.  
  
 Lorsque *chaîne_du_message* est spécifié, RAISERROR génère un message d’erreur avec un numéro d’erreur 50 000.  
  
 *chaîne_du_message* est une chaîne de caractères avec des spécifications de conversion incorporées facultatives. Chaque spécification de conversion définit comment une valeur dans la liste d’arguments est mise en forme et placée dans un champ à l’emplacement de la spécification de conversion dans *chaîne_du_message*. Les spécifications de conversion arborent la mise en forme suivante :  
  
 % [[*flag*] [*width*] [. *précision*] [{h | l}]] *type*  
  
 Les paramètres qui peuvent être utilisés dans *chaîne_du_message* sont :  
  
 *flag*  
  
 Code qui détermine l'espacement et la justification du message substitué.  
  
|Code|Préfixe ou justification| Description|  
|----------|-----------------------------|-----------------|  
|- (moins)|Cadré à gauche|Cadre la valeur de l'argument à gauche par rapport à la largeur du champ donnée.|  
|+ (plus)|Préfixe de l’authentification|Fait précéder la valeur de l'argument d'un signe positif (+) ou négatif (-) si celle-ci est de type signé.|  
|0 (zéro)|Remplissage avec des zéros|Fait précéder le résultat de zéros jusqu'à atteindre la largeur minimale. Si zéro et le signe moins (-) sont donnés ensemble, le zéro est ignoré.|  
|# (nombre)|Préfixe 0x pour le type hexadécimal de x ou X|Lorsqu'il est utilisé avec les formats o, x ou X, le signe dièse # fait précéder n'importe quelle valeur différente de zéro respectivement de 0, 0x ou 0X. Lorsque d, i ou u sont précédés du signe dièse (#), ce dernier est ignoré.|  
|' ' (vide)|Remplissage avec des espaces|Fait précéder la valeur de sortie d'espaces si la valeur est signée et positive. Ceci sera ignoré si un signe positif (+) est inclus dans le drapeau +.|  
  
 *width*  
  
 Nombre entier qui définit la largeur minimale du champ dans lequel est placée la valeur de l'argument. Si la longueur de la valeur d’argument est égale ou supérieure à *largeur*, la valeur est imprimée sans marge intérieure. Si la valeur est inférieure à *largeur*, la valeur est complétée jusqu'à la longueur spécifiée dans *largeur*.  
  
 Un astérisque (*) signifie que la largeur est spécifiée par l'argument associé dans la liste, qui doit être un nombre entier.  
  
 *precision*  
  
 Nombre maximum de caractères extraits de l'argument pour les chaînes. Par exemple, si une chaîne compte cinq caractères et que la précision est égale à 3, seuls les trois premiers caractères de la chaîne seront utilisés.  
  
 Pour les valeurs entières, *précision* correspond au nombre minimal de chiffres imprimés.  
  
 Un astérisque (*) signifie que la précision est spécifiée par l'argument associé dans la liste, qui doit être un nombre entier.  
  
 {h | l} *type*  
  
 Est utilisé avec les types de caractères d, i, o, s, x, X ou u et crée **shortint** (h) ou **longint** des valeurs (l).  
  
|Spécification de type|Représente|  
|------------------------|----------------|  
|d ou i|Entier signé|  
|o|Octal non signé|  
|s|Chaîne|  
|u|Entier non signé|  
|x ou X|Hexadécimal non signé|  
  
> [!NOTE]  
>  Ces spécifications de type sont basées sur celles initialement définies pour le **printf** fonction dans la bibliothèque standard C. Les spécifications de type utilisées dans le mappage de chaînes de message RAISERROR pour [!INCLUDE[tsql](../../includes/tsql-md.md)] des types de données, tandis que les spécifications utilisées dans **printf** mappés aux types de données du langage C. Spécifications de type utilisées dans **printf** ne sont pas pris en charge par RAISERROR lorsque [!INCLUDE[tsql](../../includes/tsql-md.md)] n’est pas un type de données semblable au type de données C associé. Par exemple, le *%p* spécification pour les pointeurs n’est pas prise en charge dans RAISERROR car [!INCLUDE[tsql](../../includes/tsql-md.md)] n’est pas un type de données de pointeur.  
  
> [!NOTE]  
>  Pour convertir une valeur pour le [!INCLUDE[tsql](../../includes/tsql-md.md)] **bigint** de type de données, spécifiez **% I64d**.  
  
 **@** *local_variable*  
 Est une variable de tout type de données de caractères valide qui contient une chaîne mise en forme de la même manière que *chaîne_du_message*. **@*** local_variable* doit être **char** ou **varchar**, ou doit pouvoir être converti implicitement à ces types de données.  
  
 *severity*  
 Représente le niveau de gravité défini par l'utilisateur associé au message en question. Lorsque vous utilisez *msg_id* pour déclencher un message défini par l’utilisateur créé à l’aide de sp_addmessage, la gravité spécifiée dans l’instruction RAISERROR remplace celui spécifié dans sp_addmessage.  
  
 Les niveaux de gravité de 0 à 18 peuvent être spécifiés par tout utilisateur. Niveaux de gravité de 19 à 25 peuvent uniquement être spécifiés par les membres du rôle sysadmin du rôle serveur fixé ou les utilisateurs avec des autorisations ALTER TRACE. Pour les niveaux de 19 à 25, l'option WITH LOG est nécessaire. Les niveaux de gravité inférieurs à 0 sont interprétés comme 0. Les niveaux de gravité supérieurs à 25 sont interprétés comme 25.  
  
> [!CAUTION]  
>  Les erreurs ayant un niveau compris entre 20 et 25 sont considérées comme irrécupérables. Si une erreur de cette gravité se produit, la connexion cliente prend fin après réception du message, et l'erreur est consignée dans le journal des erreurs ainsi que dans le journal des applications.  
  
 Vous pouvez spécifier -1 pour retourner la valeur de gravité associée à l'erreur, comme le montre l'exemple suivant.  
  
```  
RAISERROR (15600,-1,-1, 'mysp_CreateCustomer');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Msg 15600, Level 15, State 1, Line 1   
 An invalid parameter or option was specified for procedure 'mysp_CreateCustomer'.
 ```  
  
 *state*  
 Entier compris entre 0 et 255. Les valeurs négatives par défaut est 1. Valeurs supérieures à 255 ne doivent pas être utilisés. 
  
 Si une même erreur définie par l'utilisateur est générée à plusieurs emplacements, l'utilisation d'un numéro d'état unique pour chaque emplacement peut vous aider à trouver la portion de code à l'origine des erreurs.  
  
 *argument*  
 Les paramètres de substitution utilisés pour les variables définies dans *chaîne_du_message* ou le message correspondant à *msg_id*. Il peut y avoir 0 ou plusieurs paramètres de substitution ; leur nombre total ne peut toutefois pas excéder 20. Chaque paramètre de substitution peut être une variable locale ou un de ces types de données : **tinyint**, **smallint**, **int**, **char**, **varchar**, **nchar**, **nvarchar**, **binaire**, ou **varbinary**. Aucun autre type de données n'est reconnu.  
  
 *option*  
 Option personnalisée pour l'erreur. Peut prendre l'une des valeurs mentionnées dans le tableau ci-après.  
  
|Valeur| Description|  
|-----------|-----------------|  
|LOG|Consigne l’erreur dans le journal des erreurs et le journal des applications pour l’instance de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Les erreurs inscrites dans le journal des erreurs sont actuellement limitées à 440 octets. Seul un membre du rôle serveur fixe sysadmin ou un utilisateur avec des autorisations ALTER TRACE peut spécifier WITH LOG.<br /><br /> [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|  
|NOWAIT|Envoie des messages immédiatement au client.<br /><br /> [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|  
|SETERROR|Définit le @@ERROR et valeurs ERROR_NUMBER *msg_id* ou 50 000, quel que soit le niveau de gravité.<br /><br /> [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|  
  
## <a name="remarks"></a>Notes  
 Les erreurs générées par RAISERROR fonctionnent comme des erreurs générées par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] code. Les valeurs spécifiées par RAISERROR sont signalées par les fonctions ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, ERROR_STATE et @@ERROR fonctions système. Lorsque l'instruction RAISERROR est exécutée avec un niveau de gravité de minimum 11 dans un bloc TRY, elle transfère le contrôle au bloc CATCH associé. L'erreur est renvoyée à l'appelant si RAISERROR est exécutée :  
  
-   en dehors du champ d'un bloc TRY ;  
  
-   avec un niveau de gravité inférieur ou égal à 10 dans un bloc TRY ;  
  
-   avec un degré de gravité supérieur ou égal à 20 qui met fin à la connexion à la base de données.  
  
 Les blocs CATCH peuvent utiliser RAISERROR pour relancer l'erreur qui a appelé le bloc CATCH à l'aide de fonctions système, telles que ERROR_NUMBER et ERROR_MESSAGE, afin de récupérer les données d'erreur originales. @@ERROR est définie sur 0 par défaut pour les messages avec un niveau de gravité compris entre 1 et 10.  
  
 Lorsque *msg_id* spécifie un message défini par l’utilisateur disponible à partir de la vue de catalogue sys.messages, processus RAISERROR le message à partir de la colonne de texte utilisant les mêmes règles que celles appliquées au texte d’un message défini par l’utilisateur spécifié à l’aide de *chaîne_du_message*. Le texte du message défini par l'utilisateur peut contenir des spécifications de conversion, dans lesquelles RAISERROR mappera les arguments. Utilisez sp_addmessage pour ajouter des messages d’erreur définis par l’utilisateur et sp_dropmessage pour supprimer les messages d’erreur définis par l’utilisateur.  
  
 Vous pouvez également utiliser RAISERROR comme alternative à PRINT pour renvoyer des messages aux applications appelantes. RAISERROR prend en charge la substitution de caractères, semblable à la fonctionnalité de la **printf** fonction dans la bibliothèque standard C, tandis que le [!INCLUDE[tsql](../../includes/tsql-md.md)] n’est pas le cas de l’instruction PRINT. L'instruction PRINT n'est pas affectée par les blocs TRY, alors que si vous exécutez RAISERROR avec un degré de gravité compris entre 11 et 19 dans un bloc TRY, le contrôle est transféré vers le bloc CATCH associé. Spécifiez une gravité inférieure ou égale à 10 pour utiliser RAISERROR afin de renvoyer un message depuis un bloc TRY sans appeler le bloc CATCH.  
  
 En règle générale, des arguments successifs remplacent des spécifications de conversion successives ; le premier argument remplace la première spécification de conversion, le deuxième argument remplace la deuxième spécification, etc. Par exemple, dans l'instruction `RAISERROR` suivante, le premier argument `N'number'` remplace la première spécification de conversion `%s` et le deuxième argument `5` remplace la deuxième spécification de conversion `%d.`  
  
```  
RAISERROR (N'This is message %s %d.', -- Message text.  
           10, -- Severity,  
           1, -- State,  
           N'number', -- First argument.  
           5); -- Second argument.  
-- The message text returned is: This is message number 5.  
GO  
```  
  
 Si un astérisque (*) est spécifié pour la largeur ou la précision d'une spécification de conversion, la valeur à utiliser pour la largeur ou la précision est un nombre entier. Dans ce cas, une spécification de conversion peut utiliser jusqu'à trois arguments : un pour la largeur, un pour la précision et un pour la valeur de substitution.  
  
 Par exemple, les deux instructions `RAISERROR` suivantes renvoient la même chaîne. L'une spécifie la largeur et la précision dans la liste d'arguments, tandis que l'autre les indique dans la spécification de conversion.  
  
```  
RAISERROR (N'<\<%*.*s>>', -- Message text.  
           10, -- Severity,  
           1, -- State,  
           7, -- First argument used for width.  
           3, -- Second argument used for precision.  
           N'abcde'); -- Third argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
RAISERROR (N'<\<%7.3s>>', -- Message text.  
           10, -- Severity,  
           1, -- State,  
           N'abcde'); -- First argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
```  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-error-information-from-a-catch-block"></a>A. Renvoi d'informations d'erreur depuis un bloc CATCH  
 L'exemple de code ci-dessous indique comment utiliser `RAISERROR` à l'intérieur d'un bloc `TRY` pour que l'exécution passe au bloc `CATCH` associé. Il explique également comment utiliser `RAISERROR` pour retourner des informations sur l'erreur qui a appelé le bloc `CATCH`.  
  
> [!NOTE]  
>  RAISERROR génère uniquement des erreurs dont l'état est exclusivement compris entre 1 et 127. Étant donné que la [!INCLUDE[ssDE](../../includes/ssde-md.md)] peut déclencher des erreurs dont l’état 0, nous vous recommandons de vérifier l’état d’erreur retourné par ERROR_STATE avant de le transmettre en tant que valeur de paramètre d’état de RAISERROR.  
  
```  
BEGIN TRY  
    -- RAISERROR with severity 11-19 will cause execution to   
    -- jump to the CATCH block.  
    RAISERROR ('Error raised in TRY block.', -- Message text.  
               16, -- Severity.  
               1 -- State.  
               );  
END TRY  
BEGIN CATCH  
    DECLARE @ErrorMessage NVARCHAR(4000);  
    DECLARE @ErrorSeverity INT;  
    DECLARE @ErrorState INT;  
  
    SELECT   
        @ErrorMessage = ERROR_MESSAGE(),  
        @ErrorSeverity = ERROR_SEVERITY(),  
        @ErrorState = ERROR_STATE();  
  
    -- Use RAISERROR inside the CATCH block to return error  
    -- information about the original error that caused  
    -- execution to jump to the CATCH block.  
    RAISERROR (@ErrorMessage, -- Message text.  
               @ErrorSeverity, -- Severity.  
               @ErrorState -- State.  
               );  
END CATCH;  
```  
  
### <a name="b-creating-an-ad-hoc-message-in-sysmessages"></a>B. Création d'un message approprié dans sys.messages  
 L’exemple suivant montre comment générer un message stocké dans la vue de catalogue sys.messages. Le message a été ajouté à la vue de catalogue sys.messages à l’aide de la `sp_addmessage` système des procédure stockée en tant que message numéro `50005`.  
  
```  
sp_addmessage @msgnum = 50005,  
              @severity = 10,  
              @msgtext = N'<\<%7.3s>>';  
GO  
RAISERROR (50005, -- Message id.  
           10, -- Severity,  
           1, -- State,  
           N'abcde'); -- First argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
sp_dropmessage @msgnum = 50005;  
GO  
```  
  
### <a name="c-using-a-local-variable-to-supply-the-message-text"></a>C. Utilisation d'une variable locale pour fournir un texte de message  
 L'exemple de code ci-après montre comment utiliser une variable locale pour fournir un texte de message pour une instruction `RAISERROR`.  
  
```  
DECLARE @StringVariable NVARCHAR(50);  
SET @StringVariable = N'<\<%7.3s>>';  
  
RAISERROR (@StringVariable, -- Message text.  
           10, -- Severity,  
           1, -- State,  
           N'abcde'); -- First argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [PRINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/print-transact-sql.md)   
 [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_dropmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [xp_logevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-logevent-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40; Transact-SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)  
  
  

