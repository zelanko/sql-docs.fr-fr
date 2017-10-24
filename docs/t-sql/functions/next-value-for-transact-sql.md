---
title: La valeur suivante pour (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/19/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEXT_VALUE_TSQL
- NEXT
- NEXT VALUE
- NEXT VALUE FOR
- NEXT_TSQL
- NEXT_VALUE_FOR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NEXT VALUE FOR function
- sequence number object, NEXT VALUE FOR function
ms.assetid: 92632ed5-9f32-48eb-be28-a5e477ef9076
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aab8020fa04b978d7ec1b657fe0a1084123dfb48
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="next-value-for-transact-sql"></a>NEXT VALUE FOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Génère un numéro séquentiel de l'objet séquence spécifié.  
  
 Pour obtenir une description complète de la création et l’utilisation de séquences, consultez [numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md). Utilisez [sp_sequence_get_range](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md) pour générer réserver une plage de numéros de séquence.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
NEXT VALUE FOR [ database_name . ] [ schema_name . ]  sequence_name  
   [ OVER (<over_order_by_clause>) ]  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Nom de la base de données qui contient l'objet séquence.  
  
 *schema_name*  
 Nom du schéma qui contient l'objet séquence.  
  
 *sequence_name*  
 Nom de l'objet séquence qui génère le nombre.  
  
 *over_order_by_clause*  
 Détermine l'ordre dans lequel la valeur de séquence est affectée aux lignes d'une partition. Pour plus d’informations, consultez [la Clause OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Types de retour  
 Retourne un nombre à l'aide du type de la séquence.  
  
## <a name="remarks"></a>Notes  
 Le **NEXT VALUE FOR** fonction peut être utilisée dans les procédures stockées et les déclencheurs.  
  
 Lorsque le **NEXT VALUE FOR** fonction est utilisée dans une contrainte de requête ou de la valeur par défaut, si le même objet séquence est utilisé plusieurs fois, ou si le même objet séquence est utilisé à la fois dans l’instruction qui fournit les valeurs et dans une contrainte par défaut en cours d’exécution, la même valeur s’affichera pour toutes les colonnes qui référencent la même séquence dans une ligne dans le jeu de résultats.  
  
 Le **NEXT VALUE FOR** fonction est non déterministe et est autorisée uniquement dans les contextes où le nombre de valeurs de séquence générées est bien défini. Vous trouverez ci-dessous la définition du nombre de valeurs qui sera utilisé pour chaque objet séquence référencé dans une instruction donnée :  
  
-   **Sélectionnez** -pour chaque objet séquence référencé, une nouvelle valeur est générée une fois par ligne dans le résultat de l’instruction.  
  
-   **INSÉRER** ... **VALEURS** -pour chaque objet séquence référencé, une nouvelle valeur est générée une fois pour chaque ligne insérée dans l’instruction.  
  
-   **Mise à jour** -pour chaque objet séquence référencé, une nouvelle valeur est générée pour chaque ligne mise à jour par l’instruction.  
  
-   Instructions de procédure (tels que **DECLARE**, **définir**, etc.)-pour chaque objet séquence référencé, une nouvelle valeur est générée pour chaque instruction.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 Le **NEXT VALUE FOR** fonction ne peut pas être utilisée dans les situations suivantes :  
  
-   Lorsqu'une base de données est en mode en lecture seule.  
  
-   Comme argument à une fonction table.  
  
-   Comme argument à une fonction d'agrégation.  
  
-   Dans les sous-requêtes, notamment les expressions de table communes et les tables dérivées.  
  
-   Dans les vues, dans les fonctions définies par l'utilisateur ou dans les colonnes calculées.  
  
-   Dans une instruction qui utilise le **DISTINCT**, **UNION**, **UNION ALL**, **EXCEPT** ou **INTERSECT** opérateur.  
  
-   Dans une instruction qui utilise le **ORDER BY** clause, sauf si **NEXT VALUE FOR** ... **SUR** (**ORDER BY** ...) est utilisé.  
  
-   Dans les clauses suivantes : **FETCH**, **sur**, **sortie**, **ON**, **PIVOT**, **UNPIVOT**, **GROUP BY**, **HAVING**, **de calcul**, **COMPUTE BY**, ou **FOR XML**.  
  
-   Dans les expressions conditionnelles à l’aide de **cas**, **choisir**, **COALESCE**, **IIF**, **ISNULL**, ou **NULLIF**.  
  
-   Dans un **valeurs** clause n’est pas dans le cadre d’un **insérer** instruction.  
  
-   Dans la définition d'une contrainte de validation.  
  
-   Dans la définition d'une règle ou d'un objet par défaut. (Il peut être utilisé dans une contrainte par défaut.)  
  
-   Comme valeur par défaut dans un type de table défini par l'utilisateur.  
  
-   Dans une instruction qui utilise **haut**, **décalage**, ou lorsque le **ROWCOUNT** option est définie.  
  
-   Dans le **où** clause d’une instruction.  
  
-   Dans un **fusion** instruction. (Sauf lorsque le **NEXT VALUE FOR** fonction est utilisée dans une contrainte par défaut dans la table cible et la valeur par défaut est utilisée dans les **créer** instruction de la **fusion** instruction.)  
  
## <a name="using-a-sequence-object-in-a-default-constraint"></a>Utilisation d'un objet séquence dans une contrainte par défaut  
 Lorsque vous utilisez la **NEXT VALUE FOR** fonction dans une contrainte par défaut, les règles suivantes s’appliquent :  
  
-   Un objet séquence unique peut être référencé à partir de contraintes par défaut dans plusieurs tables.  
  
-   La table et l'objet séquence doivent résider dans la même base de données.  
  
-   L'utilisateur qui ajoute la contrainte par défaut doit avoir l'autorisation REFERENCES sur l'objet séquence.  
  
-   Un objet séquence référencé à partir d'une contrainte par défaut ne peut pas être supprimé avant la suppression de la contrainte par défaut.  
  
-   Le même numéro séquentiel est retourné pour toutes les colonnes dans une ligne si plusieurs contraintes par défaut utilisent le même objet séquence, ou si le même objet séquence est utilisé à la fois dans l'instruction qui fournit les valeurs et dans une contrainte par défaut en cours d'exécution.  
  
-   Les références à la **NEXT VALUE FOR** fonction dans une contrainte par défaut ne peut pas spécifier le **sur** clause.  
  
-   Un objet séquence référencé dans une contrainte par défaut peut être modifié.  
  
-   Dans le cas d’un `INSERT … SELECT` ou `INSERT … EXEC` instruction où les données insérées provient d’une requête à l’aide un **ORDER BY** clause, les valeurs qui sont retournées par la **NEXT VALUE FOR** fonction sera générée dans l’ordre spécifié par le **ORDER BY** clause.  
  
## <a name="using-a-sequence-object-with-an-over-order-by-clause"></a>Utilisation d'un objet séquence avec une clause OVER ORDER BY  
 Le **NEXT VALUE FOR** fonction prend en charge la génération de valeurs de séquence triées en appliquant la **sur** clause pour le **NEXT VALUE FOR** appeler. À l’aide de la **sur** clause, un utilisateur est assuré que les valeurs qui sont retournées sont générées dans l’ordre de la **sur** de clause **B de la commande**sous-clause. Les règles supplémentaires suivantes s’appliquent lorsque vous utilisez la **NEXT VALUE FOR** fonctionne avec le **sur** clause :  
  
-   Appels multiples à la **NEXT VALUE FOR** fonctionnera pour le même Générateur de séquence dans une instruction unique doit tous utiliser la même **sur** définition de la clause.  
  
-   Appels multiples à la **NEXT VALUE FOR** fonction que référence différents générateurs de séquence dans une instruction unique peuvent avoir différents **sur** définitions de clause.  
  
-   Un **sur** clause appliquée à la **NEXT VALUE FOR** (fonction) ne prend pas en charge la **PARTITION BY** sous-clause.  
  
-   Si tous les appels à la **NEXT VALUE FOR** fonctionner dans un **sélectionnez** instruction spécifie la **sur** clause, une **ORDER BY** clause peut être utilisée dans les **sélectionnez** instruction.  
  
-   Le **sur** clause est autorisée avec la **NEXT VALUE FOR** fonctionne lorsqu’il est utilisé dans un **sélectionnez** instruction ou `INSERT … SELECT …` instruction. Utilisation de la **sur** clause avec la **NEXT VALUE FOR** fonction n’est pas autorisée dans **mise à jour** ou **fusion** instructions.  
  
-   Si un autre processus accède simultanément à l'objet séquence, les nombres retournés peuvent comporter des espaces vides.  
  
## <a name="metadata"></a>Métadonnées  
 Pour plus d’informations sur les séquences, interrogez la [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md) affichage catalogue.  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 Requiert **mise à jour** l’autorisation sur l’objet séquence ou le schéma de la séquence. Pour obtenir un exemple d'octroi d'une autorisation, consultez l'exemple F dans la suite de cette rubrique.  
  
### <a name="ownership-chaining"></a>Chaînage des propriétés  
 Les objets séquences prennent en charge le chaînage des propriétés. Si l'objet séquence a le même propriétaire que la procédure stockée appelante, le déclencheur ou la table (ayant un objet séquence comme contrainte par défaut), aucun contrôle d'autorisation n'est obligatoire sur l'objet séquence. Si l'objet séquence n'est pas détenu par le même utilisateur que la procédure stockée appelante, le déclencheur ou la table, un contrôle d'autorisation est obligatoire sur l'objet séquence.  
  
 Lorsque le **NEXT VALUE FOR** fonction est utilisée comme valeur par défaut dans une table, les utilisateurs nécessitent deux **insérer** autorisation sur la table, et **mise à jour** autorisation sur l’objet de séquence, d’insérer des données à l’aide de la valeur par défaut.  
  
-   Si la contrainte par défaut a le même propriétaire que l'objet séquence, aucune autorisation n'est obligatoire sur l'objet séquence lorsque la contrainte par défaut est appelée.  
  
-   Si la contrainte par défaut et l'objet séquence ne sont pas détenus par le même utilisateur, des autorisations sont requises sur l'objet séquence même s'il est appelé via la contrainte par défaut.  
  
### <a name="audit"></a>Audit  
 Pour auditer les **NEXT VALUE FOR** fonctionner, surveillez SCHEMA_OBJECT_ACCESS_GROUP.  
  
## <a name="examples"></a>Exemples  
 Pour obtenir des exemples de création de séquences et à l’aide de la **NEXT VALUE FOR** afin de générer des numéros de séquence, consultez [numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 Les exemples suivants utilisent une séquence nommée `CountBy1` dans un schéma nommé `Test`. Exécutez l'instruction suivante pour créer la séquence `Test.CountBy1`. Les exemples C et E utilisent la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ; par conséquent, la séquence `CountBy1` est créée dans cette base de données.  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE SCHEMA Test;  
GO  
  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="a-using-a-sequence-in-a-select-statement"></a>A. Utilisation d'une séquence dans une instruction SELECT  
 L'exemple suivant crée une séquence nommée `CountBy1` qui augmente de 1 chaque fois qu'elle est utilisée.  
  
```  
SELECT NEXT VALUE FOR Test.CountBy1 AS FirstUse;  
SELECT NEXT VALUE FOR Test.CountBy1 AS SecondUse;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
FirstUse  
1  
  
SecondUse  
2
```  
  
### <a name="b-setting-a-variable-to-the-next-sequence-value"></a>B. Définition d'une variable sur la valeur de séquence suivante  
 L'exemple suivant illustre trois façons d'affecter à une variable la valeur suivante d'un numéro séquentiel.  
  
```  
DECLARE @myvar1 bigint = NEXT VALUE FOR Test.CountBy1  
DECLARE @myvar2 bigint ;  
DECLARE @myvar3 bigint ;  
SET @myvar2 = NEXT VALUE FOR Test.CountBy1 ;  
SELECT @myvar3 = NEXT VALUE FOR Test.CountBy1 ;  
SELECT @myvar1 AS myvar1, @myvar2 AS myvar2, @myvar3 AS myvar3 ;  
GO  
```  
  
### <a name="c-using-a-sequence-with-a-ranking-window-function"></a>C. Utilisation d'une séquence avec une fonction de fenêtre de classement  
  
```  
USE AdventureWorks2012 ;  
GO  
  
SELECT NEXT VALUE FOR Test.CountBy1 OVER (ORDER BY LastName) AS ListNumber,  
    FirstName, LastName  
FROM Person.Contact ;  
GO  
```  
  
### <a name="d-using-the-next-value-for-function-in-the-definition-of-a-default-constraint"></a>D. Utilisation de la fonction NEXT VALUE FOR dans la définition d'une contrainte par défaut  
 À l’aide de la **NEXT VALUE FOR** fonction dans la définition d’une contrainte par défaut est prise en charge. Pour obtenir un exemple d’utilisation de **NEXT VALUE FOR** dans un **CREATE TABLE** instruction, consultez l’exemple C[numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md). L'exemple suivant utilise `ALTER TABLE` pour ajouter une séquence comme valeur par défaut à une table actuelle.  
  
```  
CREATE TABLE Test.MyTable  
(  
    IDColumn nvarchar(25) PRIMARY KEY,  
    name varchar(25) NOT NULL  
) ;  
GO  
  
CREATE SEQUENCE Test.CounterSeq  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
ALTER TABLE Test.MyTable  
    ADD   
        DEFAULT N'AdvWorks_' +   
        CAST(NEXT VALUE FOR Test.CounterSeq AS NVARCHAR(20))   
        FOR IDColumn;  
GO  
  
INSERT Test.MyTable (name)  
VALUES ('Larry') ;  
GO  
  
SELECT * FROM Test.MyTable;  
GO  
```  
  
### <a name="e-using-the-next-value-for-function-in-an-insert-statement"></a>E. Utilisation de la fonction NEXT VALUE FOR dans une instruction INSERT  
 L'exemple suivant crée une table nommée `TestTable`, puis utilise la fonction `NEXT VALUE FOR` pour insérer une ligne.  
  
```  
CREATE TABLE Test.TestTable  
     (CounterColumn int PRIMARY KEY,  
    Name nvarchar(25) NOT NULL) ;   
GO  
  
INSERT Test.TestTable (CounterColumn,Name)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Syed') ;  
GO  
  
SELECT * FROM Test.TestTable;   
GO  
  
```  
  
### <a name="e-using-the-next-value-for-function-with-select--into"></a>E. Utilisation de la fonction NEXT VALUE FOR avec SELECT… INTO  
 L’exemple suivant utilise le `SELECT … INTO` instruction pour créer une table nommée `Production.NewLocation` et utilise le `NEXT VALUE FOR` fonction pour numéroter chaque ligne.  
  
```  
USE AdventureWorks2012 ;   
GO  
  
SELECT NEXT VALUE FOR Test.CountBy1 AS LocNumber, Name   
    INTO Production.NewLocation  
    FROM Production.Location ;  
GO  
  
SELECT * FROM Production.NewLocation ;  
GO  
```  
  
### <a name="f-granting-permission-to-execute-next-value-for"></a>F. Octroi d'une autorisation pour exécuter NEXT VALUE FOR  
 L’exemple suivant accorde **mise à jour** autorisation à un utilisateur nommé `AdventureWorks\Larry` l’autorisation d’exécuter `NEXT VALUE FOR` à l’aide de la `Test.CounterSeq` séquence.  
  
```  
GRANT UPDATE ON OBJECT::Test.CounterSeq TO [AdventureWorks\Larry] ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une séquence de &#40; Transact-SQL &#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [Numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  

