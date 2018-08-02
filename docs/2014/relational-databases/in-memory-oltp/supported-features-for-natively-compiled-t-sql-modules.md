---
title: Prise en charge des constructions dans les procédures stockées compilées en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91434af003bdf783ee4f2bd2c946e4a871eac44d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240850"
---
# <a name="supported-constructs-in-natively-compiled-stored-procedures"></a>Constructions prises en charge dans les procédures stockées compilées en mode natif
  Cette rubrique contient une liste des fonctionnalités prises en charge pour les procédures stockées compilées en mode natif ([CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)) :  
  
-   [Programmabilité dans les procédures stockées compilées en mode natif](#pncsp)  
  
-   [Opérateurs pris en charge](#so)  
  
-   [Fonctions intégrées dans les procédures stockées compilées en mode natif](#bfncsp)  
  
-   [La surface d’exposition de requête dans les procédures stockées compilées en mode natif](#qsancsp)  
  
-   [Audit](#auditing)  
  
-   [Table, requête et les indicateurs de jointure](#tqh)  
  
-   [Limitations sur le tri](#los)  
  
 Pour plus d’informations sur les types de données pris en charge en mode natif dans les procédures stockées compilées, consultez [pris en charge les Types de données](supported-data-types-for-in-memory-oltp.md).  
  
 Pour plus d’informations sur les constructions non prises en charge et pour plus d’informations sur la façon de contourner certaines des fonctionnalités non prises en charge dans les procédures stockées compilées en mode natif, consultez [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md). Pour plus d’informations sur les fonctionnalités non prises en charge, consultez [Les constructions Transact-SQL ne sont pas prises en charge par l’OLTP en mémoire](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
##  <a name="pncsp"></a> Programmabilité dans les procédures stockées compilées en mode natif  
 Les constructions suivantes sont admises :  
  
-   BEGIN ATOMIC (au niveau externe de la procédure stockée), LANGUAGE, ISOLATION LEVEL, DATEFORMAT et DATEFIRST  
  
-   Variables déclarantes comme NULL ou NOT NULL Si une variable est déclarée NOT NULL, la déclaration doit avoir un initialiseur. Si une variable n'est pas déclarée NOT NULL, l'initialiseur est facultatif.  
  
-   IF et WHILE  
  
-   INSERT/UPDATE/DELETE  
  
     Les sous-requêtes ne sont pas prises en charge. Dans la clause WHERE ou HAVING, AND et BETWEEN sont pris en charge ; OR, NOT et IN ne sont pas pris en charge.  
  
-   Types de tables optimisées en mémoire et variables de table.  
  
-   RETURN  
  
-   SELECT  
  
-   SET  
  
-   TRY/CATCH/THROW  
  
     Pour optimiser les performances, utilisez un bloc TRY/CATCH pour une procédure stockée compilée en mode natif entière.  
  
##  <a name="so"></a> Opérateurs pris en charge  
 Les opérateurs suivants sont pris en charge :  
  
-   [Opérateurs de comparaison &#40;Transact-SQL&#41; ](/sql/t-sql/language-elements/comparison-operators-transact-sql) (par exemple, >, \<, > =, et < =) sont pris en charge dans des instructions conditionnelles (IF, tandis que).  
  
-   Opérateurs unaires (+, -).  
  
-   Opérateurs binaires (*, /, +, -, % (modulo)).  
  
     L'opérateur plus (+) est pris en charge pour les nombres et les chaînes.  
  
-   Opérateurs logiques (AND, OR, NOT). OR et NOT sont pris en charge dans les instructions IF et WHILE mais pas dans les clauses WHERE ou HAVING.  
  
-   Opérateurs au niveau du bit ~, &, |, et ^  
  
##  <a name="bfncsp"></a> Fonctions intégrées dans les procédures stockées compilées en mode natif  
 Les fonctions suivantes sont prises en charge dans les contraintes par défaut sur les tables optimisées en mémoire et dans les procédures stockées compilées en mode natif.  
  
-   Fonctions mathématiques : ACOS, ASIN, ATAN, ATN2, COS, COT, DEGREES, EXP, LOG, LOG10, PI, POWER, RADIANS, RAND, SIN, SQRT, SQUARE et TAN  
  
-   Fonctions de date : CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME et YEAR.  
  
-   Fonctions de chaîne : LEN, LTRIM, RTRIM et SUBSTRING  
  
-   Fonction d'identité : SCOPE_IDENTITY  
  
-   Fonctions NULL : ISNULL  
  
-   Fonctions Uniqueidentifier : NEWID et NEWSEQUENTIALID  
  
-   Fonctions d'erreur : ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY et ERROR_STATE  
  
-   Conversions : CAST et CONVERT. Les conversions entre des chaînes de caractères Unicode et non-Unicode (n(var)char et (var)char) ne sont pas prises en charge.  
  
-   Fonctions système : @@rowcount. Les instructions dans les procédures stockées compilées en mode natif mettent à jour @@rowcount et vous pouvez utiliser @@rowcount dans une procédure stockée compilée en mode natif pour déterminer le nombre de lignes affectées par la dernière instruction exécutée dans cette procédure stockée compilée en mode natif. Cependant, @@rowcount est réinitialisé à 0 au début et à la fin de l’exécution d’une procédure stockée compilée en mode natif.  
  
##  <a name="qsancsp"></a> La surface d’exposition de requête dans les procédures stockées compilées en mode natif  
 Les constructions suivantes sont admises :  
  
-   BETWEEN  
  
-   Alias de noms de colonnes (en utilisant la syntaxe AS ou =).  
  
-   CROSS JOIN et INNER JOIN sont uniquement prises en charge avec les requêtes SELECT.  
  
-   Les expressions sont pris en charge dans la liste de sélection et [où &#40;Transact-SQL&#41; ](/sql/t-sql/queries/where-transact-sql) clause s’ils utilisent un opérateur pris en charge. Voir [Opérateurs pris en charge](#so) pour obtenir la liste des opérateurs actuellement pris en charge.  
  
-   Prédicat de filtre IS [NOT] NULL  
  
-   À partir de \<table optimisée en mémoire >  
  
-   [GROUP BY &#40;Transact-SQL&#41; ](/sql/t-sql/queries/select-group-by-transact-sql) est pris en charge, ainsi que les fonctions d’agrégation AVG, COUNT, COUNT_BIG, MIN, MAX et SUM. MIN et MAX ne sont pas pris en charge pour les types nvarchar, char, varchar, varchar, varbinary, et binary. [Clause ORDER BY &#40;Transact-SQL&#41; ](/sql/t-sql/queries/select-order-by-clause-transact-sql) est pris en charge avec [GROUP BY &#40;Transact-SQL&#41; ](/sql/t-sql/queries/select-group-by-transact-sql) si une expression dans la liste ORDER BY apparaît de façon textuelle dans la liste GROUP BY. Par exemple, GROUP BY a + b ORDER BY a + b est pris en charge, mais GROUP BY a, b ORDER BY a + b n'est pas pris en charge.  
  
-   HAVING, assujetti aux mêmes limitations d'expression que la clause WHERE  
  
-   INSERT VALUES (une ligne par instruction) et INSERT SELECT  
  
-   ORDER BY <sup>1</sup>  
  
-   Prédicats qui ne référencent pas de colonne.  
  
-   SELECT, UPDATE et DELETE  
  
-   HAUT <sup>1</sup>  
  
-   Affectation de variable dans la liste SELECT.  
  
-   WHERE … AND  
  
 <sup>1</sup> ORDER BY et TOP sont pris en charge dans les procédures stockées compilées en mode natif, avec quelques restrictions :  
  
-   Il n’existe aucune prise en charge pour `DISTINCT` dans le `SELECT` ou `ORDER BY` clause.  
  
-   Il n'existe aucune prise en charge de `WITH TIES` ou `PERCENT` dans la clause `TOP`.  
  
-   `TOP` combiné avec `ORDER BY` ne prend pas en charge plus de 8 192 lors de l’utilisation d’une constante dans le `TOP` clause. Cette limite peut être abaissée lorsque la requête contient des jointures ou des fonctions d'agrégation. Par exemple, avec une jointure (entre deux tables), la limite est de 4 096 lignes. Avec deux jointures (entre trois tables), la limite est de 2 730 lignes.  
  
     Vous pouvez obtenir plus de 8 192 résultats en stockant le nombre de lignes dans une variable :  
  
    ```tsql  
    DECLARE @v INT = 9000  
    SELECT TOP (@v) … FROM … ORDER BY …  
    ```  
  
 Cependant, l'utilisation d'une constante dans la clause `TOP` donne de meilleurs résultats qu'une variable.  
  
 Ces restrictions ne s’appliquent pas interprété [!INCLUDE[tsql](../../includes/tsql-md.md)] accès sur les tables optimisées en mémoire.  
  
##  <a name="auditing"></a> Audit  
 L'audit au niveau de la procédure est pris en charge dans les procédures stockées compilées en mode natif. L'audit au niveau de l'instruction n'est pas pris en charge.  
  
 Pour plus d'informations sur l'audit, consultez [Créer une spécification de l'audit du serveur et de la base de données](../security/auditing/create-a-server-audit-and-database-audit-specification.md).  
  
##  <a name="tqh"></a> Table, requête et les indicateurs de jointure  
 Les constructions suivantes sont admises :  
  
-   Indicateurs INDEX, FORCESCAN et FORCESEEK, dans la syntaxe des indicateurs de table ou dans la [Clause OPTION &#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql) de la requête.  
  
-   FORCE ORDER  
  
-   INNER LOOP JOIN  
  
-   OPTIMIZE FOR  
  
 Pour plus d’informations, consultez [indicateurs &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql).  
  
##  <a name="los"></a> Limitations sur le tri  
 Vous pouvez trier plus de 8000 lignes dans une requête qui utilise [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) et une [Clause ORDER BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql). Toutefois, sans [Clause ORDER BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) peut trier jusqu’à 8000 lignes (moins s’il existe des jointures).  
  
 Si votre requête utilise à la fois l’opérateur [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) et une [Clause ORDER BY&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql), vous pouvez spécifier jusqu’à 8192 lignes pour l’opérateur TOP. Si vous spécifiez plus de 8 192 lignes, le message d’erreur suivant s’affiche : **Message 41398, Niveau 16, État 1, Procédure *\<nom_procédure>*, Ligne *\<numéro_ligne>* L’opérateur TOP peut retourner au maximum 8 192 lignes ; *\<nombre* demandé.**  
  
 Si vous n'avez pas de clause TOP, triez les lignes avec ORDER BY.  
  
 Si vous n'utilisez pas de clause ORDER BY, utilisez une valeur entière avec l'opérateur TOP.  
  
 Exemple avec TOP N = 8192 : Compiles  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 Exemple avec TOP N > 8192 : Fails to compile.  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 La limitation de 8192 lignes s'applique uniquement à `TOP N` où `N` est une constante, comme dans les exemples précédents.  Si `N` doit être supérieur à 8192, vous pouvez affecter la valeur à une variable et utiliser cette variable avec `TOP`.  
  
 Exemple à l'aide d'une variable : Compiles  
  
```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 **Limitations sur les lignes retournées :** il existe deux cas de figure qui peuvent potentiellement réduire le nombre de lignes retournées par l'opérateur TOP :  
  
-   L'utilisation de JOINs dans la requête.  L'impact de JOINs sur une limitation dépend du plan de requête.  
  
-   L'utilisation de fonctions d'agrégation ou de références à des fonctions d'agrégation dans la clause ORDER BY.  
  
 La formule pour calculer la valeur maximale N prise en charge dans le pire des cas dans TOP est : `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)   
 [Problèmes de migration pour les procédures stockées compilées en mode natif](migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
