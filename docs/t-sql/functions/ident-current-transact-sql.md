---
title: IDENT_CURRENT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IDENT_CURRENT
- IDENT_CURRENT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- last identity value generated for table
- identity values [SQL Server], last generated
- identity columns, current value
- IDENT_CURRENT function
ms.assetid: 21517ced-39f5-4cd8-8d9c-0a0b8aff554a
caps.latest.revision: 49
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4b3563392c1df2b6056904f932b0fa2c5eaa3db3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="identcurrent-transact-sql"></a>IDENT_CURRENT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la dernière valeur d'identité générée pour une table ou une vue spécifiée. La dernière valeur d'identité générée peut être pour toute session et toute étendue.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IDENT_CURRENT( 'table_name' )  
```  
  
## <a name="arguments"></a>Arguments  
 *table_name*  
 Nom de la table dont la valeur d'identité est retournée. *nom_table* est **varchar**, sans valeur par défaut.  
  
## <a name="return-types"></a>Types de retour  
 **NUMERIC(38,0)**  
  
## <a name="exceptions"></a>Exceptions  
 Retourne la valeur NULL en cas d'erreur ou si un appelant n'est pas autorisé à afficher l'objet.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un utilisateur peut voir uniquement les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d'un droit d'accès. Cela signifie que les fonctions intégrées générant des métadonnées, telles que IDENT_CURRENT, peuvent retourner la valeur NULL si l'utilisateur ne dispose d'aucune autorisation sur l'objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Notes  
 IDENT_CURRENT est similaire à la [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] fonctions d’identité SCOPE_IDENTITY et @@IDENTITY. Ces trois fonctions renvoient les dernières valeurs d'identité générées. Toutefois, la portée et la session sur laquelle *dernière* est défini dans chacune de ces fonctions sont différents :  
  
-   IDENT_CURRENT renvoie la dernière valeur d'identité générée pour une table spécifique dans n'importe quelles session et étendue.  
  
-   @@IDENTITY renvoie la dernière valeur d’identité générée pour n’importe quelle table dans la session active, sur toutes les étendues.  
  
-   SCOPE_IDENTITY renvoie la dernière valeur d'identité générée pour n'importe quelle table dans la session et l'étendue en cours.  
  
 Lorsque la valeur IDENT_CURRENT est NULL (si la table n'a jamais contenu de ligne ou a été tronquée), la fonction IDENT_CURRENT retourne la valeur de départ.  
  
 Les instructions et les transactions en échec peuvent modifier l'identité actuelle d'une table et créer des trous dans les valeurs des colonnes d'identité. La valeur d'identité n'est jamais annulée, même si la transaction qui a essayé d'insérer la valeur dans la table n'est pas validée. Par exemple, si une instruction INSERT échoue à cause d'une violation d'identité IGNORE_DUP_KEY, la valeur d'identité actuelle de la table augmente quand même d'une unité.  
  
 Soyez prudent lorsque vous utilisez IDENT_CURRENT pour prévoir la valeur d'identité générée suivante. La valeur effectivement générée peut être différente de la somme des valeurs IDENT_CURRENT et IDENT_INCR si d'autres sessions effectuent des insertions.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-the-last-identity-value-generated-for-a-specified-table"></a>A. Renvoi de la dernière valeur d'identité générée pour une table spécifiée  
 L'exemple suivant renvoie la dernière valeur d'identité générée pour la table `Person.Address` de la base de données `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENT_CURRENT ('Person.Address') AS Current_Identity;  
GO  
```  
  
### <a name="b-comparing-identity-values-returned-by-identcurrent-identity-and-scopeidentity"></a>B. Comparaison des valeurs d’identité retournée par IDENT_CURRENT, @@IDENTITY et SCOPE_IDENTITY  
 L'exemple suivant affiche les valeurs d'identité différentes renvoyées par `IDENT_CURRENT`, `@@IDENTITY` et `SCOPE_IDENTITY`.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N't6', N'U') IS NOT NULL   
    DROP TABLE t6;  
GO  
IF OBJECT_ID(N't7', N'U') IS NOT NULL   
    DROP TABLE t7;  
GO  
CREATE TABLE t6(id int IDENTITY);  
CREATE TABLE t7(id int IDENTITY(100,1));  
GO  
CREATE TRIGGER t6ins ON t6 FOR INSERT   
AS  
BEGIN  
   INSERT t7 DEFAULT VALUES  
END;  
GO  
--End of trigger definition  
  
SELECT id FROM t6;  
--IDs empty.  
  
SELECT id FROM t7;  
--ID is empty.  
  
--Do the following in Session 1  
INSERT t6 DEFAULT VALUES;  
SELECT @@IDENTITY;  
/*Returns the value 100. This was inserted by the trigger.*/  
  
SELECT SCOPE_IDENTITY();  
/* Returns the value 1. This was inserted by the   
INSERT statement two statements before this query.*/  
  
SELECT IDENT_CURRENT('t7');  
/* Returns value inserted into t7, that is in the trigger.*/  
  
SELECT IDENT_CURRENT('t6');  
/* Returns value inserted into t6. This was the INSERT statement four statements before this query.*/  
  
-- Do the following in Session 2.  
SELECT @@IDENTITY;  
/* Returns NULL because there has been no INSERT action   
up to this point in this session.*/  
  
SELECT SCOPE_IDENTITY();  
/* Returns NULL because there has been no INSERT action   
up to this point in this scope in this session.*/  
  
SELECT IDENT_CURRENT('t7');  
/* Returns the last value inserted into t7.*/  
```  
  
## <a name="see-also"></a>Voir aussi  
 [@@IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/identity-transact-sql.md)   
 [SCOPE_IDENTITY &#40; Transact-SQL &#41;](../../t-sql/functions/scope-identity-transact-sql.md)   
 [IDENT_INCR &#40; Transact-SQL &#41;](../../t-sql/functions/ident-incr-transact-sql.md)   
 [IDENT_SEED &#40; Transact-SQL &#41;](../../t-sql/functions/ident-seed-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Fonctions système &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

